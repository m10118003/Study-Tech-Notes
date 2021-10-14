# 一、 JavaScript 執行與環境建置
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得`

JS 是程式語言， Node.js 跟瀏覽器中按下 F12 的 console 是執行環境。

---

# 安裝

1. 在官方網站安裝 node.js ， Wins 和 Mac 安裝好後輸入 node -v 有出現版本表示安裝完成。

2. 在瀏覽器上寫 JS ，首先可以新建 `vim index.html` 在裡面寫下:

       <script>
       console.log(123)
       </script>
       
   好了後使用指令 `open index.html` 在 wins 瀏覽器中按下 F12 或檢視開發人員工具 (mac 則是:option+cmd+i) 就會在 console 看到 "輸出": 123。 實際操作會在瀏覽器中才會 Debug 。

---

# Hello, World!
在 "瀏覽器" 的情況下是開啟 CLI 輸入: `vim index.html` 然後寫下 ↓
    
    <script>
      console.log('Hello, World!')
    </script>
    
接著在火狐瀏覽器開啟該檔案，在開發人員選項中可以看到: Hello, World!

而 Node.js 的環境則是 `vim index.js` 然後寫下 ↓

    console.log('Hello, World!')

接著在 CLI 中 `vim node.js` 因為有寫 console 就會在 CLI 印出 Hello, World! 

---

# 算術運算

CLI 中 輸入 `node` 下一行會出現 > 輸入四則運算的話就會回傳，要離開就按兩次 ctrl+c ， 10/3 會出現浮點數，由於十進位制無法準確換算成二進位制的部分小數，如0.1，因此只能使用近似值的方式表達 (by Wiki)。

一般 `+ - * /` 都有，而取餘數則是用 `%` 。

## 基本邏輯運算

邏輯有二元邏輯，True or False ，基本邏輯為: 且 And (&&) 、 或 Or (指令中要打 "||" 不能直接寫 or 會印不出來) 、 反相 Not (!) ， 這些邏輯是針對整體的 :  

    true || true
    true

    true || false
    true

---

    true && false
    false

    true && true
    true

---

    !true
    false

    !false
    true

---

[基本邏輯運算](https://openhome.cc/Gossip/CGossip/LogicalBitwise.html): 

1. && 運算中，如果左邊的式子已被評斷為假，如 0 、 no 、 false ，則可立即判斷整個式子為假，因而右邊的式子就不會再評斷；而左邊為真值的話，則由右邊的值決定並回傳右邊的值。

2. || 運算中如果左邊的式子已經被評斷為真，則可以判斷整個式子為真，因而右邊的式子就不會再評斷；而如果左邊被判定 0 、 控制串 、 no 、 false 則只回傳右邊為真之數值。

3. ! 運算則回傳該數值相反之數值。

參考 [MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_Operators#%E6%A2%9D%E4%BB%B6%EF%BC%88%E4%B8%89%E5%85%83%EF%BC%89%E9%81%8B%E7%AE%97%E5%AD%90)

## 數字也可以運用基本邏輯運算

    300 || 13 : 判定左邊 300 。

    false && 0 : false 。 // the && and || operators actually return the value of one of the specified operands, so if these operators are used with non-Boolean values, they may return a non-Boolean value.
    
    0 || console.log(123) : 前面 false 只執行 123 。
    
    true || console.log(123) : 只回傳 true 。

    0 && console.log(123) : 傳回 0 。
    
0 && true ; true && 0 ; 0 && false 皆回傳 0 。  
https://stackoverflow.com/questions/49163180/why-does-0-a-boolean-evaluate-to-0-instead-of-the-boolean

## 位元運算子

[解說 JavaScript 的位元運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Obsolete_Pages/Obsolete_Pages/Obsolete_Pages/%E9%81%8B%E7%AE%97%E5%AD%90/%E4%BD%8D%E5%85%83%E9%81%8B%E7%AE%97%E5%AD%90):

`>>` 維持符號往右移動， `<<` 維持符號往左移動 。
二進位：是電腦語言中最原始的形式，效能通常最好，表示如， 0100 = 2^2 = 4 ； 1000 = 2^3 = 8 。
`>>` 和 `<<` 應用在二進位則是： (2^0=1) * (2^0=1) = 0100 = 2^2 = 4 ， 而如果 0100 的 1 往左移一位則為 1000 = 2^3 = 8 ， 因此可以往左移是乘與二，往右移是除以二:

    10 << 1
    20

表示十進位的 10 在二進位是 1010 且往左移一位成 10100 ，即 10 * 2^1 。

---

    10 << 3
    80

表示十進位的 10 在二進位是 1010 且往左移三位成 1010000 ，即 10 * 2^3 。

---

    1 << 10
    1024

表示 十進位的 1 * (2^10) 。

---

    1 << 31
    -2147483648

過 30 次方會 overflow 。

---

    9 >> 1
    4

會四捨五入，但直接去掉小數點 0.5 。

---

    13 >>2
    6

為 13/2 ，但一樣去掉小數點 0.5 。

----

## 位元運算 (and, or, not, xor)

1. and ， 位元運算會變成二進位，針對每個值進行運算，為一個符號，如:

           1010
           1111
       and ____
           1010

           1010
              1    → 1 的前面都是 0 ， and 有類似可以讀取遮罩效果後的數字 。
       and ____
           0000

           1010
           1000
       and ____
           1000

   1010 可以看作 2(10)+8(1000)= 10(1010)，1111 可以看作 7(111)+8(1000)= 15，而 and 會成為 __"位元運算"__ 每個對應位元兩者均是 1 時 會回傳 1 ， 而 a 者為 0 但 b 者為 1 時則回傳 0 ， a 為 1 且 b 為 0 時則回傳 0 ， 二進位中最後一個數字是 0 的話必為偶數 ， 1 是基數 。 

2. or 則是:

           1010
           1111
       or  ____
           1111
        
   每個對應位元位置的兩個運算元，兩者或其中一者為 1 時，會回傳 1。

3. __xor__ (exculsive or) 則是每個對應同位元位置的兩個運算位元，其中之一而非兩者為 1 時，會回傳 1 ， 如:
   
            1010
            1111
       xor  ____
            0101
        
   如果兩個位元都是 1 就回傳相反值 0，而兩者都是 0 則回傳 0 ， 但 a 者為 0 且 b 者為 1 時則回傳 1 。

4. not 則是回傳所有運算元的反轉形式，如 1 則回傳 0 。

---

## JS 位元與邏輯運算區別

1. and 如果用在 JavaScript 上，位元運算則是換成二進位後一樣針對每個數值運算:

        10 & 15
        10
   
        10 & 1
        0
        
        11 & 1
        1
        
   除了 % (如 12 % 2 這種整除為偶數)，可以判斷奇偶數，& 也可以用來判斷結果是不是奇偶數，是 0 的話為偶數， 1 則為基數 。
   
   但邏輯運算則是兩個符號疊加，如 And(&&) 則是:

        10 && 15
        15

   左邊為真值的話，則由右邊的值決定並回傳右邊的值。


2. 而 JS 的位元運算的 Or (|) 則是:

        10 | 15
        15

    JS 邏輯運算的 Or (||) 則是:

        10 || 15
        10

   左邊的式子已經被評斷為真，則可以判斷整個式子為真。
   
3. xor 的 JS 位元運算則是 ^ 符號，JS 的 ^ 跟一般用於表示次方的符號不同:
        
        10 ^ 15
        5
              
        2 ^ 0
        2
        
4. not 的 JS 位元運算則是 ~ 符號:
        
        ~15
        -16 
        
   將任一個數值 n 做位元 not 運算會得到 -(n + 1) ，如， ~15 會得到 -16 。


        