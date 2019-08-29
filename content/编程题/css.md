# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.用 H5+CSS3 解决下导航栏最后一项掉下来的问题</summary></b>

答案：box-sizing: border-box;

</details>

<b><details><summary>2.请用 CSS 实现：一个矩形内容，有投影，有圆角，hover 状态慢慢变透明</summary></b>

答案：

```html
<div class="test"></div>
```

```css
.test {
  width: 200px;
  height: 100px;
  border-radius: 10px;
  box-shadow: 10px 10px 5px #888888;
  background-color: green;
  transition: 0.7s;
}
.test:hover {
  opacity: 0;
}
```

</details>

<b><details><summary>3.描述下 CSS3 里实现元素动画的方法</summary></b>

答案：

1. 创建动画：@keyframes 规则

方式一：from{属性：值;} to{属性：值;}

```css
@keyframes myflash {
  from {
    width: 200px;
    height: 200px;
  }
  to {
    position: relative;
    left: 50px;
    transform: rotate(360deg);
  }
}
```

方式二：0%{属性：值;} 100%{属性：值;}
0% 是动画的开始，100% 是动画的完成。可以在二者之间加入 25%，50%等

```css
@keyframes myflash {
  0% {
    background: red;
  }
  50% {
    background: yellow;
  }
  75% {
    background: green;
  }
  100% {
    background: blue;
  }
}
```

2. 将动画绑定到选择器

在样式中，设置动画属性 animation，自定义动画名称和时长。

animation：动画名 时长；

此时就可以完成一个简单的动画了，要进行更多设置还需要其他属性。

```css
#first {
  animation: myflash 10s;
  animation-delay: 2s;
  animation-iteration-count: 2;
  animation-timing-function: ease-in;
}
```

解析：[参考](https://jingyan.baidu.com/article/363872ec01c1146e4ba16fa5.html)

</details>

<b><details><summary>4.你怎么来实现页面设计图，你认为前端应该如何高质量完成工作? 一个满屏 品 字布局 如何设计?</summary></b>

答案：

</details>

<b><details><summary>5.如何用css实现瀑布流布局</summary></b>

答案：
利用column-count和break-inside这两个CSS3属性即可，复制如下代码即可察看效果
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <style>
        body {
            margin: 0;
        }
        .waterfall-container {
            /*分几列*/
            column-count: 2;
            width: 100%;
            /* 列间距 */
            column-gap: 10px;
        }

        .waterfall-item {
            break-inside: avoid;
            width: 100%;
            height: 100px;
            margin-bottom: 10px;
            background: #ddd;
            column-gap: 0;
            text-align: center;
            color: #fff;
            font-size: 40px;
        }
    </style>
</head>
<body>
    <div class="waterfall-container">
        <div class="waterfall-item" style="height: 100px">1</div>
        <div class="waterfall-item" style="height: 300px">2</div>
        <div class="waterfall-item" style="height: 400px">3</div>
        <div class="waterfall-item" style="height: 100px">4</div>
        <div class="waterfall-item" style="height: 300px">5</div>
        <div class="waterfall-item" style="height: 600px">6</div>
        <div class="waterfall-item" style="height: 400px">7</div>
        <div class="waterfall-item" style="height: 300px">8</div>
        <div class="waterfall-item" style="height: 700px">9</div>
        <div class="waterfall-item" style="height: 100px">10</div>
    </div>
</body>
</html>
```

</details>

<b><details><summary>6.已知父级盒子的宽高，子级img宽高未知，想让img铺满父级盒子且图片不能变形</summary></b>

答案：需要用到`css`的`object-fit`属性

```css
div {
    width: 200px;
    height: 200px;
}
img {
    object-fit: cover;
    width: 100%;
    height: 100%;
}
```

解析：[MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit)

</details>

<b><details><summary></summary></b>

答案：

</details>