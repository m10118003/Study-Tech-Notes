# 十九、 陣列 (array) 相關內建函式 
###### tags: `JavaScript` `JS101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/14`

---
## 1. 人體蜈蚣
用 `.join` 把陣列的每個元素用想要的字串接在一起:

    var arr = [1, 2, 3]
    console.log(arr.join('!'))
    
頭尾不會有 ! ， 是在陣列空格內接上，會印出: 1!2!3 。
如果無指定，預設值為空白，會直接把陣列內的所有字元印出。

---

## 2. 要記得看小地圖才不會被 gank
`.map()` 可以把每個元素傳入:

    var arr = [1, 2, 3]
      // 宣告陣列賦給 arr ; 然後最後一行的 .map 讓陣列元素代入下行函式;
    function double(x) {
      // 這時候的 x 為 1 2 3 ， 並根據函式 內計算 * 2後回傳;  
      return x*2
    }
    
    console.log(arr.map(double))

`.map` 可以讓第一行陣列中每個元素，代入 `(arr.map(double))` 內，然後將回傳值取代原本的值，因此會印出 [ 2, 4, 6 ] 。

如果是匿名函式的作法:

    var arr = [1, 2, 3]
   
    console.log(arr.map(function (x) {
      return x*2
    }))

一樣印出 [ 2, 4, 6 ] 。

陣列內還可以接東西:

    var arr = [1, 2, 3]
   
    console.log(
      arr
      .map(function (x) {
        return x*-1
      })
      .map(function(x) {
        return x*2
      })
    )

會印出印出 [ -2, -4, -6 ] ; `.map` 可以一直接下去 。

---

## 3. 濾水器

也可以回傳一個 array 的作法:
`.filter` 可以過濾東西，回傳 true 的值會留下，而剔除 false 。

    var arr = [1, 2, 3, -2, 3, -5]
    
    console.log(
      arr
      .map(function(x) {
        return x*2
      })
      .filter(function(x) {
        return x>0
      })
    )

會印出 [ 2, 4, 6, 6 ] ，去掉了負值。
也可以 `.map()` `.filter` 接下去，但不能 `.filter` 後接 `.join` 如:

`.filter` 可以過濾東西，回傳 true 的值會留下，而剔除 false 。

    var arr = [1, 2, 3, -2, 3, -5]
    
    console.log(
      arr
      .map(function(x) {return x})
      .filter(function(x) {return x})
      .join(function(x) {return x}) 
        // .join 回傳的是字串，而字串沒有 .map 的函式，所以不能接在 .filter 後;

---

## 4. 我只想要一塊蛋糕

想要陣列的某個部分，會從索引值所要求的部分開始切，記得陣列的起始值是 0 :

    var arr = [0, 1, 2, 3, 4, 5, 6]
    
    console.log(arr.slice(3))
    
會回傳陣列並印出 [ 3, 4, 5, 6 ] ， 傳數字 3 表示 含 3 以後的數字全都要~
如果這樣:

    var arr = [0, 1, 2, 3, 4, 5, 6]
    
    console.log(arr.slice(3, 4))

只會印出 [3] ，表示從第三個開始切，但切到第四個不要，因此只保留數字 3。 

---

## 5. 增加或減少排隊的人數

會改變原本的陣列並加入或刪除新元素 `array.splice(startp[, deleteCount[, item1[, item2[, ...]]]])` :
以 MDN 範例說明:

    const months = ['Jan', 'March', 'April', 'June'];
    months.splice(1, 0, 'Feb');
      // months.splice(1, 0, 'Feb') ， 括號 1 表示在 1 位插入 Feb 字串 ， 0 表示不刪除;
    console.log(months);
      
    // 會輸出 Array :  ["Jan", "Feb", "March", "April", "June"]

    months.splice(4, 1, 'May');
    // 表示在第 4 位後插入 May 字串，且刪除 1 個字串;
    console.log(months);

會輸出一個 Array :  ["Jan", "Feb", "March", "April", "May"]

---

## 6. 整理房間吧

### 根據 MDN 的範例`.sort()` 可以使陣列排序:

    const months = ['March', 'Jan', 'Feb', 'Dec'];
    months.sort();
    console.log(months);

會根據英文字母順序輸出 ["Dec", "Feb", "Jan", "March"] 。

### 無法照數字大小排的情況

    const array1 = [1, 30, 4, 21, 100000];
    array1.sort();
    console.log(array1);
    
按照順序 1, 2, 3... 會變成字串的類型來排 [1, 100000, 21, 30, 4]

### 如果要照數字比大小

需要用另一個函式 `.aort[compareFunction]` :    

#### 這是一般照字串排列的情況:

    var arr = [1, 30, 4, 21]
    arr.sort()
    
    console.log(arr)

會照字串順序排成 [ 1, 21, 30, 4 ]

#### 如果用 if 的由小排到大的話:

    var arr = [1, 30, 4, 21]
    arr.sort(function(a, b) {
      if (a===b) return 0
      if (b>a) return -1
      return 1
    })
    
    console.log(arr)

規則如下:
1. `arr.sort(function(a, b)) {` 會回傳 a, b 兩值，規則是如果相等的話; `if (a===b) return 0` 要回傳 0 ， 代表相等; 這函式是在告訴 sort 要如何排數字。

2. 如果要 a, b 互換位置的話，就回傳 1 ，不是的話則回傳 -1 ; 假設 a=1 ， b=4 ， 則不想互換位置，所以 `if b>a return -1` 。

3. 可以想像 a 在前面 ， b 在後面，如果相等的話就回傳 0 ，如果想要換位置就回傳 1 ，否則回傳 -1 ; 正數的話會換位置，不一定要 1 ， 負值則不會換位 ， 0 是相等。

#### 如果是由大排到小:

    var arr = [1, 30, 4, 21]
    arr.sort(function(a, b) {
      if (a===b) return 0  // 不用邏輯運算的話會自動判斷帶入下一行;
      if (a>b) return -1
      return 1  // 回傳任一正數都行，這邊輸入 >=0 的數皆可; 
    })
    
    console.log(arr)

a>b 表示由大排到小，則不換位置 return -1 ， 不然就回傳 1 。

#### 也可以用三元運算子 `condition ? exprIfTrue : exprIfFalse` 比較:

    var arr= [1, 30, 4, 21]
    arr.sort(function(a, b) {
      if (a===b) return 0
      return (a>b ? -1 : 1)
    })
    
    console.log(arr)
因此可以由大排到小，印出 [ 30, 21, 4, 1 ] 。

如置換 `return (a>b ? -1 : 0)` 一樣會是 [ 30, 21, 4, 1 ] 。
如果置換 `return (a>b ? 1 : -1)` 則順序相反，由小排到大 [ 1, 4, 21, 30 ] 。
如 `return (a>b ? 0 : -1)` 一樣是 [ 1, 4, 21, 30 ] 。

#### 運用數學概念的大到小排法

    var arr = [1, 30, 4, 21]
    arr.sort(function(a, b) {
      return b-a
    })

    console.log(arr)
假設 a 是運用兩數相減，會得到正值會換位，因此在前面，會印出 [ 30, 21, 4, 1 ] ; 反之 a-b 則是負值不換位 [ 1, 4, 21, 30 ] 。

推論，我們想由小到大 ， if b>a  => return -1 → 如果是 a - b 是負數就會滿足這個條件。
if b<a => return 1 → 如果是 a - b 是正數就會滿足這個條件。

    
[陣列相關函式補充](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)