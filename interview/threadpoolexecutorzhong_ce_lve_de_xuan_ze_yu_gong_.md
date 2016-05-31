# ThreadPoolExecutor中策略的选择与工作队列的选择（java线程池）

来源 http://blog.csdn.net/longeremmy/article/details/8231184
工作原理

1、线程池刚创建时，里面没有一个线程。任务队列是作为参数传进来的。不过，就算队列里面有任务，线程池也不会马上执行它们。

2、当调用 execute() 方法添加一个任务时，线程池会做如下判断：

       a. 如果正在运行的线程数量小于 corePoolSize，那么马上创建线程运行这个任务；

　　 b. 如果正在运行的线程数量大于或等于 corePoolSize，那么将这个任务放入队列。

　　 c. 如果这时候队列满了，而且正在运行的线程数量小于 maximumPoolSize，那么还是要创建线程运行这个任务；

　　 d. 如果队列满了，而且正在运行的线程数量大于或等于 maximumPoolSize，那么线程池会抛出异常，告诉调用者“我不能再接受任务了”。

3、当一个线程完成任务时，它会从队列中取下一个任务来执行。

4、当一个线程无事可做，超过一定的时间（keepAliveTime）时，线程池会判断，如果当前运行的线程数大于 corePoolSize，那么这个线程就被停掉。所以线程池的所有任务完成后，它最终会收缩到 corePoolSize 的大小。

　 　这样的过程说明，并不是先加入任务就一定会先执行。假设队列大小为 10，corePoolSize 为 3，maximumPoolSize 为 6，那么当加入 20 个任务时，执行的顺序就是这样的：首先执行任务 1、2、3，然后任务 4~13 被放入队列。这时候队列满了，任务 14、15、16 会被马上执行，而任务 17~20 则会抛出异常。最终顺序是：1、2、3、14、15、16、4、5、6、7、8、9、10、11、12、13。下面是一个线程池使用的例子：


排队
所有 BlockingQueue 都可用于传输和保持提交的任务。可以使用此队列与池大小进行交互：
如果运行的线程少于 corePoolSize，则 Executor 始终首选添加新的线程，而不进行排队。
如果运行的线程等于或多于 corePoolSize，则 Executor 始终首选将请求加入队列，而不添加新的线程。
如果无法将请求加入队列，则创建新的线程，除非创建此线程超出 maximumPoolSize，在这种情况下，任务将被拒绝。
排队有三种通用策略：
直接提交。工作队列的默认选项是 SynchronousQueue，它将任务直接提交给线程而不保持它们。在此，如果不存在可用于立即运行任务的线程，则试图把任务加入队列将失败，因此会构造一个新的线程。此策略可以避免在处理可能具有内部依赖性的请求集时出现锁。直接提交通常要求无界 maximumPoolSizes 以避免拒绝新提交的任务。当命令以超过队列所能处理的平均数连续到达时，此策略允许无界线程具有增长的可能性。
无界队列。使用无界队列（例如，不具有预定义容量的 LinkedBlockingQueue）将导致在所有 corePoolSize 线程都忙时新任务在队列中等待。这样，创建的线程就不会超过 corePoolSize。（因此，maximumPoolSize 的值也就无效了。）当每个任务完全独立于其他任务，即任务执行互不影响时，适合于使用无界队列；例如，在 Web 页服务器中。这种排队可用于处理瞬态突发请求，当命令以超过队列所能处理的平均数连续到达时，此策略允许无界线程具有增长的可能性。
有界队列。当使用有限的 maximumPoolSizes 时，有界队列（如 ArrayBlockingQueue）有助于防止资源耗尽，但是可能较难调整和控制。队列大小和最大池大小可能需要相互折衷：使用大型队列和小型池可以最大限度地降低 CPU 使用率、操作系统资源和上下文切换开销，但是可能导致人工降低吞吐量。如果任务频繁阻塞（例如，如果它们是 I/O 边界），则系统可能为超过您许可的更多线程安排时间。使用小型队列通常要求较大的池大小，CPU 使用率较高，但是可能遇到不可接受的调度开销，这样也会降低吞吐量。
被拒绝的任务
当 Executor 已经关闭，并且 Executor 将有限边界用于最大线程和工作队列容量，且已经饱和时，在方法 execute(java.lang.Runnable) 中提交的新任务将被拒绝。在以上两种情况下，execute 方法都将调用其RejectedExecutionHandler 的RejectedExecutionHandler.rejectedExecution(java.lang.Runnable, java.util.concurrent.ThreadPoolExecutor) 方法。下面提供了四种预定义的处理程序策略：
在默认的 ThreadPoolExecutor.AbortPolicy 中，处理程序遭到拒绝将抛出运行时RejectedExecutionException。
在 ThreadPoolExecutor.CallerRunsPolicy 中，线程调用运行该任务的execute 本身。此策略提供简单的反馈控制机制，能够减缓新任务的提交速度。
在 ThreadPoolExecutor.DiscardPolicy 中，不能执行的任务将被删除。
在 ThreadPoolExecutor.DiscardOldestPolicy 中，如果执行程序尚未关闭，则位于工作队列头部的任务将被删除，然后重试执行程序（如果再次失败，则重复此过程）。
定义和使用其他种类的 RejectedExecutionHandler 类也是可能的，但这样做需要非常小心，尤其是当策略仅用于特定容量或排队策略时。 
公用的类ThreadPoolTask
[java] view plain copy
public class ThreadPoolTask implements Runnable {   
  // 保存任务所需要的数据   
  private Object threadPoolTaskData;   
  private static int consumerTaskSleepTime = 2000;   
  
  ThreadPoolTask(Object tasks) {   
    this.threadPoolTaskData = tasks;   
  }   
  
  public void run() {   
    // 处理一个任务，这里的处理方式太简单了，仅仅是一个打印语句   
    System.out.println("start .." + threadPoolTaskData);   
    try {   
      //便于观察，等待一段时间   
      Thread.sleep(consumerTaskSleepTime);   
    } catch (Exception e) {   
      e.printStackTrace();   
    }   
    System.out.println("finish " + threadPoolTaskData);   
    threadPoolTaskData = null;   
  }   
  
}   


ThreadPoolExecutor.AbortPolicy
[java] view plain copy
import java.util.concurrent.ArrayBlockingQueue;   
import java.util.concurrent.LinkedBlockingQueue;  
import java.util.concurrent.ThreadPoolExecutor;   
import java.util.concurrent.TimeUnit;   
  
public class ThreadPool {   
    
  //让可执行程序休息一下  
  private static int executePrograms = 0;   
  private static int produceTaskMaxNumber = 10;   
  
  public static void main(String[] args) {   
    // 构造一个线程池   
    ThreadPoolExecutor threadPool = new ThreadPoolExecutor(2, 4, 3,   
        TimeUnit.SECONDS, new LinkedBlockingQueue<Runnable>(3),   
        new ThreadPoolExecutor.CallerRunsPolicy());   
  
    for (int i = 1; i <= produceTaskMaxNumber; i++) {   
      try {   
        String task = "task@ " + i;   
        System.out.println("put " + task);   
        threadPool.execute(new ThreadPoolTask(task));   
  
        // 便于观察，等待一段时间   
        Thread.sleep(executePrograms);   
      } catch (Exception e) {   
        e.printStackTrace();   
      }   
    }   
  }   
}   
运行结果
[java] view plain copy
put task@ 1  
put task@ 2  
start ..task@ 1  
put task@ 3  
put task@ 4  
start ..task@ 2  
put task@ 5  
put task@ 6  
put task@ 7  
start ..task@ 6  
put task@ 8  
start ..task@ 7  
java.util.concurrent.RejectedExecutionException  
    at java.util.concurrent.ThreadPoolExecutor$AbortPolicy.rejectedExecution(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.reject(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.execute(Unknown Source)  
    at ThreadPool.main(ThreadPool.java:22)  
put task@ 9  
java.util.concurrent.RejectedExecutionException  
    at java.util.concurrent.ThreadPoolExecutor$AbortPolicy.rejectedExecution(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.reject(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.execute(Unknown Source)  
    at ThreadPool.main(ThreadPool.java:22)  
put task@ 10  
java.util.concurrent.RejectedExecutionException  
    at java.util.concurrent.ThreadPoolExecutor$AbortPolicy.rejectedExecution(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.reject(Unknown Source)  
    at java.util.concurrent.ThreadPoolExecutor.execute(Unknown Source)  
    at ThreadPool.main(ThreadPool.java:22)  
finish task@ 2  
finish task@ 6  
finish task@ 7  
start ..task@ 4  
start ..task@ 3  
finish task@ 1  
start ..task@ 5  
finish task@ 4  
finish task@ 3  
finish task@ 5  




ThreadPoolExecutor.CallerRunsPolicy
[java] view plain copy
import java.util.concurrent.ArrayBlockingQueue;   
import java.util.concurrent.LinkedBlockingQueue;  
import java.util.concurrent.ThreadPoolExecutor;   
import java.util.concurrent.TimeUnit;   
  
public class ThreadPool {   
    
  //让可执行程序休息一下  
  private static int executePrograms = 0;   
  private static int produceTaskMaxNumber = 10;   
  
  public static void main(String[] args) {   
    // 构造一个线程池   
    ThreadPoolExecutor threadPool = new ThreadPoolExecutor(2, 4, 3,   
        TimeUnit.SECONDS, new LinkedBlockingQueue<Runnable>(3),   
        new ThreadPoolExecutor.CallerRunsPolicy());   
  
    for (int i = 1; i <= produceTaskMaxNumber; i++) {   
      try {   
        String task = "task@ " + i;   
        System.out.println("put " + task);   
        threadPool.execute(new ThreadPoolTask(task));   
  
        // 便于观察，等待一段时间   
        Thread.sleep(executePrograms);   
      } catch (Exception e) {   
        e.printStackTrace();   
      }   
    }   
  }   
}   
运行结果
[java] view plain copy
put task@ 1  
put task@ 2  
start ..task@ 1  
put task@ 3  
start ..task@ 2  
put task@ 4  
put task@ 5  
put task@ 6  
put task@ 7  
start ..task@ 6  
put task@ 8  
start ..task@ 8  
start ..task@ 7  
finish task@ 2  
finish task@ 1  
start ..task@ 3  
start ..task@ 4  
finish task@ 6  
start ..task@ 5  
finish task@ 7  
finish task@ 8  
put task@ 9  
put task@ 10  
start ..task@ 9  
finish task@ 4  
finish task@ 3  
start ..task@ 10  
finish task@ 9  
finish task@ 5  
finish task@ 10  




ThreadPoolExecutor.DiscardPolicy 
[java] view plain copy
import java.util.concurrent.ArrayBlockingQueue;   
import java.util.concurrent.LinkedBlockingQueue;  
import java.util.concurrent.ThreadPoolExecutor;   
import java.util.concurrent.TimeUnit;   
  
public class ThreadPool {   
    
  //让可执行程序休息一下  
  private static int executePrograms = 0;   
  private static int produceTaskMaxNumber = 10;   
  
  public static void main(String[] args) {   
    // 构造一个线程池   
    ThreadPoolExecutor threadPool = new ThreadPoolExecutor(2, 4, 3,   
        TimeUnit.SECONDS, new LinkedBlockingQueue<Runnable>(3),   
        new ThreadPoolExecutor.CallerRunsPolicy());   
  
    for (int i = 1; i <= produceTaskMaxNumber; i++) {   
      try {   
        String task = "task@ " + i;   
        System.out.println("put " + task);   
        threadPool.execute(new ThreadPoolTask(task));   
  
        // 便于观察，等待一段时间   
        Thread.sleep(executePrograms);   
      } catch (Exception e) {   
        e.printStackTrace();   
      }   
    }   
  }   
}   
运行结果
[java] view plain copy
put task@ 1  
put task@ 2  
start ..task@ 1  
put task@ 3  
start ..task@ 2  
put task@ 4  
put task@ 5  
put task@ 6  
put task@ 7  
start ..task@ 6  
put task@ 8  
put task@ 9  
start ..task@ 7  
put task@ 10  
finish task@ 2  
finish task@ 1  
start ..task@ 3  
start ..task@ 4  
finish task@ 7  
finish task@ 6  
start ..task@ 5  
finish task@ 3  
finish task@ 4  
finish task@ 5  


ThreadPoolExecutor.DiscardOldestPolicy 

[java] view plain copy
import java.util.concurrent.ArrayBlockingQueue;   
import java.util.concurrent.LinkedBlockingQueue;  
import java.util.concurrent.ThreadPoolExecutor;   
import java.util.concurrent.TimeUnit;   
  
public class ThreadPool {   
    
  //让可执行程序休息一下  
  private static int executePrograms = 0;   
  private static int produceTaskMaxNumber = 10;   
  
  public static void main(String[] args) {   
    // 构造一个线程池   
    ThreadPoolExecutor threadPool = new ThreadPoolExecutor(2, 4, 3,   
        TimeUnit.SECONDS, new LinkedBlockingQueue<Runnable>(3),   
        new ThreadPoolExecutor.CallerRunsPolicy());   
  
    for (int i = 1; i <= produceTaskMaxNumber; i++) {   
      try {   
        String task = "task@ " + i;   
        System.out.println("put " + task);   
        threadPool.execute(new ThreadPoolTask(task));   
  
        // 便于观察，等待一段时间   
        Thread.sleep(executePrograms);   
      } catch (Exception e) {   
        e.printStackTrace();   
      }   
    }   
  }   
}   
运行结果：
[java] view plain copy
put task@ 1  
put task@ 2  
start ..task@ 1  
put task@ 3  
start ..task@ 2  
put task@ 4  
put task@ 5  
put task@ 6  
put task@ 7  
start ..task@ 6  
put task@ 8  
start ..task@ 7  
put task@ 9  
put task@ 10  
finish task@ 6  
finish task@ 7  
start ..task@ 8  
finish task@ 1  
start ..task@ 9  
finish task@ 2  
start ..task@ 10  
finish task@ 8  
finish task@ 9  
finish task@ 10  