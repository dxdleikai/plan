# CSS书写规范


## 1.代码风格


### 1.1 结构

#### 1.1.1 缩进

[强制] 使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。


[强制] switch 下的 case 和 default 必须增加一个缩进层级。

示例：

```
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

```
var a = !arr.length;
a++;
a = b + c;
```


[强制] 用作代码块起始的左花括号 { 前必须有一个空格。

示例：

```
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

```
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

```
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

```
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

```
// goodcallFunc(a, b);
// badcallFunc(a , b) ;
```


[强制] 在函数调用、函数声明、括号表达式、属性访问、if / for / while / switch / catch 等语句中，() 和 [] 内紧贴括号部分不允许有空格。

示例：

```
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

```
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

```
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

```
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

```
// 仅为按逻辑换行的示例，不代表setStyle的最优实现function setStyle(element, property, value) {
    if (element == null) {
        return;
    }

    element.style[property] = value;
}
```


[建议] 在语句的行长度超过 120 时，根据逻辑条件合理缩进。

示例：
```
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

```
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
```
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
```
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

```
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

```
var loadingModules = {};
```


[强制] 常量 使用 全部字母大写，单词间下划线分隔 的命名方式。

示例：

```
var HTML_ENTITY = {};
```


[强制] 函数 使用 Camel命名法。

示例：

```
function stringFormat(source) {
}
```


[强制] 函数的 参数 使用 Camel命名法。

示例:

```
function hear(theBells) {
}
```


[强制] 类 使用 Pascal命名法。

示例：

```
function TextNode(options) {
}
```


[强制] 类的 方法 / 属性 使用 Camel命名法。

示例：

```
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

```
function XMLParser() {
}
function insertHTML(element, html) {
}
var httpRequest = new HTTPRequest();
```


[强制] 类名 使用 名词。

示例：

```
function Engine(options) {
}
```


[建议] 函数名 使用 动宾短语。

示例：

```
function getStyle(element) {
}
```


[建议] boolean 类型的变量使用 is 或 has 开头。

示例：

```
var isReady = false;var hasMoreCommands = false;
```


[建议] Promise对象 用 动宾短语的进行时 表达。

示例：

```
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

文件

namespace

类

函数或方法

类属性

事件

全局变量

常量

AMD 模块

[强制] 文档注释前必须空一行。

[建议] 自文档化的文档说明 what，而不是 how。


--------------

#### 1.3.4 类型定义

[强制] 类型定义都是以{开始, 以}结束。

解释：

常用类型如：{string}, {number}, {boolean}, {Object}, {Function}, {RegExp}, {Array}, {Date}。

类型不仅局限于内置的类型，也可以是自定义的类型。比如定义了一个类 Developer，就可以使用它来定义一个参数和返回值的类型。


[强制] 对于基本类型 {string}, {number}, {boolean}，首字母必须小写。

| 类型定义            | 语法示例          |                |
| :------------------: | :----------------: | :--------------: |

--------------

## 2 通用


### 2.1 选择器

[强制] 如无必要，不得为 id、class 选择器添加类型选择器进行限定。

解释：

在性能和维护性上，都有一定的影响。

示例：

```
/* good */
#error,
.danger-message {
    font-color: #c00;
}
/* bad */
dialog#error,
p.danger-message {
    font-color: #c00;
}
```


[建议] 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。

示例：

```
/* good */
#username input {
}
.comment .avatar {
}
/* bad */
.page .header .login #username input {
}
.comment div * {
}
```

-------------------


### 2.2 属性书写顺序

[建议] 同一 rule set 下的属性在书写时，应按功能进行分组，并以 Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果） 的顺序书写，以提高代码的可读性。

解释：

Formatting Model 相关属性包括：position / top / right / bottom / left / float / display / overflow 等

Box Model 相关属性包括：border / margin / padding / width / height 等

Typographic 相关属性包括：font / line-height / text-align / word-wrap 等

Visual 相关属性包括：background / color / transition / list-style 等

另外，如果包含 content 属性，应放在最前面。

示例：

```
.sidebar {
    /* formatting model: positioning schemes / offsets / z-indexes / display / ...  */
    position: absolute;
    top: 50px;
    left: 0;
    overflow-x: hidden;

    /* box model: sizes / margins / paddings / borders / ...  */
    width: 200px;
    padding: 5px;
    border: 1px solid #ddd;

    /* typographic: font / aligns / text styles / ... */
    font-size: 14px;
    line-height: 20px;

    /* visual: colors / shadows / gradients / ... */
    background: #f5f5f5;
    color: #333;
    -webkit-transition: color 1s;
       -moz-transition: color 1s;
            transition: color 1s;
}
```

----------------

## 3 值与单位


### 3.1数值

[强制] 当数值为 0 - 1 之间的小数时，省略整数部分的 0。

示例：

```
/* good */
panel {
    opacity: .8
}
/* bad */
panel {
    opacity: 0.8
}

```

---------------------

### 3.2 url()

[强制] url() 函数中的路径不加引号。

示例：

```
body {
    background: url(bg.png);
}
```

--------------------

### 3.3 长度

[强制] 长度为 0 时须省略单位。 (也只有长度单位可省)

示例：

```
/* good */
body {
    padding: 0 5px;
}
/* bad */
body {
    padding: 0px 5px;
}
```

------------------

## 4 兼容性


### 4.1 属性前缀

[强制] 带私有前缀的属性由长到短排列，按冒号位置对齐。

解释：

标准属性放在最后，按冒号对齐方便阅读，也便于在编辑器内进行多行编辑。

示例：

```
.box {
    -webkit-box-sizing: border-box;
       -moz-box-sizing: border-box;
            box-sizing: border-box;
}
```

------------------