# 遞迴

遞迴其實不太算是演算法，簡單來說遞迴就是在函式中呼叫自己。像是眾所皆知的費氏數列本身就是遞迴定義：

$$F(n) = \begin{cases}
    1 &\mbox{if} n = 1 \vee n = 2 \\
    F(n - 1) + F(n - 2) &\mbox{otherwise}
\end{cases}$$

於是我們可以在 Javascript 中這樣寫出

```js
function fib(n){
    if(n === 1 || n === 2){
        return 1;
    }
    else {
        return fib(n - 1) + f(n - 2);
    }
}
```

當然這不是最快的做法，這個方法的複雜度會是 $$O(e^n)$$ 因為他所需的時間正比於 $$F(n)$$，而 $$F(n) \geq 2^{\frac{n}{2}}$$（事實上最快的方法可以到 $$O(\log{n})$$）。

許多問題都可以用遞迴的方式解決（即使不一定是最快的方法），像是

* 印出一串數字的所有排列組合。
* [河內塔問題](http://openhome.cc/Gossip/AlgorithmGossip/HanoiTower.htm)
