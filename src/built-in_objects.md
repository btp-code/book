# 內建物件

前面介紹了「物件」，不過其實主要是希望能讓大家在對「物件」有一些糢糊的概念後，更能理解這章的一些內容。也就是說，主要的目標是讓大家理解這一節，前一節的內容懂不懂可能不是那麼重要。

## 陣列


問題就在於，如果我們想要儲存一個數列，像是 `1, 2, 3, 4, 5`，我們要怎麼存？

首先想到的可能是這樣：

```js
var v1 = 1;
var v2 = 2;
var v3 = 3;
var v4 = 4;
var v5 = 5;
```

但是，這就有兩個問題了，要是我事前不知道總共有幾個數字怎麼辦？另一個是，要是我想要把他們加起來怎麼辦？

事實上「陣列」就是拿來解決這個問題的。我們可以把陣列想成是「可以按照順序裝很多東西的容器」。

### 語法

如果把陣列想成是「可以按照順序裝很多東西的容器」，那首先我們可以宣告一個「空空的容器」，語法是這樣的：

```js
var a = [];
```

也可以在宣告時就先給他裝一些東西

```js
var a = [1, 2, 3, 4, 5];
```

前面說到「按照順序」，所以我們可以看看第 3 個東西是什麼，像這樣

```js
a[3];
```

喔喔，竟然是 4 也，這是因為編號是從零開始，所以

```js
a[0];
```

會是 1 喔。

我們也可以把東西放到第 3 個位置：

```js
a[3] = 100;
```

這時候 `a` 裡面裝的東西就變成 `[1, 2, 3, 100, 5]` 了。

前面還說過「很多東西」，其實陣列不只是可以放數字，他可以放任何東西，像是

```js
a[2] = 'apple';
```

那麼 `a` 就變成 `[1, 2, 'apple', 100, 5]` 了。

我們還可以把陣列裝到陣列裡，像這樣

```js
a[0] = [-1, -2, -3];
```

那麼 `a` 就變成 `[[-1, -2, -3], 2, 'apple', 100, 5]` 了。

這樣做有一個有趣的事情會發生，那就是 `a[0]` 是一個 `[-1, -2, -3]` 的陣列，所以如果說 `a[0][0]` 的意思就是對 `[-1, -2, -3]` 找第 0 個東西，就是 `-1`。如此一來我們好像就有了兩個「維度」，變成二維的陣列了。

我們還說「陣列」是一個物件，所以他也有一些自己的「屬性」和「方法」囉！首先最重要的是 `length` 屬性，他代表的是陣列的長度，有了它，我們就可以實現算出陣列裡數字的和了，像這樣

```js
var a = [1, 2, 3, 4, 5];
var sum = 0;
for(var i = 0; i < a.length; ++i){
    sum += a[i];
}
```

此外，還有一些好用的方法（用法是把 `array` 換成陣列的名字）

* `array.push(item)`： 把東西放到陣列的尾部（增加一個元素、陣列長度加 1）。
* `array.pop(item)`： 回傳陣列的尾部的東西，並從陣列刪掉他（刪除一個元素、陣列長度減 1）。
* `array.splice(position, length)`：回傳陣列從 `position` （一個整數）開始的幾個東西，要回傳幾個由 `length` 指定，並且把那些東西從陣列裡刪除。
* `array.indexOf(item)`：找到 `item` 在陣列裡的位置，也就是最小的 `i` 使得 `array[i] === item`。如果找不到會回傳 -1。
* `array.sort()`：把 `array` 裡的東西從小排到大。
* [更多...](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)


## 字串

字串是另一個常用的物件，他其實跟陣列有幾分像，首先對於字串 `str`

```js
var str = 'abcdefg';
```

它也可以像這樣

```js
str[0];
```

是 'a'，不過它沒有辦法

```js
str[0] = 'A';
```

這樣 str 還是 `"abcdefg"`。

並且它也有 `length` 屬性，至於他的方法，就直接看看 [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) 吧。


## 日期物件（Date Object）

首先是先建立一個 Date 物件

```js
var date = new Date();
```

* 年：date.getFullYear()
* 月：date.getMonth()
* 日：date.getDate()
* 星期：date.getDay()
* 時：date.getHours()
* 分：date.getMinutes() 
* 秒：date.getSeconds()
* [More...](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

## Math 物件

與其說 Math 是一個物件，倒不如說他是一個名稱空間，Javascript 中所有數學的函式都裝在裡面了，例如：

* `Math.random()`：隨機回傳一個在 [0, 1) 的小數。
* `Math.floor(float)`：把小數 `float` 無條件捨去變成整數。
* `Math.rounf(float)`：把小數 `float` 四捨五入。
* `Math.max(x1, x2, ...)`：回傳參數中最大的值。
* `Math.min(x1, x2, ...)`：回傳參數中最小的值。
* `Math.pow(x, y)`：回傳 x 的 y 次方。
* `Math.sqrt(x)`：回傳 x 的平方根。
* `Math.log(x)`：回傳 ln x （自然對數）。
* `Math.log10(x)`：回傳以十為底的 log x。
* `Math.PI`：常數 $\pi$。
* [More...](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
