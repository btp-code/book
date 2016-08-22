# 附錄：偽組合語言

為了可以讓讀者體驗一下「組合語言」，這裡隨便編造了一個「偽組合語言」，並附上[直譯器](https://btp-code.github.io/btp-code/psudo-assembly-interpreter/)。


## 指令參考


### 記憶體操作指令

#### set addr const 

將記憶體位置`addr`的值設為 `const`。

Ex
```
set 10 100
```

#### mov addr1 addr2

把記憶體位址 `addr1` 的值複製到 `addr2`。

#### mvi addr1 addr2

把記憶體位址 `addr1` 的值複製到記憶體位址 `addr2` 儲存的位址。


#### imv addr1 addr2

複製記憶體位址 `addr1` 儲存的位址的值到 `addr2`。


### 數學運算指令

#### inc addr const

增加記憶體位置 `addr` 的值 `const`


#### add addr1 addr2 addr3

把記憶體位址 `addr2` 的值加上 `addr3`的值儲存到 `addr1`。

#### sub addr1 addr2 addr3

把記憶體位址 `addr2` 的值減去 `addr3`的值儲存到 `addr1`。

### 位元運算指令

#### sht addr addr

把記憶體位置 `addr` 的值左移記憶體位址 `addr` 的值。

#### and addr1 addr2 addr3

把記憶體位址 `addr2` 的值位元 and `addr3`的值儲存到 `addr1`。


#### xor addr1 addr2 addr3

把記憶體位址 `addr2` 的值位元 xor `addr3`的值儲存到 `addr1`。


### 流程控制指令


#### hlt

停止。

#### jmp pc

跳到 `pc` 的位址（設定 Program Counter 為 `pc`）。

#### jeq address pc

如果記憶體位址 `address` 的值等於零，則跳到 `pc` 的位址（設定 Program Counter 為 `pc`）。


#### jgt address pc

如果記憶體位址 `address` 的值大於零，則跳到 `pc` 的位址（設定 Program Counter 為 `pc`）。

#### jlt address pc

如果記憶體位址 `address` 的值小於零，則跳到 `pc` 的位址（設定 Program Counter 為 `pc`）。
