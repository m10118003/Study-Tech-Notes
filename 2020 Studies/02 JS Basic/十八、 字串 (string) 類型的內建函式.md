# 十八、 字串 (string) 類型的內建函式 
###### tags: `JavaScript` `JS101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/14`

---
## JS 內建字串相關函式

### 1. 要大寫呢? 還是小寫呢?
可以把字串變大寫或是小寫。

`toUpperCase` 的情況:

    var a = 'abc'.toUpperCase()
    
    console.log(a)
    
將字串變大寫~

`toLowerCase` 的情況:

    var a = 'ABC'.toLowerCase()
    
    console.log(a)
    
將字串變小寫，如果字串內有符號將會忽略。

---

## 2. 想要拿就要動手拿
如何得到字串所代表的數字為多少 ?

`String.charCodeAt()` 

ASCII code : 字串在電腦內有對應的數字，實際存取的值。
 
    var a = 'S' 
    var aCode = a.charCodeAt(0)
    // charCodeAt() 後面接字串位置，如 0 表示第一個位置的 'S' ;
    
    console.log(aCode)
    
會印出 S 這個字串為數字 83 ， 英文字母對應的數字都有順序，是連續的，中間不會有特殊符號。  
如 A=>65 ， a=>97 ， 則 B=> 66 ， b=>98 。

---

## 3. 有值就有義
因此也可以把數字變成代表的字串值 ， `.fromCharCode` :  

    var a = 'S'
    var aCode = a.charCodeAt(0)
    var Str = String.fromCharCode(83)
    console.log(aCode)
    console.log(Str)
    
會印出 83 和 S ， 因此也可以應用在小寫轉大寫:

    var a = 'g' 
    var aCode = a.charCodeAt(0)
    var Str = String.fromCharCode(103-32) 
    //  var Str = String.fromCharCode(aCode-32) 比較聰明的做法應該是這樣;
    console.log(aCode)
    console.log(Str)  

另一種:

    var a = 'g'
    var aCode = a.charCodeAt(0)
    var Str = String.fromCharCode(aCode-('g'.charCodeAt(0) - 'G'.charCodeAt(0)))
    // 可以是 var Str = String.fromCharCode(aCode-(aCode - 'G'.charCodeAt(0)))
    console.log(Str)
    
有些程式語言可以用兩個字串相減來得到差距後回傳。

---

## 4. 來比誰大
字串可以比大小:

    var char = 'g'
    console.log(char >= 'a')

g 的順位比較大。
另外一種應用在邏輯運算:

    var char = 'g'
    console.log(char >= 'a' && char <= 'z')

g > a ， 而 g < z 所以是 true 值。
利用這方式可以判斷順位大小，也可以應用在判斷大寫:

    var char = 'g'
    console.log(char >= 'A' && char <='Z')

false ， 小寫預設比大寫小~
換成大寫 A 到 Z 均為 true 。

---

## 5. 尋找外星人到底存不存在

用 `str.indexOf('hello')` 找尋某個字串存在與否:

    var str = 'Hello World ! ZA WARUDO !'
    var index = str.indexOf('WARUDO')
    console.log(index)

會印出 17 ，第 17 個字就是 WARUDO (會省略符號) 。
找一個不存在的值就會是 -1 ， 即 index < 0 表示不存在。

---

## 6. 取代了心靈的空虛

可以取代字串的方法:

    var str = 'Hello World ! ZA WARUDO !'.replace('Hello World ! ZA WARUDO !', 'NIGARO JOTARO')
    console.log(str)

就會是 NIGARO JOTARO 。
這比較適用於第一個且單一個字串替換，如 y 換成 ! ， 或是把某個字換成其他字。

如果是整個取代:
/你要換的字串/g

    var str = 'hey yoyoyoyoyo'.replace(/y/g, '!!!!')
    console.log(str)
    
g 是 global 表示全部替換。

---

## 7. 次元切割刀
可以把單字切開，切成陣列，並回傳陣列:
    
    var str = 'hey yoyoyoyoyo'
    console.log( str.split())

會印出:
![](https://i.imgur.com/UTDoNsZ.png)

如果在 `str.split()` 中輸入 ' ' ， 會分割開來:
    
    var str = 'hey yoyoyoyoyo'
    console.log( str.split(' '))

變成有空格的地方自動分割，成為內含兩個字串元素的陣列。

![](https://i.imgur.com/CanjB15.png)

以 y 來切的話:
![](https://i.imgur.com/4FfbTVq.png)

就會把所有的 y 都取代掉，並轉換成陣列內帶有多個字串元素。
常用在 csv 格式，用逗號來分割，如:
    
    var str = 'data1, data2, data3, data4'
    console.log( str.split(','))

會比單一處理字串好，可以處理這個陣列內的各個字串。

## 8. 去掉空格的方法

假設字串內有空格，想去掉的話可以用 `str.trim()` 表示:

    var str = ' data1, data2, data3, data4 '
    console.log(str.trim())
    
會把前後空格(不管多少個)都去掉。
進階用法，跟迴圈搭配:

    var str = 'data1,data2,data3,data4'
    console.log(str.length)

    for(var i=0; i<str.length; i++) {
      console.log(str[i])
    }

會把所有單字列在直的一行。
    
    
[來源資料: MDN 字串操控補充](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

---