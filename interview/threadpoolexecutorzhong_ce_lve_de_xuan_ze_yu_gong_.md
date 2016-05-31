# ThreadPoolExecutor中策略的选择与工作队列的选择（java线程池）

来源 http://blog.csdn.net/longeremmy/article/details/8231184

http://www.javaweb.cc/help/JavaAPI1.6/index.html?java/util/concurrent/ThreadPoolExecutor.html
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




java.util.concurrent 
类 ThreadPoolExecutor

java.lang.Object
  继承者 java.util.concurrent.AbstractExecutorService
      继承者 java.util.concurrent.ThreadPoolExecutor
所有已实现的接口：
Executor, ExecutorService
直接已知子类：
ScheduledThreadPoolExecutor
public class ThreadPoolExecutor
extends AbstractExecutorService
一个 ExecutorService，它使用可能的几个池线程之一执行每个提交的任务，通常使用 Executors 工厂方法配置。

线程池可以解决两个不同问题：由于减少了每个任务调用的开销，它们通常可以在执行大量异步任务时提供增强的性能，并且还可以提供绑定和管理资源（包括执行任务集时使用的线程）的方法。每个 ThreadPoolExecutor 还维护着一些基本的统计数据，如完成的任务数。

为了便于跨大量上下文使用，此类提供了很多可调整的参数和扩展钩子 (hook)。但是，强烈建议程序员使用较为方便的 Executors 工厂方法 Executors.newCachedThreadPool()（无界线程池，可以进行自动线程回收）、Executors.newFixedThreadPool(int)（固定大小线程池）和 Executors.newSingleThreadExecutor()（单个后台线程），它们均为大多数使用场景预定义了设置。否则，在手动配置和调整此类时，使用以下指导：

核心和最大池大小
ThreadPoolExecutor 将根据 corePoolSize（参见 getCorePoolSize()）和 maximumPoolSize（参见 getMaximumPoolSize()）设置的边界自动调整池大小。当新任务在方法 execute(java.lang.Runnable) 中提交时，如果运行的线程少于 corePoolSize，则创建新线程来处理请求，即使其他辅助线程是空闲的。如果运行的线程多于 corePoolSize 而少于 maximumPoolSize，则仅当队列满时才创建新线程。如果设置的 corePoolSize 和 maximumPoolSize 相同，则创建了固定大小的线程池。如果将 maximumPoolSize 设置为基本的无界值（如 Integer.MAX_VALUE），则允许池适应任意数量的并发任务。在大多数情况下，核心和最大池大小仅基于构造来设置，不过也可以使用 setCorePoolSize(int) 和 setMaximumPoolSize(int) 进行动态更改。
按需构造
默认情况下，即使核心线程最初只是在新任务到达时才创建和启动的，也可以使用方法 prestartCoreThread() 或 prestartAllCoreThreads() 对其进行动态重写。如果构造带有非空队列的池，则可能希望预先启动线程。
创建新线程
使用 ThreadFactory 创建新线程。如果没有另外说明，则在同一个 ThreadGroup 中一律使用 Executors.defaultThreadFactory() 创建线程，并且这些线程具有相同的 NORM_PRIORITY 优先级和非守护进程状态。通过提供不同的 ThreadFactory，可以改变线程的名称、线程组、优先级、守护进程状态，等等。如果从 newThread 返回 null 时 ThreadFactory 未能创建线程，则执行程序将继续运行，但不能执行任何任务。
保持活动时间
如果池中当前有多于 corePoolSize 的线程，则这些多出的线程在空闲时间超过 keepAliveTime 时将会终止（参见 getKeepAliveTime(java.util.concurrent.TimeUnit)）。这提供了当池处于非活动状态时减少资源消耗的方法。如果池后来变得更为活动，则可以创建新的线程。也可以使用方法 setKeepAliveTime(long, java.util.concurrent.TimeUnit) 动态地更改此参数。使用 Long.MAX_VALUE TimeUnit.NANOSECONDS 的值在关闭前有效地从以前的终止状态禁用空闲线程。默认情况下，保持活动策略只在有多于 corePoolSizeThreads 的线程时应用。但是只要 keepAliveTime 值非 0，allowCoreThreadTimeOut(boolean) 方法也可将此超时策略应用于核心线程。
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
当 Executor 已经关闭，并且 Executor 将有限边界用于最大线程和工作队列容量，且已经饱和时，在方法 execute(java.lang.Runnable) 中提交的新任务将被拒绝。在以上两种情况下，execute 方法都将调用其 RejectedExecutionHandler 的 RejectedExecutionHandler.rejectedExecution(java.lang.Runnable, java.util.concurrent.ThreadPoolExecutor) 方法。下面提供了四种预定义的处理程序策略：
在默认的 ThreadPoolExecutor.AbortPolicy 中，处理程序遭到拒绝将抛出运行时 RejectedExecutionException。
在 ThreadPoolExecutor.CallerRunsPolicy 中，线程调用运行该任务的 execute 本身。此策略提供简单的反馈控制机制，能够减缓新任务的提交速度。
在 ThreadPoolExecutor.DiscardPolicy 中，不能执行的任务将被删除。
在 ThreadPoolExecutor.DiscardOldestPolicy 中，如果执行程序尚未关闭，则位于工作队列头部的任务将被删除，然后重试执行程序（如果再次失败，则重复此过程）。
定义和使用其他种类的 RejectedExecutionHandler 类也是可能的，但这样做需要非常小心，尤其是当策略仅用于特定容量或排队策略时。
钩子 (hook) 方法
此类提供 protected 可重写的 beforeExecute(java.lang.Thread, java.lang.Runnable) 和 afterExecute(java.lang.Runnable, java.lang.Throwable) 方法，这两种方法分别在执行每个任务之前和之后调用。它们可用于操纵执行环境；例如，重新初始化 ThreadLocal、搜集统计信息或添加日志条目。此外，还可以重写方法 terminated() 来执行 Executor 完全终止后需要完成的所有特殊处理。
如果钩子 (hook) 或回调方法抛出异常，则内部辅助线程将依次失败并突然终止。

队列维护
方法 getQueue() 允许出于监控和调试目的而访问工作队列。强烈反对出于其他任何目的而使用此方法。remove(java.lang.Runnable) 和 purge() 这两种方法可用于在取消大量已排队任务时帮助进行存储回收。
终止
程序 AND 不再引用的池没有剩余线程会自动 shutdown。如果希望确保回收取消引用的池（即使用户忘记调用 shutdown()），则必须安排未使用的线程最终终止：设置适当保持活动时间，使用 0 核心线程的下边界和/或设置 allowCoreThreadTimeOut(boolean)。
扩展示例。此类的大多数扩展可以重写一个或多个受保护的钩子 (hook) 方法。例如，下面是一个添加了简单的暂停/恢复功能的子类：

 class PausableThreadPoolExecutor extends ThreadPoolExecutor {
   private boolean isPaused;
   private ReentrantLock pauseLock = new ReentrantLock();
   private Condition unpaused = pauseLock.newCondition();

   public PausableThreadPoolExecutor(...) { super(...); }
 
   protected void beforeExecute(Thread t, Runnable r) {
     super.beforeExecute(t, r);
     pauseLock.lock();
     try {
       while (isPaused) unpaused.await();
     } catch(InterruptedException ie) {
       t.interrupt();
     } finally {
       pauseLock.unlock();
     }
   }
 
   public void pause() {
     pauseLock.lock();
     try {
       isPaused = true;
     } finally {
       pauseLock.unlock();
     }
   }
 
   public void resume() {
     pauseLock.lock();
     try {
       isPaused = false;
       unpaused.signalAll();
     } finally {
       pauseLock.unlock();
     }
   }
 }
 
从以下版本开始：
1.5

嵌套类摘要
static class	ThreadPoolExecutor.AbortPolicy 
          用于被拒绝任务的处理程序，它将抛出 RejectedExecutionException.
static class	ThreadPoolExecutor.CallerRunsPolicy 
          用于被拒绝任务的处理程序，它直接在 execute 方法的调用线程中运行被拒绝的任务；如果执行程序已关闭，则会丢弃该任务。
static class	ThreadPoolExecutor.DiscardOldestPolicy 
          用于被拒绝任务的处理程序，它放弃最旧的未处理请求，然后重试 execute；如果执行程序已关闭，则会丢弃该任务。
static class	ThreadPoolExecutor.DiscardPolicy 
          用于被拒绝任务的处理程序，默认情况下它将丢弃被拒绝的任务。
 
构造方法摘要
ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue) 
          用给定的初始参数和默认的线程工厂及被拒绝的执行处理程序创建新的 ThreadPoolExecutor。
ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, RejectedExecutionHandler handler) 
          用给定的初始参数和默认的线程工厂创建新的 ThreadPoolExecutor。
ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory) 
          用给定的初始参数和默认被拒绝的执行处理程序创建新的 ThreadPoolExecutor。
ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory, RejectedExecutionHandler handler) 
          用给定的初始参数创建新的 ThreadPoolExecutor。
 
方法摘要
protected  void	afterExecute(Runnable r, Throwable t) 
          基于完成执行给定 Runnable 所调用的方法。
 void	allowCoreThreadTimeOut(boolean value) 
          如果在保持活动时间内没有任务到达，新任务到达时正在替换（如果需要），则设置控制核心线程是超时还是终止的策略。
 boolean	allowsCoreThreadTimeOut() 
          如果此池允许核心线程超时和终止，如果在 keepAlive 时间内没有任务到达，新任务到达时正在替换（如果需要），则返回 true。
 boolean	awaitTermination(long timeout, TimeUnit unit) 
          请求关闭、发生超时或者当前线程中断，无论哪一个首先发生之后，都将导致阻塞，直到所有任务完成执行。
protected  void	beforeExecute(Thread t, Runnable r) 
          在执行给定线程中的给定 Runnable 之前调用的方法。
 void	execute(Runnable command) 
          在将来某个时间执行给定任务。
protected  void	finalize() 
          当不再引用此执行程序时，调用 shutdown。
 int	getActiveCount() 
          返回主动执行任务的近似线程数。
 long	getCompletedTaskCount() 
          返回已完成执行的近似任务总数。
 int	getCorePoolSize() 
          返回核心线程数。
 long	getKeepAliveTime(TimeUnit unit) 
          返回线程保持活动的时间，该时间就是超过核心池大小的线程可以在终止前保持空闲的时间值。
 int	getLargestPoolSize() 
          返回曾经同时位于池中的最大线程数。
 int	getMaximumPoolSize() 
          返回允许的最大线程数。
 int	getPoolSize() 
          返回池中的当前线程数。
 BlockingQueue<Runnable>	getQueue() 
          返回此执行程序使用的任务队列。
 RejectedExecutionHandler	getRejectedExecutionHandler() 
          返回用于未执行任务的当前处理程序。
 long	getTaskCount() 
          返回曾计划执行的近似任务总数。
 ThreadFactory	getThreadFactory() 
          返回用于创建新线程的线程工厂。
 boolean	isShutdown() 
          如果此执行程序已关闭，则返回 true。
 boolean	isTerminated() 
          如果关闭后所有任务都已完成，则返回 true。
 boolean	isTerminating() 
          如果此执行程序处于在 shutdown 或 shutdownNow 之后正在终止但尚未完全终止的过程中，则返回 true。
 int	prestartAllCoreThreads() 
          启动所有核心线程，使其处于等待工作的空闲状态。
 boolean	prestartCoreThread() 
          启动核心线程，使其处于等待工作的空闲状态。
 void	purge() 
          尝试从工作队列移除所有已取消的 Future 任务。
 boolean	remove(Runnable task) 
          从执行程序的内部队列中移除此任务（如果存在），从而如果尚未开始，则其不再运行。
 void	setCorePoolSize(int corePoolSize) 
          设置核心线程数。
 void	setKeepAliveTime(long time, TimeUnit unit) 
          设置线程在终止前可以保持空闲的时间限制。
 void	setMaximumPoolSize(int maximumPoolSize) 
          设置允许的最大线程数。
 void	setRejectedExecutionHandler(RejectedExecutionHandler handler) 
          设置用于未执行任务的新处理程序。
 void	setThreadFactory(ThreadFactory threadFactory) 
          设置用于创建新线程的线程工厂。
 void	shutdown() 
          按过去执行已提交任务的顺序发起一个有序的关闭，但是不接受新任务。
 List<Runnable>	shutdownNow() 
          尝试停止所有的活动执行任务、暂停等待任务的处理，并返回等待执行的任务列表。
protected  void	terminated() 
          当 Executor 已经终止时调用的方法。
 
从类 java.util.concurrent.AbstractExecutorService 继承的方法
invokeAll, invokeAll, invokeAny, invokeAny, newTaskFor, newTaskFor, submit, submit, submit
 
从类 java.lang.Object 继承的方法
clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait
 

构造方法详细信息
ThreadPoolExecutor

public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue)
用给定的初始参数和默认的线程工厂及被拒绝的执行处理程序创建新的 ThreadPoolExecutor。使用 Executors 工厂方法之一比使用此通用构造方法方便得多。
参数：
corePoolSize - 池中所保存的线程数，包括空闲线程。
maximumPoolSize - 池中允许的最大线程数。
keepAliveTime - 当线程数大于核心时，此为终止前多余的空闲线程等待新任务的最长时间。
unit - keepAliveTime 参数的时间单位。
workQueue - 执行前用于保持任务的队列。此队列仅保持由 execute 方法提交的 Runnable 任务。
抛出：
IllegalArgumentException - 如果 corePoolSize 或 keepAliveTime 小于 0，或者 maximumPoolSize 小于等于 0，或者 corePoolSize 大于 maximumPoolSize。
NullPointerException - 如果 workQueue 为 null
ThreadPoolExecutor

public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          ThreadFactory threadFactory)
用给定的初始参数和默认被拒绝的执行处理程序创建新的 ThreadPoolExecutor。
参数：
corePoolSize - 池中所保存的线程数，包括空闲线程。
maximumPoolSize - 池中允许的最大线程数。
keepAliveTime - 当线程数大于核心时，此为终止前多余的空闲线程等待新任务的最长时间。
unit - keepAliveTime 参数的时间单位。
workQueue - 执行前用于保持任务的队列。此队列仅保持由 execute 方法提交的 Runnable 任务。
threadFactory - 执行程序创建新线程时使用的工厂。
抛出：
IllegalArgumentException - 如果 corePoolSize 或 keepAliveTime 小于 0，或者 maximumPoolSize 小于等于 0，或者 corePoolSize 大于 maximumPoolSize。
NullPointerException - 如果 workQueue 或 threadFactory 为 null。
ThreadPoolExecutor

public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          RejectedExecutionHandler handler)
用给定的初始参数和默认的线程工厂创建新的 ThreadPoolExecutor。
参数：
corePoolSize - 池中所保存的线程数，包括空闲线程。
maximumPoolSize - 池中允许的最大线程数。
keepAliveTime - 当线程数大于核心时，此为终止前多余的空闲线程等待新任务的最长时间。
unit - keepAliveTime 参数的时间单位。
workQueue - 执行前用于保持任务的队列。此队列仅由保持 execute 方法提交的 Runnable 任务。
handler - 由于超出线程范围和队列容量而使执行被阻塞时所使用的处理程序。
抛出：
IllegalArgumentException - 如果 corePoolSize 或 keepAliveTime 小于 0，或者 maximumPoolSize 小于等于 0，或者 corePoolSize 大于 maximumPoolSize。
NullPointerException - 如果 workQueue 或 handler 为 null。
ThreadPoolExecutor

public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          ThreadFactory threadFactory,
                          RejectedExecutionHandler handler)
用给定的初始参数创建新的 ThreadPoolExecutor。
参数：
corePoolSize - 池中所保存的线程数，包括空闲线程。
maximumPoolSize - 池中允许的最大线程数。
keepAliveTime - 当线程数大于核心时，此为终止前多余的空闲线程等待新任务的最长时间。
unit - keepAliveTime 参数的时间单位。
workQueue - 执行前用于保持任务的队列。此队列仅保持由 execute 方法提交的 Runnable 任务。
threadFactory - 执行程序创建新线程时使用的工厂。
handler - 由于超出线程范围和队列容量而使执行被阻塞时所使用的处理程序。
抛出：
IllegalArgumentException - 如果 corePoolSize 或 keepAliveTime 小于 0，或者 maximumPoolSize 小于等于 0，或者 corePoolSize 大于 maximumPoolSize。
NullPointerException - 如果 workQueue、threadFactory 或 handler 为 null。
方法详细信息
execute

public void execute(Runnable command)
在将来某个时间执行给定任务。可以在新线程中或者在现有池线程中执行该任务。 如果无法将任务提交执行，或者因为此执行程序已关闭，或者因为已达到其容量，则该任务由当前 RejectedExecutionHandler 处理。
参数：
command - 要执行的任务。
抛出：
RejectedExecutionException - 如果无法接收要执行的任务，则由 RejectedExecutionHandler 决定是否抛出 RejectedExecutionException
NullPointerException - 如果命令为 null
shutdown

public void shutdown()
按过去执行已提交任务的顺序发起一个有序的关闭，但是不接受新任务。如果已经关闭，则调用没有其他作用。
抛出：
SecurityException - 如果安全管理器存在并且关闭此 ExecutorService 可能操作某些不允许调用者修改的线程（因为它没有 RuntimePermission("modifyThread")），或者安全管理器的 checkAccess 方法拒绝访问。
shutdownNow

public List<Runnable> shutdownNow()
尝试停止所有的活动执行任务、暂停等待任务的处理，并返回等待执行的任务列表。在从此方法返回的任务队列中排空（移除）这些任务。
并不保证能够停止正在处理的活动执行任务，但是会尽力尝试。 此实现通过 Thread.interrupt() 取消任务，所以无法响应中断的任何任务可能永远无法终止。

返回：
从未开始执行的任务的列表。
抛出：
SecurityException - 如果安全管理器存在并且关闭此 ExecutorService 可能操作某些不允许调用者修改的线程（因为它没有 RuntimePermission("modifyThread")），或者安全管理器的 checkAccess 方法拒绝访问。
isShutdown

public boolean isShutdown()
从接口 ExecutorService 复制的描述
如果此执行程序已关闭，则返回 true。
返回：
如果此执行程序已关闭，则返回 true
isTerminating

public boolean isTerminating()
如果此执行程序处于在 shutdown 或 shutdownNow 之后正在终止但尚未完全终止的过程中，则返回 true。此方法可能对调试很有用。关闭之后很长一段时间才报告返回的 true，这可能表示提交的任务已经被忽略或取消中断，导致此执行程序无法正确终止。
返回：
如果正在终止但尚未完成，则返回 true
isTerminated

public boolean isTerminated()
从接口 ExecutorService 复制的描述
如果关闭后所有任务都已完成，则返回 true。注意，除非首先调用 shutdown 或 shutdownNow，否则 isTerminated 永不为 true。
返回：
如果关闭后所有任务都已完成，则返回 true
awaitTermination

public boolean awaitTermination(long timeout,
                                TimeUnit unit)
                         throws InterruptedException
从接口 ExecutorService 复制的描述
请求关闭、发生超时或者当前线程中断，无论哪一个首先发生之后，都将导致阻塞，直到所有任务完成执行。
参数：
timeout - 最长等待时间
unit - timeout 参数的时间单位
返回：
如果此执行程序终止，则返回 true；如果终止前超时期满，则返回 false
抛出：
InterruptedException - 如果等待时发生中断
finalize

protected void finalize()
当不再引用此执行程序时，调用 shutdown。
覆盖：
类 Object 中的 finalize
setThreadFactory

public void setThreadFactory(ThreadFactory threadFactory)
设置用于创建新线程的线程工厂。
参数：
threadFactory - 新线程工厂
抛出：
NullPointerException - 如果 threadFactory 为 null
另请参见：
getThreadFactory()
getThreadFactory

public ThreadFactory getThreadFactory()
返回用于创建新线程的线程工厂。
返回：
当前线程工厂
另请参见：
setThreadFactory(java.util.concurrent.ThreadFactory)
setRejectedExecutionHandler

public void setRejectedExecutionHandler(RejectedExecutionHandler handler)
设置用于未执行任务的新处理程序。
参数：
handler - 新处理程序
抛出：
NullPointerException - 如果处理程序为 null
另请参见：
getRejectedExecutionHandler()
getRejectedExecutionHandler

public RejectedExecutionHandler getRejectedExecutionHandler()
返回用于未执行任务的当前处理程序。
返回：
当前处理程序
另请参见：
setRejectedExecutionHandler(java.util.concurrent.RejectedExecutionHandler)
setCorePoolSize

public void setCorePoolSize(int corePoolSize)
设置核心线程数。此操作将重写构造方法中设置的任何值。如果新值小于当前值，则多余的现有线程将在下一次空闲时终止。如果较大，则在需要时启动新线程来执行这些排队的任务。
参数：
corePoolSize - 新核心大小
抛出：
IllegalArgumentException - 如果 corePoolSize 小于 0
另请参见：
getCorePoolSize()
getCorePoolSize

public int getCorePoolSize()
返回核心线程数。
返回：
核心线程数
另请参见：
setCorePoolSize(int)
prestartCoreThread

public boolean prestartCoreThread()
启动核心线程，使其处于等待工作的空闲状态。仅当执行新任务时，此操作才重写默认的启动核心线程策略。如果已启动所有核心线程，此方法将返回 false。
返回：
如果启动了线程，则返回 true
prestartAllCoreThreads

public int prestartAllCoreThreads()
启动所有核心线程，使其处于等待工作的空闲状态。仅当执行新任务时，此操作才重写默认的启动核心线程策略。
返回：
已启动的线程数
allowsCoreThreadTimeOut

public boolean allowsCoreThreadTimeOut()
如果此池允许核心线程超时和终止，如果在 keepAlive 时间内没有任务到达，新任务到达时正在替换（如果需要），则返回 true。当返回 true 时，适用于非核心线程的相同的保持活动策略也同样适用于核心线程。当返回 false（默认值）时，由于没有传入任务，核心线程不会终止。
返回：
如果允许核心线程超时，则返回 true；否则返回 false
从以下版本开始：
1.6
allowCoreThreadTimeOut

public void allowCoreThreadTimeOut(boolean value)
如果在保持活动时间内没有任务到达，新任务到达时正在替换（如果需要），则设置控制核心线程是超时还是终止的策略。当为 false（默认值）时，由于没有传入任务，核心线程将永远不会中止。当为 true 时，适用于非核心线程的相同的保持活动策略也同样适用于核心线程。为了避免连续线程替换，保持活动时间在设置为 true 时必须大于 0。通常应该在主动使用该池前调用此方法。
参数：
value - 如果应该超时，则为 true；否则为 false
抛出：
IllegalArgumentException - 如果 value 为 true 并且当前保持活动时间不大于 0。
从以下版本开始：
1.6
setMaximumPoolSize

public void setMaximumPoolSize(int maximumPoolSize)
设置允许的最大线程数。此操作将重写构造方法中设置的任何值。如果新值小于当前值，则多余的现有线程将在下一次空闲时终止。
参数：
maximumPoolSize - 新的最大值
抛出：
IllegalArgumentException - 如果新的最大值小于等于 0，或者小于核心池大小
另请参见：
getMaximumPoolSize()
getMaximumPoolSize

public int getMaximumPoolSize()
返回允许的最大线程数。
返回：
允许的最大线程数
另请参见：
setMaximumPoolSize(int)
setKeepAliveTime

public void setKeepAliveTime(long time,
                             TimeUnit unit)
设置线程在终止前可以保持空闲的时间限制。如果池中的当前线程数多于核心线程数，在不处理任务的情况下等待这一时间段之后，多余的线程将被终止。此操作将重写构造方法中设置的任何值。
参数：
time - 等待的时间。时间值 0 将导致执行任务后多余的线程立即终止。
unit - 时间参数的时间单位
抛出：
IllegalArgumentException - 如果时间小于 0，或者时间为 0 和 allowsCoreThreadTimeOut
另请参见：
getKeepAliveTime(java.util.concurrent.TimeUnit)
getKeepAliveTime

public long getKeepAliveTime(TimeUnit unit)
返回线程保持活动的时间，该时间就是超过核心池大小的线程可以在终止前保持空闲的时间值。
参数：
unit - 所需的结果时间单位
返回：
时间限制
另请参见：
setKeepAliveTime(long, java.util.concurrent.TimeUnit)
getQueue

public BlockingQueue<Runnable> getQueue()
返回此执行程序使用的任务队列。对任务队列的访问主要用于调试和监控。此队列可能正处于活动使用状态中。获取任务队列不妨碍已加入队列的任务的执行。
返回：
任务队列
remove

public boolean remove(Runnable task)
从执行程序的内部队列中移除此任务（如果存在），从而如果尚未开始，则其不再运行。
此方法可用作取消方案的一部分。它可能无法移除在放置到内部队列之前已经转换为其他形式的任务。例如，使用 submit 输入的任务可能被转换为维护 Future 状态的形式。但是，在此情况下，purge() 方法可用于移除那些已被取消的 Future。

参数：
task - 要移除的任务
返回：
如果已经移除任务，则返回 true
purge

public void purge()
尝试从工作队列移除所有已取消的 Future 任务。此方法可用作存储回收操作，它对功能没有任何影响。取消的任务不会再次执行，但是它们可能在工作队列中累积，直到 worker 线程主动将其移除。调用此方法将试图立即移除它们。但是，如果出现其他线程的干预，那么此方法移除任务将失败。
getPoolSize

public int getPoolSize()
返回池中的当前线程数。
返回：
线程数。
getActiveCount

public int getActiveCount()
返回主动执行任务的近似线程数。
返回：
线程数。
getLargestPoolSize

public int getLargestPoolSize()
返回曾经同时位于池中的最大线程数。
返回：
线程数。
getTaskCount

public long getTaskCount()
返回曾计划执行的近似任务总数。因为在计算期间任务和线程的状态可能动态改变，所以返回值只是一个近似值。
返回：
任务数
getCompletedTaskCount

public long getCompletedTaskCount()
返回已完成执行的近似任务总数。因为在计算期间任务和线程的状态可能动态改变，所以返回值只是一个近似值，但是该值在整个连续调用过程中不会减少。
返回：
任务数。
beforeExecute

protected void beforeExecute(Thread t,
                             Runnable r)
在执行给定线程中的给定 Runnable 之前调用的方法。此方法由将执行任务 r 的线程 t 调用，并且可用于重新初始化 ThreadLocals 或者执行日志记录。
此实现不执行任何操作，但可在子类中定制。注：为了正确嵌套多个重写操作，此方法结束时，子类通常应该调用 super.beforeExecute。

参数：
t - 将运行任务 r 的线程。
r - 将执行的任务。
afterExecute

protected void afterExecute(Runnable r,
                            Throwable t)
基于完成执行给定 Runnable 所调用的方法。此方法由执行任务的线程调用。如果非 null，则 Throwable 是导致执行突然终止的未捕获 RuntimeException 或 Error。
注：当操作显示地或者通过 submit 之类的方法包含在任务内时（如 FutureTask），这些任务对象捕获和维护计算异常，因此它们不会导致突然终止，内部异常不会 传递给此方法。

此实现不执行任何操作，但可在子类中定制。注：为了正确嵌套多个重写操作，此方法开始时，子类通常应该调用 super.afterExecute。

参数：
r - 已经完成的 runnable 线程。
t - 导致终止的异常；如果执行正常结束，则为 null。
terminated

protected void terminated()
当 Executor 已经终止时调用的方法。默认实现不执行任何操作。注：为了正确嵌套多个重写操作，子类通常应该在此方法中调用 super.afterExecute。