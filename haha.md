---1
請問彩虹的顏色是什麼???



---2
彩虹的顏色是由於太陽光在雨滴中經過折射、反射及分散而形成的，通常按照光譜順序排列，可以記住為「紅橙黃綠藍靛紫」（Red, Orange, Yellow, Green, Blue, Indigo, Violet），每種顏色代表著不同波長的光。在彩虹中，紅色位於最外圈，因為它有最長的波長，而紫色位於最內圈，因為它有最短的波長。
--- end ---


---1
請用一段js code撰寫出彩虹的形狀包含顏色



---2
<br>在網頁上使用 HTML 和 JavaScript 繪製彩虹的形狀，可以使用 HTML5 的 `<canvas>` 元素來實現。以下是一段基本的 JavaScript 代碼示例，它將在 `<canvas>` 上繪製一個包含七種顏色的半圓形彩虹：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Canvas Rainbow</title>
</head>
<body>

<canvas id="rainbowCanvas" width="400" height="200"></canvas>

<script>
function drawRainbow() {
    var canvas = document.getElementById('rainbowCanvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');
        var radius = 100;
        var rainbowColors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'];

        for (var i = 0; i < rainbowColors.length; i++) {
            ctx.beginPath();
            ctx.arc(200, 200, radius, Math.PI, 2 * Math.PI);
            ctx.strokeStyle = rainbowColors[i];
            ctx.lineWidth = 10;
            ctx.stroke();
            radius -= 10; // Decrease the radius for the next color
        }
    }
}

drawRainbow();
</script>

</body>
</html>
```

這段代碼會創建一個名為 `rainbowCanvas` 的畫布元素，然後使用 JavaScript 中的 `getContext` 和 `arc` 函數來繪製七個半圓弧，每個都有不同的顏色。顏色按照紅橙黃綠藍靛紫的順序排列，並且每畫一次弧形時都將半徑減少10像素，從而創建了彩虹的效果。

只需將這段代碼放入 HTML 文件中並在支持 HTML5 的瀏覽器中打開它，就能看到畫布上出現了一個彩虹。注意：這裡我們假設畫布寬度至少是400像素，高度至少是200像素，以便有足夠空間顯示整個彩虹。
<br>--- end ---



