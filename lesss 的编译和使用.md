##### lesss 的编译和使用

##### kolal编译工具
   -koala
   -国人开发的LESS/SASS编译工具
   -下载地址 ：http://koala-app.com/index-zh.html

#####  Node.js库

##### 浏览器端使用

#####  LESS中的注释
​       //-可以使用css中的注释
​         -也可以使用//注释
​       //编译时会自动过滤掉

##### LESS中的变量
 -@开头

 - @变量名：变量值  //写法
 - 

 混合（mixin）变量  两种形式
  -列如： .border{border:solid 10px red}
  带参数的混合

    - .border-radis(@radius){css代码  }
    可设定默认值
        - .border-radius(@radius:30px){css代码}
匹配模式
 -相当于Js中的if但不完全时
 -满足条件才能匹配
 LESS运算
 -任何数字、颜色或者变量都可以参与运算，运算应该被包裹在括号中
 列如 ： +-/*

#####  LESS中的嵌套
  -最有意思的小东西
  -两种用法
     & 对尾类使用
      -hover或focus
    对连接的使用
       &-item
@arguments变量
  @arguments包含了所有传递进来的参数
避免编译
 -有时候我们需要输出一些不正确的CSS语法或者使用一些LESS不认识的专有语法
 -要输出这样的值我们可以在字符串前加一个 ~
 列如：width：~'calc(100%-35)'
 !important关键字

  - 会为所有的混合所带来的样式，添加上！important