# 第二讲 一元函数微分学 Single Variable Differential Calculus
## 一、导数定义（牛顿）
* 瞬时变化率
* $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0) $$ 记为
* [注]
    * 1. 左右有别， $$ x_0 + \Delta x $$
        * $$ \lim_{\Delta x \to 0^+ } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f_+'(x_0) $$  右导数
        * $$ \lim_{\Delta x \to 0^- } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f_-'(x_0) $$  左导数
        * 故 $$f'(x_0) \exists  \Longleftrightarrow f_+'(x_0)=f_-'(x_0)$$
    * 2. $$ \Delta x \to t $$ 变量的广义化
         * $$ f'(x_0) \triangleq \lim_{t \to 0 } \frac{f(x_0 + t) - f(x_0)}{t}  $$ 
         * 学会凑出t
    * 3. 一静一动原则
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0 - \Delta x)}{2\Delta x} =f'(x_0) $$ 典型错误，这里是两动
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0) $$ 一静一动
        * 导数是瞬时变化率，所以里面必须有$$f(x_0)$$这个静点
    * 4.换元法 
        * 令$$ x_0 + \Delta x  = x $$
        * 等价写法 $$f'(x_0) = \lim_{ x \to x_0 } \frac{f(x) - f(x_0)}{x - x_0}  $$ 差值形式
        * $$ \lim_{\Delta x \to 0 } \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x} =f'(x_0)$$ 增量写法
* 见到$$f'(x_0)$$ 先用定义法来
* $$ h \to 0, \cos h \to 1^- , 1- \cos h \to 0^+$$
* $$\frac{|x|}x 在 x \to 0 时有界，但是极限不存在$$
* 2A-A≠A （A只是符号，只有A存在时才做数量运算）
## 二、计算
### 1.基本求导公式
* $$(x^\alpha)' = \alpha x^{\alpha -1} $$
* $$ (a^x)'=a^x \ln a ,(e^x)'=e^x$$
* $$(\ln x)'= \frac1x$$
* $$(\sin x)' = \cos x , (\cos x)'= -\sin x$$
* $$(\tan x)' = \sec^2 x , (\cot x)'= -\csc^2 x$$
* $$(\sec x)' = \sec x\tan x , (\csc x)'= -\csc x \cot x$$
* $$(\arcsin x)' = \frac1{\sqrt{1-x^2}} , (\arccos x)'= -\frac1{\sqrt{1-x^2}} $$
* $$(\arctan x)' = \frac1{1+x^2} , (\arccot x)'= -\frac1{1+x^2} $$





