# 十六、 回傳 (return) 差異
###### tags: `JavaScript` `JS101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/13`

---
## 回傳 (return) 的作用
即需要回傳值時會用 return 。

函式 (function) 兩功能:
1. 你需要他運算完後回傳後去做甚麼事情，你需要知道結果(回傳值) 。
2. 你只是要呼叫他不需要回傳值，即你不需要知道結果。

__1. 如需要回傳值的情況:__
希望得到 x*2 的結果。

    function double(x) {
      return x*2  // 如果不回傳會預設回傳 undefined ;
    }
    double(3)

也比較少只有出現一個只有 function 的結果，通常 function 都會有回傳值;
如果只有這樣，是甚麼都不會產生，因此:

    function double(x) {
      return x*2
    }
    var result = double(3)  // 這個 result 就會是 3*2的結果
    
    console.log(result)
如果需要回傳值的話，要寫 return ， 但 return 後要接要的參數值(value) 。
    
---

要注意的是，在 function 內一用到 return 就會立刻回傳，例如:

    function double(x) {
      console.log(12345)  
      // console.log 放在 return 前面會先執行;
      return x*2
      // console.log(12345) 放這裡不會執行
    }
    var result = double(3)  // 這個 result 就會是 3*2的結果
    
    console.log(result)
    
只會回傳 1 為結果的情況:

    function double(x) {
      return 1 
      // 會先執行回傳，以下都不會執行，只會回傳結果 1 ;
      console.log(12345)
      // 不會執行;
      return x*2
      console.log(12345)
      // 不會執行;
    }
    var result = double(3)  
    // 這個 result 也不會執行;
    
    console.log(result)

真的只回傳結果 1 。

---

__2. 如不需要回傳的情況:__

如果要把 double 後的值給印出來:

    function printDouble(x) {
      console.log(x*2)
    }
    
    printDouble(3)
    
---

    function sayHello() {
      console.log('hello')
    }
    
    sayHello()
    
會回傳 hello 。
也可以在 sayHello( ) 傳參數:

    function sayHello(name) {
      console.log('hello', name)
      // 如果在這裡回傳 return 1 也不會有所影響，其預設是回傳 undefined ;
    }
    
    sayHello('John Titor')

但如果沒有回傳，return 會預設 undefined :    

    function sayHello(name) {
      // console.log('hello', name) ;
      // 這裡會回傳 return undefined  ;
      /* 
        這邊 return 甚麼, a 就會是甚麼 ， y=f(x) 最後 x 產生是甚麼 ， 
        y 就是甚麼;
      */
    }
    
    var a = sayHello('John Titor')  
      // a 就會是 say hello 的回傳值;
    console.log(a)
會回傳 return undefined 。
因此可以修改 return :    

    function sayHello(name) {
        // console.log('hello', name) ， 如果這邊先加上就會先執行;
      return 'I am. '  
        // 執行到這行 retrun 時，第八行的 var a 就會賦予字串 'I am.'
        //  這邊的 return 是甚麼 ， a 就是甚麼。
    }

    var a = sayHello('John Titor')
    console.log(a)

但如果不需要知道結果，其實也不會賦予 function 的回傳值給 a 。

[參考 MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/return)

---

# 十七、 數字相關內建函式
好處是可以節省時間、簡潔程式碼，如數字相關函式。

## 1. 字串轉數字:
這是常見的類型轉換問題。

    var a = 10
    var b = '20'
    console.log(a+b)
      
因為類型是字串，就會自動轉會成字串，所以會印出 1020 。 
所以要將字串轉成同數字類型:

    var a = 10
    var b = '20'
    console.log(a + Number(b))
    
這樣就會印出 30 。

---

## 2. parseInt  
這是可以將參數解釋成幾進位的函式:

    var a = 10
    var b = '20'
    console.log(a + parseInt(b, 10))
    // parseInt(b, 10) 內 b, 10 的 10 表示 10 進位制;
    
會印出 30 ，但不適用數字後有小數點位的，因為 parseInt 適用於整數。

---

## 3. parseFloat
浮點數的函式:

    var a = 10
    var b = '20.35'
    console.log(a + parseFloat(b, 10))

主要拿來 pass 小數用的。   
如果小數點位太多，可以取固定的小數點後第幾位:

    var a = 10
    var b = '20.354545'
    
    console.log(parseFloat(b, 10).toFixed(2))
   
`.toFixed(2)` 取 2 的話，可以取到小數點後兩位; 甚麼都不傳的話 `.toFixed()` 會去掉所有小數位。

---

## 4. MAX_VALUE, MIN_VALUE
表示數據能存取的最大值和最小值:

    console.log(Number.MAX_VALUE)
    
如果直接印出來為: 1.7976931348623157e+308
表示這是 JS 所能儲存的最大值，超過的話存數據會不精準。

---

## 5. 跟數學有關的函式
開頭幾乎都是 `Math.xxx()` 例如:

### 圓周率函式:

    console.log(Math.PI)
    
不會變的圓周率常數就會印出來。
Math.接大寫的幾乎都是常數的函式。

### 自動無條件進位到天花板 (ceil) 的方法 `Math.ceil` :    

    console.log(Math.ceil(10.5))
    
進位成 11 。

### 自動無條件捨去躺到地板 (floor) 的方法 `Math.floor` : 
    
    console.log(Math.floor(10.5))
    
捨去成 10 。

### 四捨五入 (round) about 的用法

    console.log(Math.round(10.4))

### 開根號

    console.log(Math.sqrt(9))

### 次方

    console.log(Math.pow(2, 10))


### 產生隨機數

    console.log(Math.random(1)*10+1)
會產生一個 0 到 1 ，但不含 1 的數字    
*10 會變成 0 ~ 9.999...
+1 會變成 1 ~ 10.999...

也可以與其他式子並用:

    console.log(Math.floor(Math.random(1)*10+1))
可以產生 1 ~ 10 的數。

## 6. 數字變成字串
### 第一種 `.toString()` : 
    
    var a = 2
    a.toString()
    
這不會印出東西。

### 第二種，加上空字串:

    var a = 2
    (a + '')

[參考資料 from MDN : 1. Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
[參考資料 from MDN : 2. Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

---

