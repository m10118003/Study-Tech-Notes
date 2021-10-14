# 十、 迴圈 `loop` 
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得` `7/7`

---

## 1. 迴圈基本介紹

一直 redo 同件事，大概像是重跑操場好幾圈，通常也有個終止條件，像是跑到天黑停下來; 也有無窮迴圈，瘋狂一直跑而且跳脫不了循環，通常在沒有給終止條件，或是設錯終止條件才會發生。

---
## 2. 非 JS 的迴圈介紹

### 這是 JS 沒有的語法: `label` 和 `goto` ， 如假設要印出 1 到 10 的情況:

    console.log(1)
    console.log(2)
    console.log(3)
    ....
    ....
    .
    .
    .
    console.log(10)
    /* 
      這段印不出來;
      那假設要印出更多，印到 100 ， 甚至 10000 次的情況呢 ？  
      這樣可能會沒有效益而且無法規模化，因此需要有方法來規模化。
    */
---

### 規模化的方法:

    var i = 1
    console.log(i)    
    i++  // 等同 i = i+1 ， 也就是 i+=1; 會算出 i=2;
    /* 如果可以用指令一直回到 console.log(i) 這行，
       就會算出 3, 4..., 直到 10 ， 甚至 100 ， 10000;
       就可以達成迴圈的功能; 這只會印出 1 。
    */
---

### `goto` where ? 的場合:
承接上面的式子， JS 雖沒這個語法，但概念就是達成迴圈。
 
    var i = 1
    
    loop:  // 執行每行程式後碰到 loop 後會停下。
    console.log(i)    
    i++  // 等同 i = i+1 ， 也就是 i+=1; 會算出 i=2;
    goto loop // goto 要接 label 為 loop ;
    
    /*   
       這樣會從 var i = 1 開始跑，經過 loop 先不理他，一路跑到 goto loop 後再回 到 loop: ， 然後往
       下跑 console.log(2) ， 再往下跑 i++ ， 接著跑 goto loop  後再回到 loop ， 如此重複，但是因為沒有煞車所以會停不下來。
    */  
---    
    
### 所以我們需要煞車
    
    var i = 1
    
    loop:  // 執行每行程式後碰到 loop 後會停下。
    console.log(i)    
    i++  // 等同 i = i+1 ， 也就是 i+=1; 會算出 i=2;
    if (i<=100) {
      goto loop // goto 要接 label 為 loop ;
    } else {    // 但其實 else 可以不用;
      console.log('finished!')
    }
    
    /* 
      這樣會從 var i = 1 開始跑，經過 loop 先不理他，一路跑到 goto loop 
      後再回 到 loop: ， 然後往下跑 if 直到 i 值超過 100 後，因為有了
      else 煞車才會停下來; 如果最後 i 值超過 100 後把 i 值 log 出來 
      console.log('i=', i) ， 因為要符合 (i<=100) 這個條件時 ， 
      i 已經是 100 了，因此 100 = 100+1， 會印出 101 。
    */    
   
如此可以達到迴圈的功能，一直重複做同件事，和有終止條件，如果沒有終止條件，無窮迴圈會吃掉電腦資源 ， ctrl+c 可以終止。 

---

## 3. 要怎麼用 JS 執行迴圈 ？
### JS 執行迴圈的儀式
常用的情形，第一種是 do...while... 同時做:
    
    // 要記得 ( ) 內是條件，而 { } 內是區塊;
    var i = 1

    do {
      console.log(i)
      i++
    } while(i<=100)  

    console.log('i=', i)
      // 會一直印直到 101 才停。

只要 while(i<=100)，條件是 true 的話，就會回到 do 那行，即無窮迴圈；如果是 fales 即值超過 101 時，會跳出迴圈; 如果跑迴圈不確定怎麼跑的時候記得寫下來，讓自己跟電腦一樣一行一行執行。

---
第二種，如果是 while(true) 的情況，要怎麼一擊脫離 ?:

    var i = 1

    do {
      console.log(i)
      i++
      if (i>100) { // 如果設 i<=100 ， 式子一下就斷掉囉;
        break  // 執行到這個 break 就會中斷並跳出區塊，
      }
      
    } while(true)  
    console.log('i=', i)
      // 一樣印直到 101 才停。
而當 `while(true)` ，條件是 true 的話，是無窮迴圈，因此要有辦法脫離，所以上面有設定 i>100 值; 而如果是 `while(false)` 會先跑第一行印出 1 ， 而執行 i++ 後值為 2 ， 因為 false 的關係即值永遠不會達到 i>100 因此會中斷迴圈; 

---

第三種，街機遊戲一直投代幣停不下來 ， continue :
無窮迴圈的場合。

    var i = 1
    
    do {
      if (i%2 === 1) {
        continue  // 如果 continue 設在這裡，會一直往上跳到 do ， 一直都是 1 的情況
      }
      console.log(i)
      i++
      
    } while(i<=100)
    
    console.log('i=', i)
    // 這是無窮迴圈~

這情況是:

i => 1
do
if ()i%2 ===1) => true
continue
while(i<=100) => true
do
if ()i%2 ===1) => true
continue
while(i<=100) => true
會一直重複...但 continue 是可以跳過迴圈這圈的，但在這個範例中成為無窮迴圈。

---

例如我只要印出 1 ~ 101 中的 i++ 偶數行:

    var i = 1
    
    do {
      console.log(i)
      i++  // 如果是 i-- 會變成無窮迴圈。
      if (i%2 === 1) {  
        continue  // 會跑到下一圈，而讓基數被 console.log('i++', i) 忽略掉， 使基數不會印出 i++ ;
      }
      console.log('i++', i)  
    } while(i<=100)
    
    console.log('i=', i) // 'i=' 會等於 'i:'
    // 偶數會印出 i++ 的字串。
宣告變數後開始跑，跑到 `while` 看到條件 `i<=100` ， 如果值還是 <=100 就接著跳回 `do` ， 然後一直做下去直到值超過 101 ; 同時 `if (i%2 === 1) {` 會跑到下一圈，而讓基數被 console.log('i++', i) 忽略掉， 使基數不會印出 i++ ， 在下行有 `continue` 的情況就會跳出這段迴圈使偶數印出 i++ ; 如果給 `if (i <=10)` 就會變成 1 到 10 都不會印出 i++ ; 而給 `if (i>=1)` 和 `if (i <=1000)` 就會跟第二種情況一樣直到 印出 101 才停。

---

而突然終止迴圈的情況:

    var i = 1
    
    do {
      console.log(i)
      i++
      if (i <=1000) {
        break
      }
      console.log('i++', i)  // 這行沒有起到作用;
    } while(i<=100)
    
    console.log('i=', i)
    // 會印出 1 且下行是 i= 2 。
    
因為一開始宣告 i= 1 ， 往下就印出 1 ，因此繼續執行 i++ 時，值為 2 ， 而接著往下執行 `if (i <=1000) {` 則發現因為值 <=1000 ， 因此到 break 就終止了，最後往下執行印出 i= 2 。

---

## 4. 而在瀏覽器的執行環境場合
要看場合的方法:

    <script>
      debugger  
      var i = 1
      do {
        console.log(i)
        i++
      } while(i<=100)
      console.log('i=', i)
      </script>
用瀏覽器開啟存下上面這行文字的 html 格式檔案，開發人員選項中可以看到 sources 
debugger 偵錯模式:按下 F5 會在 Chrome 中停在 debugger 行， 按下 step 或是 F9 會繼續往下; 如果按下 Watch 輸入 i ， Enter 後會看到 i 的數值，用這個可以檢查程式的問題; 也能在每行設中斷點，再按下 F8 或是 Resume script execution 就會停在中斷點:

![](https://i.imgur.com/XA1KboO.png)

---

## 5. 擺脫輪迴 while
do...while...的使用情況是先做某件事情，最後到 while 判斷條件:

    var i = 1
    
    do {
      console.log(i)
      i++
    } while(i<=100)

    console.log('i=', i)
    // 印到 101 為止。
在某些 check 覺得第一次一定要做的場合會用到 do...while... 。

---

而只用 while 的情況就會變成先判斷條件，和執行區塊:

    var i = 1
    
    while(i<=100) {    // 如果條件設定成 true ， 就會變成無窮迴圈
      console.log(i)  
      i++
    }
    
    console.log('i=', i)
    // 跟 do...while... 一樣印到 101 為止。
    // 如果再更精簡可以變成:
    
    var i = 1
    
    while(i<=100) {
      console.log(i++)  // 記得 i++ 會先賦與自身變數後再計算
      // 如果這邊放 break 就只會跑一圈。
    }
    
    console.log('i=', i)
先賦與 1 給變數 i
執行 while(條件) 後看區塊
印出 變數 i 
算出 i = i+ 1
印出字串 和經過 i++ 的變數 i
回到 while 直到條件 i 超過 100

---

## 6. 最常用的大魔王 for lop 

### 一般迴圈常見的形式
我們想要特定範圍內的數字或東西，如:

1...100
a...b

---
### do...while...

    var i = 1  // 初始值;
    
    console.log(i)
    
    do { 
      console.log(i++)  // i 每圈要做的事情
    } while(i<=100) {  // 終止條件;
      console.log('i=', i)
    }
    
    // while 的場合:
    
    var i = 1  // 初始值;
    
    console.log(i)
    
    while(i<=100) {  // 終止條件;
      console.log(i++) // i 每圈要做的事情
    }  
      console.log('i=', i)
迴圈三要素: 初始值、每圈的 to do list 、 終止條件。

### 而 for loop 其實是用一個不同的語法來做這三要素
會用在你已經知道有多少圈的情況下，結構如下:

    for (初始值; 終止條件; i 每圈要做的事情) {    // ; 表示這行結束;
    
    }
    
---
先寫結構語法比較不會出錯:

    for (var i = 1; i<=100; i++) {
      console.log(i)
    }
    // 會跑到 100 停下來。

實際上是這樣跑 ↓
var i = 1 ;
檢查 (i<=100) { 如果條件 i 是 <=100 ， 繼續執行迴圈;
console.log(i) ;
i++ ， 即 i+=1 } ;

回到 console.log(i) ;
一直往下跑;
直到檢查 (i<=100) { 如果條件 i 是超過 <=100 } ， 終止執行迴圈。

---

### 如果是為了休息一下 for break 的場合:

    for (var i = 1; i<=5; i++) {
      if (i===3) break
      console.log(i)
    }
    // 會只印出 1 2 然後就跳掉。

var i = 1 ;
檢查 { 如果條件 i 是 <=5 ， 繼續執行迴圈;
if (i嚴格相等3) 終止
console.log(i) ;
i++ ， 即 i+=1 } ;

回到 console.log(i) ;
一直往下跑;
直到檢查 { 如果條件 i ===3 } ， 終止執行迴圈。

### 如果是為了接關 for continue 的場合:
    
    for(var i =1; i<=5; i++) {
      if (i===3) continue
      console.log(i)
    } // 會除了 3 不印出來外，印出 1245 。

var i = 1 ;
檢查 { 如果條件 i 是 <=5 ， 繼續執行迴圈;
if (i嚴格相等3) 當前的值不要，然後繼續接關執行迴圈;
console.log(i) ;
i++ ， 即 i+=1 } ;

回到 console.log(i) ;
一直往下跑;
直到檢查 { 如果條件 i 的值超過 5 } ， 終止執行迴圈。

### 初始新手教學關可以跳過，但之後的關卡可不能
初始值可以跳過，但還是要寫在外面這樣:
    
    var i = 1
    for(; i<=10; i++) {
      if (i%2) continue
      console.log(i)
    }  // 因為不要奇數，所以印出 246810 。

---

### 如果搬家請大聲說出想要箱子
可以搭配陣列 [ ] 的用法:

    var numbers = [1,2,3,4,5]
    
    for (var i=0; i<=4; i++) {
      console.log(numbers[i])
    }
因為陣列的起始值，也就是第一位是 0 ， 而陣列 [ ] 中只有 5 個數值，因此 i 是設置 4 ， 而如果 i<= 5 的情況則會多出一個未定義在陣列的值。

而也可以這樣用:

    var numbers = [1, 2, 3, 4, 5]
    
    for (var i=0; i<5; i++) {
      console.log(numbers[i])
    }
    // 使用小於 < 的情況，亦或是下式:
    var numbers = [1, 2, 3, 4, 5]
    
    for (var i=0; i<numbers.length; i++) {
      console.log(numbers[i])
    }

### 眾志成城，即是人海優勢
可以應用在總和的算法:

    var numbers = [1, 2, 3, 4, 5]
    var sum = 0
    for (var i=0; i<numbers.length; i++) {
      sum += numbers[i]
    }
    console.log(sum)

### 大家都是箱子的好朋友
陣列 [ ] 也可以跟 while 混用算出總和:
    
    var numbers = [1, 2, 3, 4, 5]
    var sum = 0
    var i = 0
    while(i<numbers.length) {
      sum += numbers[i]
      i++
    }
    console.log(sum)
迴圈是要一步一步，一行一行檢查~

---
自己try 這樣會印出五排的陣列:

    var numbers = [1, 2, 3, 4, 5]
    var sum = 0
    for (var i=0; i<numbers.length; i++) {
      sum += numbers[i]
      console.log(numbers) // 會印出陣列內數字
    }

---

自己在 try 印出奇數的情況:

    for (var i = 1; i<=100; i++) {
 	  console.log(i)
 	  console.log(i<=100)  
      console.log(i++)
      
    }
      console.log('i=', i)

會先給 i 這個值，一開始是 1 ; 判斷 i 是不是 <=100 ; 先賦與自身變數再計算 +1 所以這時候是 2 ;
印出 i 值，一開始是 1 ;
接著判斷條件是 true;
印出 i++ ，因一開始先賦與自身變數所以是 1 ，但由於面有執行到 i++ 值已是 +2 ， 而這邊再一個 i++ 所以變成 3 ;

因前一動計算會先給 i 這個值經過兩次 i++ 因此是 3 ; 判斷 i 是不是 <=100 ; 先賦自身變數再計算+1 ， 這時為 4 ; 
印出上面經過兩次 i++ 的值 3 ;
接著判斷條件是 true;
印出 i++ ，因前一動計算會先給 i ，而 i++ 先賦與自身變數所以 i 是 3 ，但由於面有執行到 i++ 值已是 4 ， 而這邊再一個 i++ +1 所以值會成 5 ;

自己在 try 印出偶數的情況:

    for (var i = 1; i<=100; ++i) {
 	  console.log(i)
 	  console.log(i<=100)  
      console.log(++i)
      
    }
      console.log('i=', i)

會先給 i 這個值，一開始是 1 ; 判斷 i 是不是 <=100 ; 先計算再賦與自身變數 +1 所以這時候是 2 ;
印出 i 值，一開始是 1 ;
接著判斷條件是 true;
印出 i++ ，因先計算再賦與自身變數所以是 2 ，由於面有執行到 ++i 值已是 +2 ， 而這邊再一個 ++i 所以變成+3 ;

因前一動先計算再給 i 這個值經過兩次 ++i 因此是 3 ; 判斷 i 是不是 <=100 ; 先計算再賦與自身變數 +1 ， 這時為 4 ;
印出上面經過兩次 ++i 的值 3 ;
接著判斷條件是 true;
印出 ++i ，因前一動先計算再給 i ，而 ++i 先計算再賦與自身變數所以 i 是 4 ，但由於面有執行到 i++ 值已是 5 ;



