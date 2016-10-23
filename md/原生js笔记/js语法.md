
## JavaScript语句

- js 语句以行为单位，一行为一句话，每句话后用“；隔开”，两句话用也可以写在一行，分号前面可以没有任何内容，JavaScript引擎将其视为空语句。

- 表达式：一个为得到返回值的计算式eg:1+3就是一个表达式；

- 如果使用var重新声明一个已经存在的变量，是无效的。但是，如果第二次声明的同时还赋值了，则会覆盖掉前面的值。

#### 变量提升：
- JavaScript引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行。这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升（hoisting）。
```
console.log(a);
var a = 1;
```
上面代码首先使用console.log方法，在控制台（console）显示变量a的值。这时变量a还没有声明和赋值，所以这是一种错误的做法，但是实际上不会报错。因为存在变量提升，真正运行的是下面的代码。

#### 标识符：
- 标识符（identifier）是用来识别具体对象的一个名称。最常见的标识符就是变量名，以及后面要提到的函数名。JavaScript语言的标识符对大小写敏感，所以a和A是两个不同的标识符。
- **标识符有一套命名规则，不符合规则的就是非法标识符。JavaScript引擎遇到非法标识符，就会报错。
简单说，标识符命名规则如下：**

    ```
    第一个字符，可以是任意Unicode字母（包括英文字母和其他语言的字母），以及美元符号（$）和下划线（_）。
    第二个字符及后面的字符，除了Unicode字母、美元符号和下划线，还可以用数字0-9。
    中文是合法的标识符，可以用作变量名。
    var 临时变量 = 1;
    arg0     合法标识符    
    _tmp    合法标识符
    $elem    合法标识符
    π    合法标识符；

    1a  // 第一个字符不能是数字
    23  // 同上
    ***  // 标识符不能包含星号
    a+b  // 标识符不能包含加号
    -d  // 标识符不能包含减号或连词线
    ```
#### 保留字
- JavaScript有一些保留字，不能用作标识符；

  ```
  arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。
  ```
**另外，还有三个词虽然不是保留字，但是因为具有特别含义，也不应该用作标识符：Infinity、NaN、undefined。**

#### 注释

- :

    ```
    1.源码中被JavaScript引擎忽略的部分就叫做注释，它的作用是对代码进行解释。Javascript提供两种注释：一种是单行注释，用//起头；另一种是多行注释，放在"/* 和 *//*"之间。
    2. 此外，由于历史上JavaScript兼容HTML代码的注释，所以<!--和-->也被视为单行注释。
    3. 上面代码中，只有x = 1会执行，其他的部分都被注释掉了。
    4.需要注意的是，-->只有在行首，才会被当成单行注释，否则就是一个运算符。
    function countdown(n) {
    while (n --> 0) console.log(n);
    }
    countdown(3)
    // 2
    // 1
    // 0
    上面代码中，n --> 0实际上会当作n-- > 0，因此输出2、1、0。
    ```
#### 区块
- JavaScript使用大括号，将多个相关的语句组合在一起，称为“区块”（block）。

- 与大多数编程语言不一样，JavaScript的区块不构成单独的作用域（scope）。也就是说，区块中的变量与区块外的变量，属于同一个作用域。

```
{
  var a = 1;
}

a // 1
```
上面代码在区块内部，声明并赋值了变量a，然后在区块外部，变量a依然有效，这说明区块不构成单独的作用域，与不使用区块的情况没有任何区别。所以，单独使用的区块在JavaScript中意义不大，很少出现。区块往往用来构成其他更复杂的语法结构，比如for、if、while、function等。

## 条件语句

### if语句
- if结构先判断一个表达式的布尔值，然后根据布尔值的真伪，执行不同的语句。
