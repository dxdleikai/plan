# CSS书写规范

-----------------

## 1.代码风格


### 1.1 缩进

[强制] 使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。

----------------

### 1.2  空格

[强制] 选择器 与 { 之间必须包含空格。

示例：

```
.selector {
}
```

[强制] 属性名 与之后的 : 之间不允许包含空格， : 与 属性值 之间必须包含空格。

示例：

```
margin: 0;
```

[强制] 列表型属性值 书写在单行时，, 后必须跟一个空格。

示例：

```
font-family: Arial, sans-serif;
```

----------------

### 1.3 行长度

[强制] 每行不得超过 120 个字符，除非单行不可分割。

解释：

常见不可分割的场景为URL超长。

[建议] 对于超长的样式，在样式值的 空格 处或 , 后换行，建议按逻辑分组。

示例：

```
/* 不同属性值按逻辑分组 */
background:
    transparent url(aVeryVeryVeryLongUrlIsPlacedHere)
    no-repeat 0 0;
/* 可重复多次的属性，每次重复一行 */background-image:
    url(aVeryVeryVeryLongUrlIsPlacedHere)
    url(anotherVeryVeryVeryLongUrlIsPlacedHere);
/* 类似函数的属性值可以根据函数调用的缩进进行 */background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    color-stop(0.04, rgb(88,94,124)),
    color-stop(0.52, rgb(115,123,162))
);
```

-----------------

### 1.4 选择器

[强制] 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行。

示例：

```
/* good */
.post,
.page,
.comment {
    line-height: 1.5;
}
/* bad */
.post, .page, .comment {
    line-height: 1.5;
}

```

[强制] >、+、~ 选择器的两边各保留一个空格。

示例：

```
/* good */
main > nav {
    padding: 10px;
}
label + input {
    margin-left: 5px;
}
input:checked ~ button {
    background-color: #69C;
}
/* bad */
main>nav {
    padding: 10px;
}
label+input {
    margin-left: 5px;
}
input:checked~button {
    background-color: #69C;
}
```

-----------------

### 1.5 属性

[强制] 属性定义必须另起一行。

示例：

```
/* good */
.selector {
    margin: 0;
    padding: 0;
}
/* bad */
.selector { margin: 0; padding: 0; }
````

[强制] 属性定义后必须以分号结尾。

示例：
```
/* good */
.selector {
    margin: 0;
}
/* bad */
.selector {
    margin: 0
}
```

-------------


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