### 标题

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
---------

### 列表

* 无序列表
在文字前面加上 - 或者 *
```
- 文本1
- 文本2
- 文本3

```

```
* 文本1
* 文本2
* 文本3
```

* 有序列表
```
1. 文本1
2. 文本2
3. 文本3
```
---------

### 插入链接

[显示文本](链接地址)
```
[显示文本](http://www.xianshiwenben.com)
```

---------

### 图片

![](图片链接地址)
```
![](http://upload-images.jianshu.io/upload_images/259-0ad0d0bfc1c608b6.jpg
```
---------

#### 引用
在引用的文字前面加上 >

```
> 一盏灯， 一片昏黄； 一简书， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。
```
最终显示的就是：
> 一盏灯， 一片昏黄； 一简书， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。

---------

### 粗体和斜体
用两个 * 包含一段文本就是粗体的语法，用一个 * 包含一段文本就是斜体的语法。

```
*一盏灯*， 一片昏黄；**一简书**， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。
```

最终显示的就是下文，其中「一盏灯」是斜体，「一简书」是粗体：


*一盏灯*， 一片昏黄；**一简书**， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。


----------

### 代码引用

需要引用代码时，如果引用的语句只有一段，不分行，可以用 ` 将语句包起来。

代码如下：
```
`<addr>` element here instead.
```

显示效果如下：

`<addr>` element here instead.

如果引用的语句为多行，可以将```置于这段代码的首行和末行。

代码如下：

\`\`\`javascript
 function fancyAlert(arg) {
    if(arg) {
         $.facebox({div:'#foo'})
     }
 }
\`\`\`

显示如下：


```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```


----------

### 表格

相关代码：

```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```


显示效果：

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

---------


### 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。

代码如下：
``` 
    * * *

    ***

    *****

    - - -

    ---------------------------------------
```

参考资料：[链接](http://www.jianshu.com/p/q81RER)

参考资料：[链接](https://www.appinn.com/markdown/)