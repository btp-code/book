# Web API

要讓你的 Javascript 程式和網頁能夠一起運作，就必須使用一些「應用程式界面（**A**pplication **P**rogramming **I**nterface）」了。什麼是應用程式界面呢？就是到目前為止，你的 HTML 和 Javascript 是完全分開的，假如你希望 Javascript 能夠讀取、修改 HTML 的內容，或是對於某些「事件」——像是滑鼠點擊——做出回應，那麼你就需要一些方法來結合 Javascript 和 HTML，這些方法就統稱「應用程式界面」，而因為這個界面是用在 Web 的世界的，所以稱之為 Web API。

這裡將介紹一些常用的 Web API ，更完整的列表請參考 [MDN](https://developer.mozilla.org/en-US/docs/Web/Reference/API)。

## DOM （Document Object Model）

DOM 是一種概念，簡單來說，他的目標是讓你能夠像是操作物件一樣操作頁面上的 HTML 元素。

### 取得元素

我們可以用下面幾種方式取得代表頁面上元素的「物件」。

* `document.getElementById`
* `document.getElementsTagName` (return array)
* `document.getElementByClassName` (return array)

> **Exercise:** 使用 `console.log` 印出一個頁面上的物件。

### 操作元素

一些常見的屬性：

* `Element.className`: 可以用來修改元素的 class。
* `Element.innerHTML`: 可以用來修改元素的內容。
* `Element.style`： 可以用來修改元素樣式的屬性。
* `HTMLInputElement.value`: input 元素的值。


一些常見的方法（Method）：
* `Element.getAttribute(attributeName)`: 取得元素屬性 `attributeName` 的值。
* `Element.setAttribute(attributeName, value)`: 設定元素屬性 `attributeName` 的值。
* `Element.removeAttribute(attributeName)`： 刪除元素屬性 `attributeName`。

其中 `Element` 與 `HTMLInputElement` 要換成 DOM 物件（像是用 `document.getElementById` 取得的物件）。

如：

```js
    document.getElementsByTagName('body')[0].innerHTML = "This is a test."
```

> **Exercise:** 使用 `Element.innerHTML` 顯示九九乘法表。（注意：你的 script 必須放在  body 內容的最後面，否則可能會失敗。）

> **Exercise:** 使用 `Element.setAttribute('disabled', 'disabled')` 使一個按鈕失效。

### 新增元素

你可以使用 `document.createElement(tagName)` 來創造元素，並使用 `parent.appendChild(element)` 把這個元素加到 `parent` 元素的子元素們。

例如我可以這樣創造一個標題

```js
    let body = document.getElementsByTagName('body')[0];
    let h1 = document.createElement('h1');
    h1.innerHTML = "this is a test";
    body.appendChild(h1);
```

或是使用 `document.createTextNode(text);` 像這樣

```js
    let body = document.getElementsByTagName('body')[0];
    let h1 = document.createElement('h1');
    let textNode = document.createTextNode("this is a test");
    h1.appendChild(textNode);
    body.appendChild(h1);
```

### 刪除元素

刪除元素比較麻煩，必須像這樣

```js
    element.parentElement.removeChild(element);
```

如果你不介意有些較舊的瀏覽器不支援的話，也可以直接呼叫元素的`.remove()` 方法。

## 事件處理（Event Processing）

在 Web 的世界，事件是一個抽象的概念，當一些事情發生時，像是使用者移動了滑鼠、敲下了鍵盤，就會有一個「事件」產生。

我們可以用某種方式增加一個「Listener」去「聽」某種事件，並指定一個「handler」處理事件，這些動作我們稱之為「註冊（Register）」。也就是說，我們可以指定一個函式在某種事件發生時自動被執行。

事件發生的來源稱之為「Event Target」，例如一個按鈕點擊（click）事件的 Event Target 就是那個按鈕本身。

### 註冊事件處理函式

而註冊一個 Event Listener 的方式有幾種：

#### 在 HTML 裡指定

可以透過設定元素的 Event Handler 屬性來指定事件發生時要做什麼。

常見的 Event Handler 屬性有

* onclick （滑鼠按下）
* ondbclick （滑鼠按兩下）
* onchange （input 的值被改變）
* onselect
* ...

使用方式如下：

```html
<div onclick='handler()'></div>
```

單引號裡就是事件發生時要執行的程式碼。

[這裡](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)有比較完整的參考。

#### 在 Javascript 中使用 onXXXX 指定

可以透過更改 DOM 物件的 onXXXX 屬性指定事件發生時要執行的函式。而這個函式在被執行時，會被傳入一個參數，這個參數就是代表著發生事件的物件。這個物件可能會包含一些跟事件有關的資訊，例如 click 的事件會有滑鼠的座標。

常見的屬性有

* onclick
* oninput
* onkeypress
* ...

用法如下：

```js
document.getElementById('btn').onclick = handler;

function handler(event){
    console.log('clicked!! event:', event);
};
```

更完整的參考請看 [MDN](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers)。

下面將介紹一些常見的事件。

#### 在 Javascript 中使用 addEventListener 指定

可以呼叫 DOM 物件的 addEventListener 方法來指定當事件發生時要呼叫的函式。

addEventListener 的第一個參數是事件的種類，第二個則是處理事件的函式。與上一個方法一樣， event 物件會被當作參數傳給處理事件的函式。

常見的事件種類有：

* click
* dbclick
* change
* ...

```
document.getElementById('btn').addEventListener('click', handler);

function handler(event){
    console.log('clicked!! event:', event);
};
```

在[這裡](https://btp-code.github.io/btp-code/web-api/examples/event.html)有以上三種用法的範例。
在[這裡](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)有 addEventListener 更完整的用法。 
事件的種類在[這裡](https://developer.mozilla.org/en-US/docs/Web/Events)有更完整的參考。


> **Exercise:** 建立兩個 type 為 number 的 input，並在旁邊即時顯示兩個 input 數字相乘的結果。（提示：使用 `onchange` 或 `change`。）


### 常見的用法

#### window.onload

用法如下：

```js
    window.onload = function(){
        // do something here
    }
```

有時候，我們會希望再依開始的時候就動態新增一些元素到頁面上，然而在頁面還沒被完全載入之前，因為 DOM 還沒完全建立，我們是無法操作 DOM 的。因此，我們會希望知道網頁什麼時候被完全載入，這時候 `window.onload` 就很好用了。

> **Exercise:** 利用 `window.onload` 在頁面載入後用 js 建立一個長度為 100 、每一項的內容從 100 到 1 的列表。

> **Exercise:** 對於上一題做出來的列表中的每一項，按一下即刪除。（event object 的 traget 屬性可能很有用）


## 雜七雜八

### 計時器

可以使用 `window.setInterval(func, delay)` 讓 `func` 每隔 `delay` 毫秒就被執行一次。或是用 `window.setTimeout(func, delay)` 讓 `func` 在 `delay` 毫秒後被執行。

這兩個函式會回傳一個 id ，可以透過呼叫 `window.clearInterval(id)` 或是 `window.clearTimeout(id)` 來結束計時器。

例如：

```js
    let id = window.setInterval(function(){ console.log('!'); }, 1000);
```

再這樣結束

```js
    window.crearTimeout(id);
```


> **Exercise:** 在頁面上顯示現在的時間。
