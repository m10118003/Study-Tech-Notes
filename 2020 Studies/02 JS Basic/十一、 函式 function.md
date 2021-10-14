# 十一、 函式 `function` 
###### tags: `JavaScript` `JS101` `2020七月第二週` `進度筆記` `Lidemy心得` `7/8`

---

數學上的函數 `y=f(x)` 跟程式的函式是類似的東西，函式為丟某個東西進去就會回傳值:

![](https://i.imgur.com/WIUU2Ek.png)

---

## JavaScript 的函式
### 基本結構:

    function f() { 
      return 
    }

f 為函式名稱，可以更動; () 內放參數，參數名稱也可以隨意更動;

例如:

    function f(a, b, c) {
      return a + 2*b + 3*c
    }
    
    console.log(f(1, 2, 3))
    // 答案會是 14 。
    
---

### 目標可以執行
可以執行物件在區塊內:

    function f(x) {
      return {
        answer: x*2
      }
    }
    
    console.log(f(10))
    // 答案會是 20 。
    
為何目標 undefined ? :    

    function f(x) {
      return  // 這邊會傳回 undefined;
      { 
        answer: x*2
      }
    }
    
    console.log(f(10))
    
一行一行看會是 ， function f(x) {
return 這是第一句，因後面沒接區塊，所以回傳 undefined
{ answer } 這邊是第二句，會變成無意義。 }
最後跑 console.log(f(10)) ， 但因上面已回傳 undefined ， 所以會直接印出。

---

### 可以產生陣列
函式區塊內也可以接陣列，假設我要自動產生一個規律到 10 : 

    function makeArray(n) {
      var result = []
      for (var i=1; i<=n; i++) {
        result.push(i)
      }
      return result
    }
    console.log(makeArray(10))
    // 會印出 [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
    
最後一行如果改成 `console.log(makeArray)` 則會印出 [Function: makeArray] 這是一個函式。

---

也可更改參數數目，並要求回傳某值到某值之間:


    function makeArray(from, to) {
      var result = []
      for (var i=from; i<=to; i++) {
        result.push(i)
      }
      return result
    }
    console.log(makeArray(3, 10))
    // 會印出 [ 3, 4, 5, 6, 7, 8, 9, 10 ]
    
參數也可以自己取名，通常建議可以看出 range 的，像是 (from, to) ， (min, max) 。

---

也可以傳變數給 console.log(makeArray(3, 10)) : 

    function makeArray(from, to) {
          var result = []
          for (var i=from; i<=to; i++) {
            result.push(i)
          }
          return result
        }
        var a = 3
        var b = 10
        console.log(makeArray(a, b))
        // 會印出 [ 3, 4, 5, 6, 7, 8, 9, 10 ]
    
最後一行 `console.log(makeArray(a, b))` 表示傳進去的值，其傳進去的值不一定要跟第一行的 `function makeArray(from, to) {` ( )內的參數同名稱，但函式參數名稱，需跟函式區塊內迴圈起始條件和終止條件的名稱一致。

---

也可以不用 console.log 回傳值:

    function log(n) {
      for (var i=1; i<=n; i++) {
        console.log(i)
          }
        }
        log(10)
        // 會印出 1 到 10 (隔行)。

---

### 解題的時候不知道怎麼解，可以先從寫 function 開始，先寫一個大綱。

    function printTo100() {
    
    }
    
    printTo100
    
假設寫出從 1 到 100 的偶數:

    function logEven(number) {
      if (number%2===0) {
        console.log(number)
      }
    }
    function printTo100() { //這邊開始都是結構，比較能看出想要做甚麼;
      for (var i=1; i<=100; i++) {
        logEven(i)
          }
        }
        printTo100(100)
        // 會從 2 開始印直到 100 的偶數。

---

自己 try 偶數到 100 :    

    function printTo100(n) {
      for (var i=1; i<=n; i++) {
        console.log(++i)
          }
        }
        printTo100(100)
        // 。


---
自己 try，自動產生偶數規律到 10 :  

    function makeArray(n) {
      var result =  []
      for (var i=1; i<=n; i++) {
        result.push(++i)
         console.log(i)
      }
      return result
    }
    console.log(makeArray(10))




