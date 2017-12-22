# CSS书写规范


## 1.代码风格


### 1.1 结构

#### 1.1.1 缩进

[强制] 使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。


[强制] switch 下的 case 和 default 必须增加一个缩进层级。

示例：

```javascript
// good
switch (variable) {
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
switch (variable) {
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

----------------


#### 1.1.2  空格


[强制] 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

示例：

```javascript
var a = !arr.length;
a++;
a = b + c;
```


[强制] 用作代码块起始的左花括号 { 前必须有一个空格。

示例：

```javascript
// good
if (condition) {
}
while (condition) {
}
function funcName() {
}
// bad
if (condition){
}
while (condition){
}
function funcName(){
}
```


[强制] if / else / for / while / function / switch / do / try / catch / finally 关键字后，必须有一个空格。

示例：

```javascript
// good
if (condition) {
}
while (condition) {
}

(function () {
})();
// bad
if(condition) {
}
while(condition) {
}

(function() {
})();
```


[强制] 在对象创建时，属性中的 : 之后必须有空格，: 之前不允许有空格。

示例：

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


[强制] 函数声明、具名函数表达式、函数调用中，函数名和 ( 之间不允许有空格。

示例：

```javascript
// good
function funcName() {
}
var funcName = function funcName() {
};
funcName();
// bad
function funcName () {
}
var funcName = function funcName () {
};
funcName ();
```


[强制] , 和 ; 前不允许有空格。

示例：

```javascript
// goodcallFunc(a, b);
// badcallFunc(a , b) ;
```


[强制] 在函数调用、函数声明、括号表达式、属性访问、if / for / while / switch / catch 等语句中，() 和 [] 内紧贴括号部分不允许有空格。

示例：

```javascript
// good
callFunc(param1, param2, param3);
save(this.list[this.indexes[i]]);

needIncream && (variable += increament);
if (num > list.length) {
}
while (len--) {
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


[强制] 单行声明的数组与对象，如果包含元素，{} 和 [] 内紧贴括号部分不允许包含空格。

解释：

声明包含元素的数组与对象，只有当内部元素的形式较为简单时，才允许写在一行。元素复杂的情况，还是应该换行书写。

示例：

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

[强制] 行尾不得有多余的空格。

----------------


### 1.1.3 换行

[强制] 每个独立语句结束后必须换行。

[强制] 每行不得超过 120 个字符。

解释：

超长的不可分割的代码允许例外，比如复杂的正则表达式。长字符串不在例外之列。


[强制] 运算符处换行时，运算符必须在新行的行首。

示例：

```javascript
// good
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}
var result = number1 + number2 + number3
    + number4 + number5;

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


[强制] 在函数声明、函数表达式、函数调用、对象创建、数组创建、for语句等场景中，不允许在 , 或 ; 前换行。

示例：

```javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// bad
var obj = {
    a: 1
    , b: 2
    , c: 3
};
foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
);
```


[建议] 不同行为或逻辑的语句集，使用空行隔开，更易阅读。

示例：

```javascript
// 仅为按逻辑换行的示例，不代表setStyle的最优实现function setStyle(element, property, value) {
    if (element == null) {
        return;
    }

    element.style[property] = value;
}
```


[建议] 在语句的行长度超过 120 时，根据逻辑条件合理缩进。

示例：

```javascript
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。// 建议最终将右括号 )
与左大括号 { 放在独立一行，保证与 if 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 按一定长度截断字符串，并使用 + 运算符进行连接。// 分隔字符串尽量按语义进行，如不要在一个完整的名词中间断开。
// 特别的，对于HTML片段的拼接，通过缩进，保持和HTML相同的结构。var html = '' // 此处用一个空字符串，以便整个HTML片段都在新行严格对齐
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 + 更容易调整缩进。var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 也可以按逻辑对参数进行组合。// 最经典的是baidu.format函数，调用时将参数分为“模板”和“数据”两块
baidu.format(
    dateFormatTemplate,
    year,
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如setTimeout函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);
order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 链式调用较长时采用缩进进行调整。
$('#items')
    .find('.selected')
    .highlight()
    .end();

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;
var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;

// 数组和对象初始化的混用，严格按照每个对象的 { 和结束 } 在独立一行的风格书写。
var array = [
    {
        // ...
    },
    {
        // ...
    }
];
```


[建议] 对于 if...else...、try...catch...finally 等语句，推荐使用在 } 号后添加一个换行 的风格，使代码层次结构更清晰，阅读性更好。

示例：

```javascript
if (condition) {
    // some statements;
}else {
    // some statements;
}
try {
    // some statements;
}catch (ex) {
    // some statements;
}
```

-----------------


### 1.1.4 语句


[强制] 不得省略语句结束的分号。


[强制] 在 if / else / for / do / while 语句中，即使只有一行，也不得省略块 {...}。

示例：
```javascript
// good
if (condition) {
    callFunc();
}
// bad
if (condition) callFunc();if (condition)
    callFunc();
```


[强制] 函数定义结束不允许添加分号。

示例：
```javascript
// good
function funcName() {
}
// bad
function funcName() {
};
// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```


[强制] IIFE 必须在函数表达式外添加 (，非 IIFE 不得在函数表达式外添加 (。

解释：

IIFE = Immediately-Invoked Function Expression.

额外的 ( 能够让代码在阅读的一开始就能判断函数是否立即被调用，进而明白接下来代码的用途。而不是一直拖到底部才恍然大悟。

示例：

```javascript
// good
var task = (function () {
   // Code
   return result;
})();
var func = function () {
};

// bad
var task = function () {
    // Code
    return result;
}();
var func = (function () {
});
```


-----------------

### 1.2 命名


[强制] 变量 使用 Camel命名法。

示例：

```javascript
var loadingModules = {};
```


[强制] 常量 使用 全部字母大写，单词间下划线分隔 的命名方式。

示例：

```javascript
var HTML_ENTITY = {};
```


[强制] 函数 使用 Camel命名法。

示例：

```javascript
function stringFormat(source) {
}
```


[强制] 函数的 参数 使用 Camel命名法。

示例:

```javascript
function hear(theBells) {
}
```


[强制] 类 使用 Pascal命名法。

示例：

```javascript
function TextNode(options) {
}
```


[强制] 类的 方法 / 属性 使用 Camel命名法。

示例：

```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}
TextNode.prototype.clone = function () {
    return this;
};
```


[强制] 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。

示例：

```javascript
function XMLParser() {
}
function insertHTML(element, html) {
}
var httpRequest = new HTTPRequest();
```


[强制] 类名 使用 名词。

示例：

```javascript
function Engine(options) {
}
```


[建议] 函数名 使用 动宾短语。

示例：

```javascript
function getStyle(element) {
}
```


[建议] boolean 类型的变量使用 is 或 has 开头。

示例：

```javascript
var isReady = false;var hasMoreCommands = false;
```


[建议] Promise对象 用 动宾短语的进行时 表达。

示例：

```javascript
var loadingData = ajax.get('url');
loadingData.then(callback);
```


-------------


### 1.3 注释

#### 1.3.1 单行注释

[强制] 必须独占一行。// 后跟一个空格，缩进与下一行被注释说明的代码一致。


--------------


#### 1.3.2 多行注释

[建议] 避免使用 /*...*/ 这样的多行注释。有多行注释内容时，使用多个单行注释。


--------------

#### 1.3.3 文档化注释

[强制] 为了便于代码阅读和自文档化，以下内容必须包含以 /**...*/ 形式的块注释中。

解释：
* 文件
* namespace
* 类
* 函数或方法
* 类属性
* 事件
* 全局变量
* 常量
* AMD 模块

[强制] 文档注释前必须空一行。

[建议] 自文档化的文档说明 what，而不是 how。


--------------

#### 1.3.4 类型定义

[强制] 类型定义都是以{开始, 以}结束。

解释：

常用类型如：{string}, {number}, {boolean}, {Object}, {Function}, {RegExp}, {Array}, {Date}。

类型不仅局限于内置的类型，也可以是自定义的类型。比如定义了一个类 Developer，就可以使用它来定义一个参数和返回值的类型。


[强制] 对于基本类型 {string}, {number}, {boolean}，首字母必须小写。

| 类型定义         | 语法示例                            |  解释     						           |
| --------------- | ----------------------------------- | ----------------------------------------- |
| String          |  {string}                           | --         						           |  
| Number          |  {number}                           | --            						       |  
| Boolean         |  {boolean}                          | --    						               | 
| Object          |  {Object}                           | --                                        |      
| Function        |  {Function}                         | --                                        |              
| RegExp          |  {RegExp}                           | --                                        |               
| Array           |  {Array}                            | --                                        |       
| Date            |  {Date}                             | --                                        |  
| 单一类型集合     |  {Array.<string>}                   | string 类型的数组                          |  
| 多类型           |  {(number｜boolean)}               | 可能是 number 类型, 也可能是 boolean 类型    | 
| 允许为null       |  {?number}                         | 可能是 number, 也可能是 null                |  
| 不允许为null     | {!Object}                          | Object 类型, 但不是 null                    |
| Function类型     | {function(number, boolean)}        | 函数, 形参类型                              |
| Function带返回值 | {function(number, boolean):string} | 函数, 形参, 返回值类型                       | 
| 参数可选         | @param {string=} name              | 可选参数, =为类型后缀                        |
| 可变参数         | @param {...number} args            | 变长参数, ...为类型前缀                      |
| 任意类型         | {*}                                | 任意类型                                    |
| 可选任意类型     | @param {*=} name                    | 可选参数，类型不限                          |
| 可变任意类型     | @param {...*} args                  | 变长参数，类型不限                          |
        
#### 1.3.5 注释
  
[强制] 有时我们会使用一些特殊标记进行说明。特殊标记必须使用单行注释的形式。下面列举了一些常用标记：

解释：
* TODO: 有功能待实现。此时需要对将要实现的功能进行简单说明。
* FIXME: 该处代码运行没问题，但可能由于时间赶或者其他原因，需要修正。此时需要对如何修正进行简单说明。
* HACK: 为修正某些问题而写的不太好或者使用了某些诡异手段的代码。此时需要对思路或诡异手段进行描述。
* XXX: 该处存在陷阱。此时需要对陷阱进行描述。
      

--------------

## 2 语言特性


### 2.1 变量

[强制] 每个 var 只能声明一个变量。

解释：

一个 var 声明多个变量，容易导致较长的行长度，并且在修改时容易造成逗号和分号的混淆。

示例：

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

[强制] 变量必须 即用即声明，不得在函数或其它形式的代码块起始位置统一声明所有变量。

解释：

变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。虽然JavaScript的变量是函数作用域，还是应该根据编程中的意图，缩小变量出现的距离空间。

示例：
```javascript
// good
function kv2List(source) {
    var list = [];

    for (var key in source) {
        if (source.hasOwnProperty(key)) {
            var item = {
                k: key,
                v: source[key]
            };
            list.push(item);
        }
    }

    return list;
}
// badfunction kv2List(source) {
    var list = [];
    var key;
    var item;

    for (key in source) {
        if (source.hasOwnProperty(key)) {
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

-------------------


### 2.2 条件

[强制] 在 Equality Expression 中使用类型严格的 ===。仅当判断 null 或 undefined 时，允许使用 == null。

解释：

使用 === 可以避免等于判断中隐式的类型转换。

示例：
```javascript
// good
if (age === 30) {
    // ......
}
// bad
if (age == 30) {
    // ......
}
```

[建议] 尽可能使用简洁的表达式。

示例：
```javascript
// 字符串为空
// good
if (!name) {
    // ......
}
// bad
if (name === '') {
    // ......
}
// 字符串非空
// good
if (name) {
    // ......
}
// bad
if (name !== '') {
    // ......
}
// 数组非空
// good
if (collection.length) {
    // ......
}
// bad
if (collection.length > 0) {
    // ......
}
// 布尔不成立
// good
if (!notTrue) {
    // ......
}
// bad
if (notTrue === false) {
    // ......
}
// null 或 undefined
// good
if (noValue == null) {
  // ......
}
// bad
if (noValue === null || typeof noValue === 'undefined') {
  // ......
}
```

[建议] 按执行频率排列分支的顺序。

解释：
* 按执行频率排列分支的顺序好处是：
* 阅读的人容易找到最常见的情况，增加可读性。
* 提高执行效率。

[建议] 对于相同变量或表达式的多值条件，用 switch 代替 if。

示例：
```javascript
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}
// bad
var type = typeof variable;
if (type === 'object') {
    // ......
} else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```
----------------

### 2.3 循环

[建议] 对有序集合进行遍历时，缓存 length。

解释：

虽然现代浏览器都对数组长度进行了缓存，但对于一些宿主对象和老旧浏览器的数组对象，在每次 length 访问时会动态计算元素个数，此时缓存 length 能有效提高程序性能。

示例：
```javacript
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    // ......
}
```

[建议] 对有序集合进行顺序无关的遍历时，使用逆序遍历。

解释：

逆序遍历可以节省变量，代码比较优化。

示例：
```javascript
var len = elements.length;
while (len--) {
    var element = elements[len];
    // ......
}
```
----------------

### 2.4 类型

#### 2.4.1 类型转换

[建议] 转换成 string 时，使用 + ''。

示例：
```javacript
// good
num + '';
// bad
new String(num);
num.toString();
String(num);
```

[建议] 转换成 number 时，通常使用 +。

示例：
```javacript
// good
+str;
// bad
Number(str);
```

[建议] number 去除小数点，使用 Math.floor / Math.round / Math.ceil，不使用 parseInt。

示例：
```javasript
// good
var num = 3.14;
Math.ceil(num);
// bad
var num = 3.14;
parseInt(num, 10);
```
-------------------

### 2.5 字符串

[强制] 字符串开头和结束使用单引号 '。

解释：
* 输入单引号不需要按住 shift，方便输入。
* 实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。

示例：
```javascript
var str = '我是一个字符串';
var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```
---------------------

### 2.6 对象

[强制] 对象创建时，如果一个对象的所有 属性 均可以不添加引号，则所有 属性 不得添加引号。

示例：
```javascript
var info = {
    name: 'someone',
    age: 28
};
```

[强制] 对象创建时，如果任何一个 属性 需要添加引号，则所有 属性 必须添加 '。

解释：

如果属性不符合 Identifier 和 NumberLiteral 的形式，就需要以 StringLiteral 的形式提供。

示例：
```javascript
// good

var info = {
    'name': 'someone',
    'age': 28,
    'more-info': '...'
};
// badvar info = {
    name: 'someone',
    age: 28,
    'more-info': '...'
};
```
-----------------
## 3 浏览器环境

### 3.1  DOM
#### 3.1.1  DOM 操作

[建议] 操作 DOM 时，尽量减少页面 reflow。

解释：

页面 reflow 是非常耗时的行为，非常容易导致性能瓶颈。下面一些场景会触发浏览器的reflow：
* DOM元素的添加、修改（内容）、删除。
* 应用新的样式或者修改任何影响元素布局的属性。
* Resize浏览器窗口、滚动页面。
* 读取元素的某些属性（offsetLeft、offsetTop、offsetHeight、offsetWidth、scrollTop/Left/Width/Height、clientTop/Left/Width/Height、getComputedStyle()、currentStyle(in IE)) 。

[建议] 尽量减少 DOM 操作。

解释：

DOM 操作也是非常耗时的一种操作，减少 DOM 操作有助于提高性能。举一个简单的例子，构建一个列表。我们可以用两种方式：

1. 在循环体中 createElement 并 append 到父元素中。
2. 在循环体中拼接 HTML 字符串，循环结束后写父元素的 innerHTML。
第一种方法看起来比较标准，但是每次循环都会对 DOM 进行操作，性能极低。在这里推荐使用第二种方法。
