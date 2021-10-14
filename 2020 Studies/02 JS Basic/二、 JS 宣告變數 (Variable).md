# 二、 JS 宣告變數 (Variable)
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得`

## 變數是甚麼 ？ 
想像變數是個箱子，裡面裝了東西，要宣告 (var) 變數的話要用 `var` + 接的變數名稱，如:

    var box = 123
    var BOX = 456
            // = 這符號是賦值
    console.log(box, BOX)
    
會印出 123 456 ， JS 內大小寫是有區別的，而如果宣告變數卻沒賦予，或是 .log 一個完全不存在的東西則會出現 undefined 和 not defined ， 如:

    var box
    console.log(box)
    
變數不能用數字開頭:

    var box = 123
    var hello = 60
    var 1fwefo = 1   //1fwefo 會出現錯誤
    console.log(box & hello)



有些特殊符號也不行例如驚嘆號，也不能有保留字，程式本身會用到的，需要好好命名:

    var box = 123
    var hello = 60
    var var = 1   //var var 會出現錯誤
    console.log(box & hello)

一個變數也能操作:

    var a = 0
    a = a + 5 
    a = 5

    var a = 0
    a = a + 5
    a += 5
    10


還可以再更簡化:

    var a = 0
    a += 5 
    5      

---

前置型遞增 ++i 或遞減 --i : 先將自身運算，再賦值給變量 (先運算自身增加或減少了多少錢，再把它存到自己的銀行戶頭裡或還給債主) 。


    var i = 100
    // alert（i） => 100; 先將 100 賦給 i ; 會先計算自身增加多少錢 。
    ++i       
    // alert（i） => 101 ; 再將其存到自身銀行戶頭或者再還給債主。
    101　　　　

    //相當於下式:

    var i = 100
    i = i + 1 
    i = 100 + 1 
    101

---

通常一行程式 (  ) 內只會有一個 "遞增" 或 "遞減" ( ++ 或 -- ) ， 再多會有點複雜 。

    var a = 0
    
    console.log(++a && 30) 
    // 會先執行 a+=1 ， 先算值再賦變數再執行整句;
    30
    console.log('a:', a)   
    //然後再執行這句 。
    a:1
    
執行前置型遞增或遞減時，變量的值都是在語句被求出值以前可以被改變的 （在計算機科學領域中常被稱作"副效應"） ， 所以有後置型 "遞增" + 1 或 "遞減" -1 ， 又稱後增量(post-increment) :

    var i = 100
    // alert（i） => 100 一樣將 100 賦給 i; 即先把自身上錢 100 存到自身銀行戶頭內或是先還給債主;　　　　　　　
    i++
    100
    // alert（i）;  => 然後再計算自己在原來基礎上增加或是減少多少錢 。
    101               

後置型遞增 i++ 或遞減 i-- : 先將自身的值賦給變量，再運算自身（先將自身的錢存到自己銀行戶頭內或是先還給債主，然後再計算自己在原來基礎上增加或減少多少錢）。
[參考來源:](https://www.itread01.com/content/1495002249.html)

---

    var a = 0
    
    console.log(a++ && 30)    // 會先賦予變數再算值，將這整句跑完，因此 && 左邊賦予 0 是 false ;
    0
    console.log('a:', a)      // 因為變數賦予完了，再執行 a++ 計算。
    1
    
    // 相當以下:
    
    var a = 0
    
    console.log(a++ && 30)
    0
    console.log(a && 30)  // a++ ， 相當於 a+= 1 。
    1
---


     var a = 1
    
     a += 1
     2
     a++   // 效果直接 + 1
     2
 
    var a = 1
    a++
    1

    a = 0
    0
    a--
    0
    a--
    -1

    var a = 0
    a--
    0
    
---



## 命名方式

Underscroll ， 命名規則加底線:

    var this_is_a_box = 13
    
駝峰式，如多個英文字連接組成，有開頭都要大寫駝峰型，也有開頭小寫駝峰型，如:

    var UpperCamelCase
    var upperCamelCase

變數命名的時候要好好命名，以看得懂、容易區別、辨識...等，如屬性 (field) 名稱、方法 (method) 名稱、參數 (parameter) 名稱、區域變數 (local variable) 名稱；也有匈牙利命名法，將資料型態寫在變數名稱前，如:

    intNum(整數)
    strName(字串))
    
---

## 三、變數型態

宣告的時候 ， JS 的內部還是會給變數一個型態，可以用 typeof 接想看的東西就會印出變數型態:

    console.log('typeof true', typeof true)

![](https://i.imgur.com/OSXpO5l.png)

## JS Primitive 原始型別，[參考資料:](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Data_structures)

### 1. bool 布林(是非 ， boolean)
即 true 、 false 。

### 2. number 所有數字數據類型如整數、浮點(小數) :

##### `int` 整數(Integer)
如100 、 -2 、 1246... 等 。

##### `float` 浮點數(小數 ， floating point)
如: 3.1415 、 0.5 、 -1.5... 等 。

### 3. string 字串(文句 ， String) ， 用雙引號或單引號刮起來:
如: "Hello"、"^_^"、"Rock!" ...等 。

### 4. undefined
type of undefined 即未定義，也是一種回傳值。

## 歸類在 "其他" 的資料結構與型別
物件與函數在語言中是其它的基本元素。

### 5. 物件(object)
對陣列作 type of 會得到 object ， 其實 JS 中沒有陣列，是包含資料與處理資料指令的結構，其 null 的回傳值是 object (歷史原因) 。

### 6. 函數(function)
應用程式所執行的步驟。

[參考資料:](https://www.csie.ntu.edu.tw/~b98902112/cpp_and_algo/cpp/variable_type_and_declare.html)

---

# 四、變數相關: 陣列 (Array)
是很重要的資料型態，假設有 50 個學生的分數平均用簡單的程式來寫:

    var score1 = 30
    var score1 = 50
    var score1 = 10
    ...
    var score1 = 29

    (score1+score2+.....50)/50
    //重複性的性質可以用陣列來優化
    
用圖來看，陣列像是很多的宣告(箱子)疊在一起，裡面裝不同的東西:
![](https://i.imgur.com/732h6qT.png)

 [   ] 内接的是索引值 (index) ， 即目錄 ， JS 陣列的 index 都是從 0 開始，因此優化學生分數的話:
 
     var score = []
     score[0] = 30
     score[1] = 50
     score[2] = 100
     ...
     
差別在於用變數的方式無法用索引方式去取得資料，也會搭配迴圈使用，如:

    var index = 10
    var score = []
    score[0] = 30
    score[1] = 50
    score[index] = 100 
    ...
    /// 表示 score 的第 index 個。
    
## 陣列內可以放不同東西

    var index = 10
    var score = []
    score[0] = 'hello'
    score[1] = 50
    score[2] = 0.4
    score[3] = 'world'
    ...
    ///  陣列通常是性質相同的東西(元素)存很多份，不同性質的可以用不同的變數。
    ///  即一連串的變數。
    
## 陣列內可以給初始值
用中括號[  ]隔開，括號內給逗點 , 就可以給初始值: 

    var score = [1, 3, 5, 10, 100]
    console.log(score)
        
## 陣列內可以取得長度
    
    var score = [1, 3, 5, 10, 100]
    console.log(score.length)
    // 會顯示有 5 個元素。
    
## 陣列內可以取得位置

    var score = [1, 3, 5, 10, 100]
    console.log(score[score.length - 1])
    // 會顯示第四位的 100 ， 因為 JS 陣列的 index 是從 0 開始。
    
## 陣列內可以多放元素

    var score = [1, 3, 5, 10, 100]
    score[score.length] = 1000
    console.log(score)
    
    // 會在陣列中多塞一個元素，或是這樣用:
    
    var score = [1, 3, 5, 10, 100]
    score.push(1000)
    score.push(0.3)
    console.log(score)
    // 會如下圖顯示:
        
![](https://i.imgur.com/eWa14dU.png)

## 陣列內也可以補空值

    var score = []
    score[10] = 100
    score.push(1000)
    score.push(0.3)
    console.log(score, score.length)
    
    // 但其實都是從第 0 個開始放之類的:
    
    var score = []
    score[0] = 100
    score.push(1000)
    score.push(0.3)
    console.log(score, score.length)
    
    // 或是讓他自己決定幫你放哪:
    
    var score = []
    score.push(1)
    score.push(1000)
    score.push(0.3)
    console.log(score, score.length)

![](https://i.imgur.com/G9hr4vj.png)

---