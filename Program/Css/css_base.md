# CSS 学习

## CSS 基础

### 注释

```css
/* 这是一个注释 */
```

### 导入样式表的方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Weiguang19</title>

    <!-- 1. 导入外部样式表 -->
    <link rel="stylesheet" href="mystyle.css" type="text/css">

    <!-- 2. 内联样式(不推荐）) -->
    <style>
        h1{
            color: blueviolet;
        }
    </style>
</head>

<body>
    <h1>hello world</h1>

    <!-- 3. 嵌入式样式 -->
    <p style="font-size: 15px;">this is a paragraph.</p>

</body>
</html>
```

### 在样式表中导入其他样式表

> 优先级：html内部通过@import导入的样式表 > css自身样式 > css内导入的外部样式表

```css
/* mystyle.css*/
/* 在样式表中引入其他样式表 */
@import url("common/menus.css");
```

#### 在HTML中也可以这样使用(不推荐)

```html
<!--index.html-->
	<style>
        @import url("common/menus.css");
    </style>
```

### 选学：使用less辅助css编写

### 标签选择器

```css
    <style>
        /* 通配符选择 */
        * {
            color: cadetblue;
        }
        /* 标签选择器 */
        h1,
        h2 {
            color: chartreuse;
        }
        /* 可以这样写 */
        h2,
        h3 {
            color: coral;
        }
        /* 当属性重复时，效果会叠加（顾名思义：层叠样式表） */
    </style>
```



类选择器

```html
<head> 
	<style>
        .success {
            color: green;
        }
        .error {
            color: red;
        }
    </style>
</head>
<body>
    <div class="success">success</div>
    <div class="error">error</div>
</body>
```

### ID选择器

```html
<head>
    <style>
        #success {
            color: green;
            font-size: 24pt;
        }
        #error {
            color: red;
            font-size: 24pt;
        }
    </style>

</head>
<body>
    <div id="success">success</div>
    <div id="error">error</div>
</body>
```



### 多重类样式声明(id选择器不适用)

```html
<head>
    <style>
        .success {
            color: green;
            font-size: 24pt;
            border: solid 1px green;
        }
        .error {
            color: red;
            font-size: 24pt;
            border: solid 1px red;
        }
        .mb {
            margin-bottom: 10px;
        }
        .bg_blue{
            background: blue;
        }
    </style>

</head>
<body>
    <!-- 可以引用多重类样式 -->
    <div class="success mb">success</div>
    <div class="error mb bg_blue">error</div>
</body>
```

### 结构选择器

#### 后代选择器

```css
<style>
        /* 后代选择器， 会影响无限后代 */
        main article h2 {
            color: blueviolet;
        }
</style>
```

#### 子元素选择器

```html
<style>
        /* 子元素选择器, 只影响有限同级子元素*/
        main article>h2 {
            color: chartreuse;
</style>
```

#### 兄弟元素选择器

```html
<style>
        /* 兄弟元素选择器，在其之后的同级元素会受到影响（案例中所有同级h2受影响） */
        article h1~h2 {
            color: chartreuse;
        }
</style>
```

#### 紧密兄弟选择器

```html
<style>
        /* 紧密兄弟元素选择器，在其之后的同级第一个元素会受到影响（案例中仅同级的第一个紧随其后的h2受影响） */
        article h1+h2 {
            color: chartreuse;
        }
</style>
```

