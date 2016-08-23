l# 條件判斷
JavaScript最常使用在網頁上，假設要寫一個行事曆網站：如果今天是上班日，則顯示工作運勢，如果今天是假日則推薦遊玩景點。
現在介紹if判斷式：
```js
if (判斷式){
 程式碼
}else if(第二個判斷式){
 第二段程式碼

}else if(第三個判斷式){
 第三段程式碼
}else{
 第四段程式碼
}
```
下面是一個範例：
```js
var date = new Date();
var day = date.getDay();
if (day == 1){
console.log("Today is Monday");
}else if (day == 2){
console.log("Today is Tuesday");
}else if (day == 3){
console.log("Today is Wednesday");
}else{
console.log("I don't know yet");
}
```
[^1] [^2]
``` if (){    }``` 如果```()```內為真(true)則會執行```{}```裡面的程式。以上的範例中，如果今天是星期一就會印出```"Today is Monday"```
##布林運算(Boolean operator)
在剛剛的條件中，應該有人會感到困惑，如果為真到底是什麼意思。
首先跟大家介紹Boolean這個資料型態(Type)，它有兩種可能結果真（true)與假(false)，非真即假。
首先就是這幾個
*  ```==``` 相等
*  ```!=``` 不相等
*  ```>```  大於
*  ```>=``` 大於等於
*  ```<```  小於
*  ```<=``` 小於等於
*  ```&&``` 且 
*  ```||``` 或
[^3]
可以試著輸入幾個
```3 > 2``` ```50 < 100``` ``` ((3 <= 5 && 100 != 3 ) || 50 >100 ) ```
出來的結果不是true就是false。這裡要複習一下邏輯的且、或、非判斷式，常常程式的錯誤都是出在這種判斷式沒有算清楚，大家這邊請先熟悉。
##課後練習
完成一開始的範例，首先透過
```js
var date = new Date();
var day = date.getDay();
```
取得星期幾，如果是星期一到五則印出```上班```，如果是六日就印```放假```
_不要列出七個if else，請善用boolean operator_


[^1]: 
要注意的是條件判斷式中是```==```不是```=```，在js中=是用於給值。
[^2]:
Date()為內建物件，之後會在介紹，此方法能取得今天是星期幾1～7。
[^3]:
是 ```==``` ```&&``` ```||```不是```=``` ```&``` ```|```他們是完全不同的意義。請一定要注意這點，搞錯會讓程式出現意料之外的錯誤。

##Switch
除了if_else之外，還有switch可以做條件判斷，在有些情況可以使程式碼變得更簡潔。*請記住switch在有些情況下會讓程式變得更不容易閱讀。*
這裡先用簡單的例子解釋switch的用法。
```js
var date = new Date();
var day = date.getDay();
switch (day){
	case 0:
		console.log("上班");
		break;
	case 1:
		console.log("上班");
		break;
	case 2:
		console.log("上班");
		break;
	case 3:
		console.log("上班");
		break;
	case 4:
		console.log("上班");
		break;
	case 5:
		console.log("上班");
		break;
	case 6:
		console.log("放假");
		break;
	case 7:
		console.log("放假");
		break;
}
```
這邊要特別注意的是```break```，代表跳出此判斷式中，如果沒有```break```會從當前那行一直往下進行，直到遇到下一個break或是離開此大刮號。試試把```break```拿掉試試看
```js
var date = new Date();
var day = date.getDay();
switch (day){
	case 0:
		console.log("上班");
	case 1:
		console.log("上班");
	case 2:
		console.log("上班");
	case 3:
		console.log("上班");
	case 4:
		console.log("上班");
	case 5:
		console.log("上班");
	case 6:
		console.log("放假");
	case 7:
		console.log("放假");
}
```
知道```break```就能稍稍改一下此範例。
```js
var date = new Date();
var day = date.getDay();
switch (day){
	case 0:
	case 1:	
	case 2:
	case 3:
	case 4:
	case 5:
		console.log("上班");
		break;
	case 6:
	case 7:
		console.log("放假");
		break;
}
```
```switch```也有像是```if-else```的語法：```default```在沒有符合任何一個條件會進執行```default```
所以上面的範例可以再改成更短一些。
```js
var date = new Date();
var day = date.getDay();
switch (day){
	case 6:
	case 7:
		console.log("放假");
		break;
	default:
		console.log("上班");
		break;
}```
不過在這種情況下建議的寫法還是第二種，因為第三種有程式碼不易了解的缺點。[^4]

[^4]:程式碼寫的越短不代表越會寫程式，程式執行的速度與程式碼的易讀性才是程式設計者該努力的方向，隨著電腦速度越來越快，程式越寫越大，程式碼的易讀性變得越來越重要。能寫出讓人一看就懂的程式碼才是厲害的程式設計師。
