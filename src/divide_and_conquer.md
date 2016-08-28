# 分而治之法

前面講了遞迴，其實遞迴有點隱含了演算法設計常用的「分而治之」法（Divide and Conquer）。意思是說，直接解一個大問題很難，如果我們可以把一個大問題切成很多的小問題，再把小問題的答案結合起來，說不定會簡單一點。

例如，前面提到的「排序問題」，這裡要介紹一種時間複雜度最低的演算法：合併排序（Merge Sort）。合併排序的概念是，把一個陣列切兩半，對兩半分別再切兩半，直到不能切為止，然後再一層層的把排序好的兩半合起來。

我們先看看「合起來」是如何做到的。假如我們要把兩個已經排序的數列合起來變成一個大的已排序的陣列，那麼這樣的時間複雜度會是多少？答案是 $O(n)$。方法是，例如我們有兩個數列 `[1, 2, 5, 7]` 和 `[3, 4, 8, 9]` ，我們可以每次都從兩個陣列挑出一個最小的數來依序放到另一個陣列裡，於是新的陣列就會是排序過得了。而每次我們在挑選兩者最小的數時，有可能的答案只有兩陣列中最小的數，也就是兩陣列中最前面的數，兩者之中較小的就是最小的數。也就是說每挑出一個最小的數我們都只需要做一次比較，而總共有 $N$ 個數，所以整體而言我們只需要比較 $N$ 次，所以複雜度是 $O(N)$。前幾步是這樣的：

```
[1, 2, 5, 7]  [3, 4, 8, 9]                     新陣列 []
[1, 2, 5, 7]  [3, 4, 8, 9] -> 1 < 3 -> 拿出 1         [1]
   [2, 5, 7]  [3, 4, 8, 9] -> 2 < 3 -> 拿出 2         [1, 2]
      [5, 7]  [3, 4, 8, 9] -> 5 > 3 -> 拿出 3         [1, 2, 3]
      [5, 7]     [4, 8, 9] -> 5 > 4 -> 拿出 4         [1, 2, 3, 4]

...

                                                             [1, 2, 3, 4, 5, 7, 8, 9]
```                                                             

而「切兩半」這件事會像這樣：

```
2 5 7 1 3 8 4 9
2 5 7 1|3 8 4 9
2 5|7 1|3 8|4 9
2|5|7|1|3|8|4|9
```

最多只有大概 $\log_2{N}$ 層，而合併每一層的時間只需要 $N$，所以整體而言複雜度會是 $O(N \log N)$