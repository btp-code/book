# 畫布

在 HTML 裡有一個特別的元素，可以讓你在上面用 js 畫圖。

這裡是一份範例程式碼。

```html
<canvas></canvas>
<script>
    var canvas = document.getElementsByTagName("canvas")[0];
    var ctx = canvas.getContext("2d");
    ctx.fillStyle = "gray";
    ctx.fillRect(5, 5, 100, 100);
</script>
```

因為 [MDN 上的教學](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)已經寫得很好了，以下就只簡單節錄一些重點。


## Canvas 元素

只有 `width` 和 `height` 這兩個特別的屬性，如果不指定，預設是寬度 350px ，高度 150px。

## 取得渲染環境

要在 canvas 上畫東西，必須先取得「Contex」（繁體中文版教學把 Contex 翻譯成渲染環境，中國地區則習慣稱之為「上下文」，不過我們還是就叫他 Contex 好了。）

```js
    let ctx = canvas.getContext('2d');
```

## 繪製矩形

* `fillRect(x, y, width, height)`：填滿一個矩形。
* `strokeRect(x, y, width, height)`：畫出一個矩形的框。
* `clearRect(x, y, width, height)`：清空一個矩形的範圍（變成透明）。

## 繪製路徑

以下是繪製路徑的步驟：

* `ctx.beginPath()`：開始一個新的路徑。
* `ctx.XXX`：使用一些路徑的函式。
* `ctx.closePath()`：可以用它來閉合路徑。
* `ctx.stroke()`：按照路徑畫線
* `ctx.fill()`：填滿路徑包圍的區域。如果路徑沒有閉合，那麼它會按照閉合的樣子填滿。


## 路徑函式

* `ctx.moveTo(x, y)`：移動你的畫筆。通常在 `ctx.beginPath` 後都會先使用這個函式。
* `lineTo(x, y)`
* `arc(x, y, radius, startAngle, endAngle, anticlockwise)`
* `arcTo(x1, y1, x2, y2, radius)`

## 顏色

* `fillStyle = color`
* `strokeStyle = color`

color 就是代表 CSS 的顏色的字串，如：`#FFFFFF`。

## 線條樣式

* `lineWidth = value`
* `lineCap = butt | round | square`
* `lineJoin = round | bevel | miter`

## 繪製文字

* fillText(text, x, y [, maxWidth])
* strokeText(text, x, y [, maxWidth])

可以像這樣改變文字的大小與字體：

```js
    ctx.font = "30px mono";
```

## 動畫

* `window.requestAnimationFrame(draw);`

[這裡](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations)
有一個很好的範例。
