# 更多的元素

在知道以上的概念後，剩下的就只是熟悉許多html的元素了。這裡有一張[完整的表](https://developer.mozilla.org/zh-TW/docs/Web/HTML/Element)。

不過以下還是大概介紹一些常見的標籤

## 標題

```html
<h1>標題，等級1</h1>
<h2>標題，等級2</h2>
<h3>標題，等級3</h3>
<h4>標題，等級4</h4>
<h5>標題，等級5</h5>
<h6>標題，等級6</h6>
```

## 超連結

```html
<a href='https://google.com'>戳我</a>
```

## 一段文字

```html
<span>一小段字</span>
```

這個要和之後的 css 搭配才會比較有用。

## 一段段落

```html
<p>這是一段話</p>
```

## 區塊

```html
<div></div>
```

或

```html
<section></section>
```

## 圖片

```html
<img src="https://www.mozilla.org/media/img/styleguide/identity/firefox/guidelines-logo.7ea045a4e288.png">
```

src 屬性指定了圖片的來源（網址），別忘了引號`"`。

## 表格

```html
<table>
  <thead>
    <tr>
      <th>欄位名稱1</th>
      <th>欄位名稱2</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>表格的尾巴</td>
      <td>表格的尾巴</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>CCCC</td>
      <td>CCCC</td>
    </tr>
  </tbody>
</table>
```

## 清單

列點
```html
<ul>
  <li>項目1</li>
  <li>項目2</li>
  <li>項目3</li>
  <li>項目4
    <ul>
      <li>子項目 4 - 1</li>
      <li>子項目 4 - 2</li>
    </ul>
  </li>
</ul>
```

有序
```html
<ol>
  <li>項目1</li>
  <li>項目2</li>
  <li>項目3</li>
  <li>項目4
    <ol>
      <li>子項目 4 - 1</li>
      <li>子項目 4 - 2</li>
    </ol>
  </li>
</ol>
```

## 換行

```
<br>
```

## 輸入

```html
<input type='text' value='100'>
<br>

<label><input type='radio' value='100' name='test'>100</label>
<label><input type='radio' value='200' name='test' checked>200</label>
<br>

<label><input type='checkbox' value='100'>100</label>
<label><input type='checkbox' value='200' checked>200</label>
<br>

<input type="button" value="戳">
```

這些要跟 Javascript 一起用才比較有用。


## 選項

```html
<select>
  <option>選項 1</option>
  <option>選項 2</option>
  <option>選項 3</option>
  <option>選項 4</option>
</select>
```  

這也要跟 Javascript 一起用才比較有用。
