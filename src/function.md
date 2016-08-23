# function
還記得前面一直強調要維護可讀性嗎？如何要讓程式碼一行就看得懂？函數的設計與使用是很重要的，並且可以減少很多重複的程式碼，先試試看執行下面程式碼：
```js
function multiply2(x){
	console.log("I got number",x);
	return x*2;
}
console.log(multiply2(50));
```
用關鍵字```function```開頭，括號內的可以自由取名子，而回傳值則是執行function會得到的值。
括號內的參數數量可以自由定義，試執行以下程式碼：
```js
function max(x,y){
	if (x>y){
		return x;
	}else{
		return y;
	}
}
console.log(max(3,5), max(5,3));
```
也可以有沒有回傳值的```function```
試試看下面的範例：
```js
function printSignature(){
	console.log("This is Jonah.");
}
for(i = 0; i <10; i++){
	printSignature();
}
```

##課後練習
請大家練習寫出一個```function```回傳三個參數中最大的那個。
```js
function max(x, y, z){
	//Write your code!
}
console.log(max(50, 60, 70));
```
