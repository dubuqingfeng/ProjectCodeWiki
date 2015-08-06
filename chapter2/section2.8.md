本文档的目标是使HTML代码风格保持一致，容易被理解和被维护。

## HTML编码规范

---

### 缩进与换行
* 【强制】使用 4个空格做为一个缩进层级，不允许使用 2个空格 或 tab字符。

```html

    <ul>
        <li>first</li>
        <li>second</li>
    </ul>
```

---

### 命名
* 【强制】`class`必须单词全字母小写，单词间以 `-` 分隔。
* 【强制】`class`必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。

```html

    <!-- good -->
    <div class="sidebar"></div>

    <!-- bad -->
    <div class="left"></div>
```
* 【强制】`id`必须已驼峰形书写

```html

    <div id="tuoFeng"></div>
```

---

### 标签
* 【强制】标签名必须使用小写字母。

---

### 属性
* 【强制】属性名必须使用小写字母。
* 【强制】属性值必须用双引号包围。

```html

    <!-- good -->
    <script src="esl.js"></script>

    <!-- bad -->
    <script src='esl.js'></script>
    <script src=esl.js></script>
```

---

### 图片
* 【强制】禁止`img`的`src`取值为空。延迟加载的图片也要增加默认的`src`。`src`取值为空，会导致部分浏览器重新加载一次当前页面。

### 按钮
* 【强制】使用`button`元素时必须指明`type`属性值。

