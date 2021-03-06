# 迴圈
##While
```while``` 能重複執行一段程式碼，一樣先從簡單範例介紹。
```js
let i = 0;
while(i < 10){
	console.log(i);
	i++;
}
```
如果符合```()```內條件則執行```{}```內的程式碼。
##Do-while
```do``` 與```while``` 類似，不過```do``` 會先執行一次之後再判斷，如果符合條件的話再重新執行。
```js
let i = 0;
do{
	console.log(i);
	i++;
}while(i<10)
```
在這裡結果會一樣，但比較以下兩種程式碼。
```js
let i = 10;
do{
	console.log(i);
	i++;
}while(i<10)
```
```js
let i = 10;
while(i<10){
	console.log(i);
	i++;
}
```
能看到do-while還是印出了10
##For
上面那段程式也可以用以下程式取代。

```js
for(i = 0; i < 10; i = i++){
console.log(i);
}
```
與下面這段程式碼完全相同。
```js
let i = 0;
while(i < 10){
	console.log(i);
	i++;
}
```


```for``` 括號內用兩個分號分成三段，第一段是程式執行前會執行的，第二段是條件，第三段是這段迴圈後跟下次迴圈開始前會執行的程式碼，大家可以試試看以下這段程式碼，看看與前面有什麼不同。
```js
for(i = 0; i < 10; console.log(i)){
	i++;
}
```
[^1]
##課後練習
請大家利用算出2的31次方。[^2]

	
[^1]: 這裡是為了讓大家了解for-loop做的解釋，這是非常不好的示範，作為程式初學者，使用這種寫法容易讓自己搞混，事實上，作為程式設計者幾乎沒有任何理由一這種方式寫程式，這除了讓自己更容易搞混外沒有任何得好處。我們將這種不依照慣例的寫法稱為黑魔法，雖然適當的使用黑魔法可以讓程式碼更"短"，但是容易把自己與別人搞混。

[^2]: 2的31次方在電腦程式裡面是很重要的（事實上是2^31 -1）。
