# 第三讲 一元函数积分学 Single Variable Integral Calculus
* 定义，计算，应用 
 
## 一、定义
* 1.不定积分
    * $$ \forall x \in I,使F'(x)=f(x),则称F(x)是f(x)在I上的一个原函数。$$
    * 全体原函数就叫不定积分，记成
    * $$ \int f(x)dx = F(x) + C $$
* 2.定积分
    *[小结]
         * $$ \int f(x)dx  ,函数族 $$
         * $$ \int_a^b f(x)dx ,面积值(数）$$
    * $$ N-L公式  \int_a^b f(x)dx = F(x)|_a^b = F(b) -F(a)$$
    

## 二、计算（四大方法）
* 1.凑微分法
    * 1.基本积分公式（熟稔于心）
        * $$ \int x^kdx=\frac1{k+1}x^{k+1}+C,k≠-1 $$
            * $$ \int \frac1{x^2}dx=-\frac1x+C $$
            * $$ \int \frac1{\sqrt x}dx=2\sqrt x+C $$
        * $$ \int \frac1xdx=\ln |x|+C $$
        * $$ \int a^xdx = \frac { a^x}{\ln a} + C $$
            * $$ \int e^xdx =  e^x + C $$
        * $$ \int \sin xdx= -\cos x + C $$
        * $$ \int \cos xdx= \sin x + C $$
        * $$ \int \tan xdx= -\ln|\cos x| + C $$
        * $$ \int \cot xdx= \ln |\sin x| + C $$
        * $$ \int \sec xdx= \ln |\sec x +\tan x| + C $$
        * $$ \int \csc xdx= \ln |\csc x -\cot x| + C $$
        * $$ \int \sec^2 xdx=  \tan x + C $$
        * $$ \int \csc^2 xdx=  -\cot x + C $$
        * $$ \int \sec x\tan xdx=  \sec x + C $$
        * $$ \int \csc x\cot xdx=  -\csc x + C $$
        * $$ \int \frac1{\sqrt{1- x^2}}dx=  \arcsin x + C $$
            * $$ \int \frac1{\sqrt{a^2- x^2}}dx= \int \frac1{\sqrt{1- (\frac xa)^2}}d(\frac xa) = \arcsin {\frac xa} + C $$
            * $$ \int \frac1{\sqrt{a^2 + x^2}}dx = \ln(x+ \sqrt{a^2 + x^2}) + C $$
            * $$ \int \frac1{\sqrt{x^2 -a^2}}dx = \ln(x+ \sqrt{x^2-a^2}) + C $$
        * $$ \int \frac1{1+ x^2}dx=  \arctan x + C $$
            * $$ \int \frac1{a^2+ x^2}dx=\frac 1a \int \frac1{1+ (\frac xa)^2}d(\frac xa) = \frac1a\arctan {\frac xa} + C $$
            * $$ \int \frac1{a^2 - x^2}dx=\frac 1{2a} \ln|\frac{a+x}{a-x}| + C $$
            * $$ \int \frac1{ x^2 - a^2}dx=\frac 1{2a} \ln|\frac{x-a}{x+a}| + C $$
        * $$ \int \sqrt{a^2- x^2}dx= \frac{a^2}2 \arcsin {\frac xa} +\frac x2\sqrt{a^2-x^2} + C $$
        * $$ 凑微分 \frac 1{\sqrt{u}}du=d(2\sqrt u)$$




 























 





        




        

 

