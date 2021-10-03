---
title: JavaScript基础知识总结
date: 2020-10-05
updated: 2021-01-22
tags: [Frontend]
categories: 编程与开发
references: 
  - title: learn x in y minutes
    url: https://learnxinyminutes.com/docs/zh-cn/javascript-cn/
---

> JavaScript 是一门跨平台、面向对象的脚本语言，它能使网页可交互，可以让你在网页上添加更多功能，另外还有高级的服务端 JavaScript 版本，在web浏览器中，JavaScript能够通过其所连接的环境提供的编程接口进行控制。在之前我已经简单总结了[HTML5/CSS3的必会知识点](/HTML和CSS基础)，为Javascript 学习打下基础，以下是我对于经常会使用到的 JavaScript 基础知识的总结，但不包括JS 库和框架的知识，会在之后再补上。

<!--more-->

### Javascript 介绍

- Javascript 于 1995 年由网景公司的 Brendan Eich 发明，最初它作为一种简单的，用于开发网站的脚本语言而被发明出来，是用于开发复杂网站的 Java 的补充=
- 但由于它与网页结合度很高并且在浏览器中得到内置的支持，所以在网页前端领域 Javascript 变得比 Java 更流行了
- 不过，Javascript 不仅用于网页浏览器，一个名为 `Node.js` 的项目提供了面向 Google Chrome V8 引擎的独立运行时环境，它正在变得越来越流行

### 数字、字符串与操作符

- 注释
  ```javascript
  // 单行注释
  /* 多行
     注释 */
  ```

- 通过单引号或双引号来构造字符串，字符串用 `+` 连接，可以用 `< 、>` 来比较

  ```javascript
  "Hello " + "world!";    // = "Hello world!"
  ```

- 用 `!` 来取非，`===` 相等，`!==` 不等

  ```javascript
  !true;    // = false
  1 === 1;    // = true
  2 !== 1;    // = true
  ```

- Javascript 只有一种数字类型（64位 IEEE 754 双精度浮点 double）

  ```javascript
  5 / 2;    // = 2.5
  ```

- 当你对浮点数进行位运算时，浮点数会转换为至多 32 位的无符号整数

  ```javascript
  1 << 2;    // = 4
  ```

- 有三种非数字的数字类型

  - `Infinity;`（1/0 的结果）
  - `-Infinity;`（-1/0 的结果）
  - `NaN;`（0/0 的结果）

- 使用 `==` 比较时会进行类型转换

  ```javascript
  null == undefined;    // = true
  ```

- 可以用 `charAt` 来得到字符串中的字符，或使用 `substring` 来获取更大的部分

  ```javascript
  "This is a string".charAt(0);    // = 'T'
  "Hello world".substring(0, 5);   // = "Hello"
  ```

- `length` 是一个属性，表示长度

  ```javascript
  "Hello".length;    // = 5
  ```

- `null;` 用来表示刻意设置的空值，`undefined;` 用来表示还没有设置的值（`undefined` 自身实际是一个值）

- 0 是逻辑假而  "0" 是逻辑真，0 == "0"

### 变量、数组和对象

- 变量用 `var` 关键字声明，无需指定类型，赋值需要用 `=` 

- 声明时没有加 `var` 关键字就会在全局作用域创建变量，而你定义的当前作用域

- 没有被赋值的变量都会被设置为undefined

  ```javascript
  var someVar = 5;
  var someThirdVar;    // = undefined
  ```

- 数组是任意类型组成的有序列表，数组的元素可以用方括号下标来访问

  ```javascript
  var myArray = ["Hello", 45, true];
  myArray[1];   // = 45
  ```

-  数组是可变的，并拥有变量 length

  ```javascript
  myArray.push("World");
  myArray[3] = "Hello";
  myArray.length;    // = 4
  ```

- Javascript 中的对象相当于其他语言中的“字典”或“映射”（键-值对的无序集合）

  ```javascript
  var myObj = {myKey: "myValue", "my other key": 4};
  myObj["my other key"];    // = 4
  myObj.myKey;    // = "myValue"
  ```

- 对象是可变的；值也可以被更改或增加新的键

  ```javascript
  myObj.myThirdKey = true;
  myObj.myFourthKey;    // = undefined
  ```

### 逻辑与控制结构

-  Javascript 的 if 、while、for 语法与 Java 的语法几乎完全相同

- if 语句

  ```javascript
  var count = 1;
  if (count == 3){
      // count 是 3 时执行
  } else if (count == 4){
      // count 是 4 时执行
  } else {
      // 其他情况下执行 
  }
  ```

-  while 循环

  ```javascript
  while (true) {
      // 无限循环
  }
  ```

-  Do-while循环

  ```javascript
  var input;
  do {
      input = getInput();
  } while (!isValid(input))
  ```

- for 循环 

  ```javascript
  for (var i = 0; i < 5; i++){
      // 遍历5次
  }
  ```

- `&&` 是逻辑与，`||` 是逻辑或

  ```javascript
  if (house.size == "big" && house.colour == "blue"){
      house.contains = "bear";
  }
  if (colour == "red" || colour == "blue"){
      // colour是red或者blue时执行
  }
  ```

- 短路语句

  ```javascript
  var name = otherName || "default";    //在设定初始化值时特别有用
  ```

- switch 语句使用 `===` 检查相等性，在每一个 case 结束时使用 break ，否则其后的 case 语句也将被执行

  ```javascript
  grade = 'B';
  switch (grade) {
    case 'A':
      console.log("Great job");
      break;
    case 'B':
      console.log("OK job");
      break;
    case 'C':
      console.log("You can do better");
      break;
    default:
      console.log("Oy vey");
      break;
  }
  ```

### 函数、作用域、闭包

- JavaScript 函数由 `function` 关键字定义

  ```javascript
  function myFunction(thing){
      return thing.toUpperCase();
  }
  myFunction("foo");    // = "FOO"
  ```

- 函数也能够赋给一个变量，并且被作为参数传递

  ```javascript
  function myFunction(){
      // 这段代码将在5秒钟后被调用
  }
  setTimeout(myFunction, 5000);    // setTimeout不是js语言的一部分，而是由浏览器和Node.js提供的
  ```

- 函数对象不需要声明名称，可以直接把一个函数定义写到另一个函数的参数中

  ```javascript
  setTimeout(function(){
      // 这段代码将在5秒钟后被调用
  }, 5000);
  ```

- JavaScript 有函数作用域：函数有其自己的作用域而其他的代码块则没有

  ```javascript
  if (true){
      var i = 5;
  }
  i;     // = 5
  ```

- “立即执行匿名函数”可以避免一些临时变量扩散到全局作用域去

  ```javascript
  (function(){
      var temporary = 5;
      window.permanent = 10;
  })();
  temporary; // 抛出引用异常ReferenceError
  permanent; // = 10
  ```

  - 我们可以访问修改全局对象（"global object"）来访问全局作用域，在web浏览器中是 window 这个对象，在其他环境如Node.js中这个对象的名字可能会不同

- 闭包：如果一个函数在另一个函数中定义，那么这个内部函数就拥有外部函数的所有变量的访问权，即使在外部函数结束之后

  - 内部函数默认是放在局部作用域的，就像是用 `var` 声明的

  ```javascript
  function sayHelloInFiveSeconds(name){
      var prompt = "Hello, " + name + "!";
      function inner(){
          alert(prompt);
      }
      setTimeout(inner, 5000);
  }
  sayHelloInFiveSeconds("Adam");     // 会在5秒后弹出 "Hello, Adam!"
  ```

  - setTimeout 是异步的，所以 sayHelloInFiveSeconds 函数会立即退出，而 setTimeout 会在后面调用 inner
  - 然而，由于 inner 是由 sayHelloInFiveSeconds 闭合包含的，所以 inner 在其最终被调用时仍然能够访问 `prompt` 变量

###  对象、构造函数与原型

- 对象可以包含方法

  ```javascript
  var myObj = {
      myFunc: function(){
          return "Hello world!";
      }
  };
  myObj.myFunc();    // = "Hello world!"
  ```

-  当对象中的函数被调用时，这个函数可以通过 `this` 关键字访问其依附的这个对象

  ```javascript
  myObj = {
      myString: "Hello world!",
      myFunc: function(){
          return this.myString;
      }
  };
  myObj.myFunc(); // = "Hello world!"
  ```

-  但上面这个函数访问的其实是其运行时环境，而非定义时环境，即取决于函数是如何调用的，所以如果函数被调用时不在这个对象的上下文中，就不会运行成功了

  ```javascript
  var myFunc = myObj.myFunc;
  myFunc(); // = undefined
  ```

- 相应的，一个函数也可以被指定为一个对象的方法，并且可以通过 `this` 访问，即使这个对象的成员在函数被定义时并没有依附在对象上

  ```javascript
  var myOtherFunc = function(){
      return this.myString.toUpperCase();
  }
  myObj.myOtherFunc = myOtherFunc;
  myObj.myOtherFunc();     // = "HELLO WORLD!"
  ```

- 通过 `call` 或者 `apply` 调用函数的时候，也可以为其指定一个执行上下文

  ```javascript
  var anotherFunc = function(s){
      return this.myString + s;
  }
  anotherFunc.call(myObj, " And Hello Moon!");     // = "Hello World! And Hello Moon!"
  ```

- `apply` 函数几乎完全一样，只是要求一个 array 来传递参数列表（当一个函数接受一系列参数，而你想传入一个 array 时特别有用）

  ```javascript
  anotherFunc.apply(myObj, [" And Hello Sun!"]); // = "Hello World! And Hello Sun!"
  Math.min(42, 6, 27);     // = 6
  Math.min([42, 6, 27]);     // = NaN (uh-oh!)
  Math.min.apply(Math, [42, 6, 27]);     // = 6
  ```

- `call` 和 `apply` 只是临时的，如果=希望函数附着在对象上，可以使用 `bind`

  ```javascript
  var boundFunc = anotherFunc.bind(myObj);
  boundFunc(" And Hello Saturn!");     // = "Hello World! And Hello Saturn!"
  ```

- `bind`  也可以用来部分应用一个函数（柯里化）

  ```javascript
  var product = function(a, b){ return a * b; }
  var doubler = product.bind(this, 2);
  doubler(8);     // = 16
  ```

- 构造函数：通过 `new` 关键字调用一个函数时，就会创建一个对象，而且可以通过 `this` 关键字访问该函数

  ```javascript
  var MyConstructor = function(){
      this.myNumber = 5;
  }
  myNewObj = new MyConstructor();     // = {myNumber: 5}
  myNewObj.myNumber;     // = 5
  ```

- 每一个 js 对象都有一个原型，当你要访问一个实际对象中没有定义的一个属性时，解释器就回去找这个对象的原型

  - 一些 JS 实现会让你通过 `__proto__` 属性访问一个对象的原型
  - `__proto__` 并非标准规定，实际上也没有标准办法来修改一个已存在对象的原型

  ```javascript
  var myObj = {
      myString: "Hello world!"
  };
  var myPrototype = {
      meaningOfLife: 42,
      myFunc: function(){
          return this.myString.toLowerCase()
      }
  };
  myObj.__proto__ = myPrototype;
  myObj.meaningOfLife; // = 42
  // 函数也可以工作。
  myObj.myFunc() // = "hello world!"
  // 如果要访问的成员在原型当中也没有定义的话，解释器就会去找原型的原型
  myPrototype.__proto__ = {
      myBoolean: true
  };
  myObj.myBoolean; // = true
  // 这其中并没有对象的拷贝；每个对象实际上是持有原型对象的引用
  // 这意味着当我们改变对象的原型时，会影响到其他以这个原型为原型的对象
  myPrototype.meaningOfLife = 43;
  myObj.meaningOfLife;     // = 43
  ```

- 两种方式为指定原型创建一个新的对象

  - 第一种方式是 `Object.create`

  ```javascript
  var myObj = Object.create(myPrototype);
  myObj.meaningOfLife;     // = 43
  ```

  - 第二种方式必须通过构造函数和 new 关键字创建新对象的原型

  ```javascript
  MyConstructor.prototype = {
      myNumber: 5,
      getMyNumber: function(){
          return this.myNumber;
      }
  };
  var myNewObj2 = new MyConstructor();
  myNewObj2.getMyNumber(); // = 5
  myNewObj2.myNumber = 6
  myNewObj2.getMyNumber(); // = 6
  // 字符串和数字等内置类型也有通过构造函数来创建的包装类型
  var myNumber = 12;
  var myNumberObj = new Number(12);
  myNumber == myNumberObj; // = true
  // 但是它们并非严格等价
  typeof myNumber; // = 'number'
  typeof myNumberObj; // = 'object'
  myNumber === myNumberObj; // = false
  if (0){
      // 这段代码不会执行，因为0代表假
  }
  // 不过，包装类型和内置类型共享一个原型，
  // 所以你实际可以给内置类型也增加一些功能，例如对string：
  String.prototype.firstCharacter = function(){
      return this.charAt(0);
  }
  "abc".firstCharacter(); // = "a"
  ```

  - `Object.create` 并没有在所有的版本中都实现，但是仍然可以通过代码填充来实现兼容

  ```javascript
  if (Object.create === undefined){ // 如果存在则不覆盖
      Object.create = function(proto){
          // 用正确的原型来创建一个临时构造函数
          var Constructor = function(){};
          Constructor.prototype = proto;
          // 之后用它来创建一个新的对象
          return new Constructor();
      }
  }
  ```

