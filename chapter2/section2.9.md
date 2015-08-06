本文档的目标是使CSS代码风格保持一致，容易被理解和被维护

## CSS编码规范

---

### 缩进
* 【强制】使用4个空格做为一个缩进层级，不允许使用2个空格或tab字符。
* 【强制】选择器与`{`之间不允许包含空格。
* 【强制】属性名与之后的`:`之间不允许包含空格，`:`与属性值之间必须包含空格。

```css

    margin: 0;
```
* 列表型属性值书写在单行时`,`后必须跟一个空格。

```css

    font-family: Arial, sans-serif;
    color: rgba(0, 0, 0, .5);
```
* 每行不得超过120个字符，除非单行不可分割。对于超长的样式，在样式值的空格处或`,`后换行，建议按逻辑分组。

```css

    /* 不同属性值按逻辑分组 */
    background:
        transparent url(aVeryVeryVeryLongUrlIsPlacedHere)
        no-repeat 0 0;

    /* 可重复多次的属性，每次重复一行 */
    background-image:
        url(aVeryVeryVeryLongUrlIsPlacedHere)
        url(anotherVeryVeryVeryLongUrlIsPlacedHere);

    /* 类似函数的属性值可以根据函数调用的缩进进行 */
    background-image: -webkit-gradient(
        linear,
        left bottom,
        left top,
        color-stop(0.04, rgb(88,94,124)),
        color-stop(0.52, rgb(115,123,162))
    );
```

---

### 选择器
* 【强制】当一个rule包含多个selector时，每个选择器声明必须独占一行。

```css

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
* 【强制】>、+、~ 选择器的两边各保留一个空格。

```css

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
* 【强制】属性选择器中的值必须用双引号包围。

```css

    /* good */
    article[character="juliet"] {
        voice-family: "Vivien Leigh", victoria, female
    }

    /* bad */
    article[character='juliet'] {
        voice-family: "Vivien Leigh", victoria, female
    }
```
* 【强制】文本内容必须用双引号包围。
 
```css

    /* good */
    article[character="juliet"] {
        voice-family: "Vivien Leigh", victoria, female
    }

    /* bad */
    article[character='juliet'] {
        voice-family: "Vivien Leigh", victoria, female
    }

```
---

### 属性
* 【强制】属性定义必须另起一行。
```css
    /* bad */
    .selector {
        margin: 0;
        padding: 0;
    }

    /* bad */
    .selector { margin: 0; padding: 0; }
```
* 【强制】属性定义后必须以分号结尾。
* 【强制】如无必要，不得为`id、class`选择器添加类型选择器进行限定。
```css

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
* 【建议】选择器的嵌套层级应不大于3级，位置靠后的限定条件应尽可能精确。
```css

    /* good */
    #username input {}
    .comment .avatar {}

    /* bad */
    .page .header .login #username input {}
    .comment div * {}
```

### 值与单位
* 【建议】长度为0时须省略单位。 (也只有长度单位可省)
```css

    /* good */
    body {
        padding: 0 5px;
    }

    /* bad */
    body {
        padding: 0px 5px;
    }
```
* url() 函数中的路径不加引号。
```css

    body {
        background: url(bg.png);
    }
```
* RGB颜色值必须使用十六进制记号形式 #rrggbb。不允许使用 rgb()。
```css

    /* good */
    .success {
        box-shadow: 0 0 2px rgba(0, 128, 0, .3);
        border-color: #008000;
    }

    /* bad */
    .success {
        box-shadow: 0 0 2px rgba(0,128,0,.3);
        border-color: rgb(0, 128, 0);
    }
```
* 颜色值不允许使用命名色值
```css

    /* good */
    .success {
        color: #90ee90;
    }

    /* bad */
    .success {
        color: lightgreen;
    }
```
* 需要在Windows平台显示的中文内容，其字号应不小于12px。
    - 由于Windows的字体渲染机制，小于12px的文字显示效果极差、难以辨认。
* font-family属性中的字体族名称应使用字体的英文Family Name，
其中如有空格，须放置在引号中。
```css

    h1 {
        font-family: "Microsoft YaHei";
    }
```

* 使用`transition`时应指定`transition-property`。

```css

    /* good */
    .box {
        transition: color 1s, border-color 1s;
    }

    /* bad */
    .box {
        transition: all 1s; // 效率有问题
    }

```
### 响应式
* Media Query不得单独编排，必须与相关的规则一起定义。

```css

    /* Good */
    /* header styles */
    @media (...) {
        /* header styles */
    }

    /* main styles */
    @media (...) {
        /* main styles */
    }

    /* footer styles */
    @media (...) {
        /* footer styles */
    }


    /* Bad */
    /* header styles */
    /* main styles */
    /* footer styles */

    @media (...) {
        /* header styles */
        /* main styles */
        /* footer styles */
    }
```


