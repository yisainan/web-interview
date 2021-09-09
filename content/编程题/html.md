# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.请写出一张图片的 HTML 代码，已知道图片地址为"images/abc.jpg",宽 100px，高 50px</summary></b>

参考答案：

```html
<img src="images/abc.jpg"  alt="" width="100" height="50"/>
```

</details>

<b><details><summary>2.canvas绘制五角星</summary></b>

参考答案：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <title>canvas绘制五角星 </title>
  <script type="text/javascript" >
    window.onload = function () {
      var canvas = document.getElementById("canvas");
      if (canvas) {
        var context = canvas.getContext("2d");
        drawStar(context, 50, 100, 100);
      } else {
        document.writeln("浏览器不支持canvas组件");
      }
    }
    function drawStar(context, r, x, y) {
      context.lineWidth = 5;
      context.beginPath();
      var dit = Math.PI * 4 / 5;
      var sin = Math.sin(0) * r + y;
      var cos = Math.cos(0) * r + x;
      console.log(0+":"+0);
      context.moveTo(cos, sin);
      for (var i = 0; i < 5; i++) {
        var tempDit = dit * i;
        sin = Math.sin(tempDit) * r + y;
        cos = Math.cos(tempDit) * r + x;
        context.lineTo(cos, sin);
        console.log(sin+":"+sin+":"+tempDit);
      }
      context.closePath();
      context.strokeStyle = "red";
      context.fillStyle = "#ffc107";
      context.fill();
    }
  </script>
</head>
<body>
<canvas id="canvas" ></canvas>
</body>
</html>
```

</details>