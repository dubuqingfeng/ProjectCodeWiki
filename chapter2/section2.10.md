本文档的目标是使JS代码风格保持一致，容易被理解和被维护

## JS编码规范

---

### 结构
#### 缩进
* 【强制】使用4个空格做为一个缩进层级，不允许使用2个空格或tab字符。
* 【强制】`switch`下的`case`和`default`必须增加一个缩进层级。

```javascript

    // good
    switch(variable){
        case '1':
            // do...
            break;
        case '2':
            // do...
            break;
        default:
            // do...
    }

    // bad
    switch(variable){
    case '1':
        // do...
        break;
    case '2':
        // do...
        break;
    default:
        // do...
    }
```

#### 空格
* 【强制】二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

```javascript

    var a = !arr.length;
    a++;
    a = b + c;
```
* 【强制】在对象创建时，属性中的`:`之后必须有空格，`:`之前不允许有空格。
```javascript

    // good
    var obj = {
        a: 1,
        b: 2,
        c: 3
    };

    // bad
    var obj = {
        a : 1,
        b:2,
        c :3
    };
```
* 【强制】单行声明的数组与对象，如果包含元素，`{}`和`[]`内紧贴括号部分不允许包含空格。
```javascript

    // good
    var arr1 = [];
    var arr2 = [1, 2, 3];
    var obj1 = {};
    var obj2 = {name: 'obj'};
    var obj3 = {
        name: 'obj',
        age: 20,
        sex: 1
    };

    // bad
    var arr1 = [ ];
    var arr2 = [ 1, 2, 3 ];
    var obj1 = { };
    var obj2 = { name: 'obj' };
    var obj3 = {name: 'obj', age: 20, sex: 1};
```
* 【强制】每行不得超过120个字符。超长的不可分割的代码允许例外，比如复杂的正则表达式。长字符串不在例外之列。

* 用作代码块起始的左花括号`{`前不能有空格。

```javascript

    // good
    if(condition){
    }

    while(condition){
    }

    function funcName(){
    }

    // bad
    if (condition){
    }

    while (condition) {
    }

    function funcName() {
    }
```

* 函数声明、具名函数表达式、函数调用中，函数名和`(`之间不允许有空格。

```javascript

    // good
    function funcName(){
    }

    var funcName = function funcName(){
    };

    funcName();

    // bad
    function funcName () {
    }

    var funcName = function funcName () {
    };

    funcName ();
```
* `,`和`;`前不允许有空格。
```javascript

    // good
    callFunc(a, b);

    // bad
    callFunc(a , b) ;
```
* 在函数调用、函数声明、括号表达式、属性访问、if / for / while / switch / catch 等语句中，() 和 [] 内紧贴括号部分不允许有空格。
```javascript

    // good
    callFunc(param1, param2, param3);

    save(this.list[this.indexes[i]]);

    needIncream && (variable += increament);

    if(num > list.length){
    }

    while(len--){
    }


    // bad
    callFunc( param1, param2, param3 );

    save( this.list[ this.indexes[ i ] ] );

    needIncreament && ( variable += increament );

    if ( num > list.length ) {
    }

    while ( len-- ) {
    }
```

#### 语句
* 【强制】不得省略语句结束的分号。
* 【强制】在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块`{...}`。
```javascript
    // good
    if(condition){
        callFunc();
    }

    // bad
    if (condition) callFunc();
    if (condition)
        callFunc();
```
* 运算符处换行时，运算符必须在新行的行首。

```javascript

    // good
    if(user.isAuthenticated()
        && user.isInRole('admin')
        && user.hasAuthority('add-admin')
        || user.hasAuthority('delete-admin')
    ){
        // Code
    }

    var result = number1 + number2 + number3
        * number4 + number5;


    // bad
    if (user.isAuthenticated() &&
        user.isInRole('admin') &&
        user.hasAuthority('add-admin') ||
        user.hasAuthority('delete-admin')) {
        // Code
    }

    var result = number1 + number2 + number3 +
        number4 + number5;
```
* 在 if / else / for / do / while 语句中，即使只有一行，也不得省略块 {...}。

```javascript

    // good
    if(condition){
        callFunc();
    }

    // bad
    if(condition) callFunc();
    if(condition)
        callFunc();
```
* 函数定义结束不允许添加分号。
```javascript

    // good
    function funcName(){
    }

    // bad
    function funcName(){
    };

    // 如果是函数表达式，分号是不允许省略的。
    var funcName = function(){
    };
```
* IIFE(匿名函数自调用)必须在函数表达式外添加`(`，非`IIFE`不得在函数表达式外添加`(`。
    - 额外的 ( 能够让代码在阅读的一开始就能判断函数是否立即被调用，进而明白接下来代码的用途。而不是一直拖到底部才恍然大悟。
```javascript

    // good
    var task = (function(){
       // Code
       return result;
    })();

    var func = function(){
    };


    // bad
    var task = function(){
        // Code
        return result;
    }();

    var func =(function (){
    });
```
* 尽可能使用简洁的表达式。
```javascript

    // 字符串为空
    // good
    if(!name){
        // ......
    }
    // bad
    if(name === ''){
        // ......
    }

    // 字符串非空
    // good
    if(name){
        // ......
    }
    // bad
    if(name !== ''){
        // ......
    }

    // 数组非空
    // good
    if(collection.length){
        // ......
    }
    // bad
    if(collection.length > 0){
        // ......
    }

    // 布尔不成立
    // good
    if(!notTrue){
        // ......
    }
    // bad
    if(notTrue === false){
        // ......
    }

    // null 或 undefined
    // good
    if(noValue == null){
      // ......
    }
    // bad
    if(noValue === null || typeof noValue === 'undefined'){
      // ......
    }
```

---

### 命名
* 【强制】变量、函数、参数、属性使用Camel命名法 。
```javascript
    var loadingModules = {
        myName: ''
    };

    function stringFormat(mySource) {
    }
```
* 【强制】常量使用全部字母大写，单词间`_`分隔的命名方式。
```javascript
    var HTML_ENTITY = {};
```
* 【强制】类使用Pascal命名法。
```javascript
    function TextNode(options) {
    }
```
* 【强制】jquery对象的引用必须要以`$`开头
```javascript

    var $body = $('body');
    var $demo = $('#demo');
```
* 【强制】类名使用名词。
* 【强制】函数名使用动宾短语。
* 【建议】`boolean`类型的变量使用`is`或`has`开头。

---

### 注释（该部分暂时按该方案执行，等调研jsDoc之后可能会稍有调整）
#### 单行注释
* 【强制】必须独占一行。

#### 文件注释
* 【强制】文件顶部必须包含文件注释，用`@file`标识文件说明。
```javascript
    /**
     * @file Describe the file
     */
```
* 【建议】文件注释中可以用`@author`标识开发者信息。
```javascript
    /**
     * @file Describe the file
     * @author author-name(mail-name@domain.com)
     *         author-name2(mail-name2@domain.com)
     */
```

#### 类注释
* 【建议】使用`@class`标记类或构造函数。
```javascript
    /**
     * 描述
     *
     * @class
     */
    function Developer(){
        // constructor body
    }
```
* 【建议】使用`@extends`标记类的继承信息。
```javascript
    /**
     * 描述
     *
     * @class
     * @extends Developer
     */
    function Fronteer(){
        Developer.call(this);
        // constructor body
    }
    util.inherits(Fronteer, Developer);
```
* 【建议】类的属性或方法等成员信息使用`@public / @private`中的任意一个，指明可访问性。
```javascript
    /**
     * 类描述
     *
     * @class
     * @extends Developer
     */
    var Fronteer = function(){
        Developer.call(this);

        /**
         * 属性描述
         *
         * @type {string}
         * @private
         */
        this._level = 'T12';

        // constructor body
    };
    util.inherits(Fronteer, Developer);

    /**
     * 方法描述
     *
     * @private
     * @return {string} 返回值描述
     */
    Fronteer.prototype._getLevel = function(){
    };
```

#### 函数/方法注释
* 【强制】函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。
* 【强制】参数和返回值注释必须包含类型信息和说明。
* 【建议】当函数是内部函数，外部不可访问时，可以使用`@inner`标识。

```javascript

    /**
     * 函数描述
     *
     * @param {string} p1 参数1的说明
     * @param {string} p2 参数2的说明，比较长
     *     那就换行了.
     * @param {number=} p3 参数3的说明（可选）
     * @return {Object} 返回值描述
     */
    function foo(p1, p2, p3){
        var p3 = p3 || 10;
        return {
            p1: p1,
            p2: p2,
            p3: p3
        };
    }
```

#### 常量注释
* 【强制】常量必须使用 @const 标记，并包含说明和类型信息。

---

### 变量声明
* 【强制】变量在使用前必须通过 var 定义。

```javascript

    // good
    var name = 'MyName';

    // bad
    name = 'MyName';
```
* 【强制】每个`var`只能声明一个变量。
    1. 一个`var`声明多个变量，容易导致较长的行长度。
    2. 在修改时容易造成逗号和分号的混淆。
```javascript

    // good
    var hangModules = [];
    var missModules = [];
    var visited = {};

    // bad
    var hangModules = [],
        missModules = [],
        visited = {};
```
* 【建议】__变量必须即用即声明__，不得在函数或其它形式的代码块起始位置统一声明所有变量。
    1. 变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。虽然JavaScript的变量是函数作用域，还是应该根据编程中的意图，缩小变量出现的距离空间。

```javascript

    // good
    function kv2List(source){
        var list = [];
        for(var key in source){
            if(source.hasOwnProperty(key)){
                var item = {
                    k: key,
                    v: source[key]
                };
                list.push(item);
            }
        }
        return list;
    }

    // bad
    function kv2List(source){
        var list = [];
        var key;
        var item;
        for(key in source){
            if(source.hasOwnProperty(key)){
                item = {
                    k: key,
                    v: source[key]
                };
                list.push(item);
            }
        }
        return list;
    }
```

---

### 字符串
* 【强制】字符串开头和结束使用单引号`'`。
    - 输入单引号不需要按住`shift`，方便输入。
    - 实际使用中，字符串经常用来拼接HTML。为方便HTML中包含双引号而不需要转义写法。

```javascript

    var str = '我是一个字符串';
    var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```

---

### 对象
* 不允许修改和扩展任何原生对象和宿主对象的原型。

```javascript

    // 以下行为绝对禁止
    String.prototype.trim = function(){
    };
```

---

### 数组
* 遍历数组不使用`for in`。
    - 数组对象可能存在数字以外的属性, 这种情况下`for in`不会得到正确结果。

```javascript

    var arr = ['a', 'b', 'c'];
    arr.other = 'other things'; // 这里仅作演示, 实际中应使用Object类型

    // 正确的遍历方式
    for(var i = 0, len = arr.length; i < len; i++){
        console.log(i);
    }

    // 错误的遍历方式
    for(i in arr){
        console.log(i);
    }
```

---

### 函数
* 【建议】一个函数的长度控制在50行以内。

### 事件
* 自定义事件的事件名必须全小写。
    - 在JavaScript广泛应用的浏览器环境，绝大多数DOM事件名称都是全小写的。为了遵循大多数JavaScript开发者的习惯，在设计自定义事件时，事件名也应该全小写。

