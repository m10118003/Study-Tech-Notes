# 零、 ALG 熟練程式語法和思維
###### tags:  `ALG 101` `JavaScript` `2020七月第三週` `進度筆記` `Lidemy心得` `7/15`

---
## 重點:

1. 學習並熟練程式基礎語法（變數、陣列、判斷式、迴圈以及函式） 。
2. 學習並熟練程式的思維方式。

## 目標是學會如何解題，培養觀念。
課綱:

Unit1 : 學程式，從不要寫程式開始。
Unit2 : 學會看程式。
Unit3 : 看懂題目。

## 基礎練習。

Unit4 : 實戰。
Unit5 : 練習經典題型。
Unit6 : 熟練內建函式。
Unit7 : 複習國中數學題。

## 未來

Unit8 : 拿分方式，困難題解題。
Unit9 : 未來學習。

目標為上完後，會覺得 LidemyOJ 八成的題型很簡單。

# 一、 ALG 課程須知
###### tags: `JavaScript` `ALG 101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/15`

---

1. 已有程式語言基礎。
2. 寫 leetcode 障礙。
3. 寫不出九九乘法表。

---

## 為何要上這堂課 ?

需要熟悉基礎，再來是 leetcode 、 程式架構。

---

## 先想題，再看實戰。

課程進行方式：

1. 觀看課程影片學習
2. 觀看課程影片實戰內容
3. 寫作業（Project）練習
4. 觀看課程檢討影片
5. 複習作業

---

# 二、 Projec : 0
###### tags: `JavaScript` `ALG 101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/15`

[教學影片](https://www.youtube.com/watch?v=v7zv1ixaO3M)

線上解題系統: Online Judeg System
1. 不會跟你講 code 哪裡有寫錯。
2. 有部分 code 錯誤。

分為實作 function (leetcode) 和檔案 I/O (LIOJ) 。
leetcode 適用 return 來輸出。
LIOJ 需要從標準輸入去讀取輸入 (input) ， 然後用 `console.log` 來輸出。

---

## LIOJ 上 JavaScript 讀取輸入方式

readline 的 library 用法:

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情;
      console.log('input:', line)
    }); 

使用者輸入資料就會被拿出來了:

![](https://i.imgur.com/zQI276q.png)

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情，拿到每行資料;
      console.log('input:', line)
    }); 

    rl.on('close', function() {
    	console.log('close')
    	// 程式直接關掉: 這時按下 Ctrl+C 會把程式整個終止。
    	// 資料輸入結束為 Ctrl+D (mac OS) 送出程式結尾，會顯示 close 。
    })
    

---

存取每一行新資料的方法:

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    var lines = []
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情，拿到每行資料;
      lines.push(line)  // 把每一行資料都 push 進去  rl.on('line', function (line) { 的陣列內;
    }); 

    rl.on('close', function() {
    	console.log(lines)
    	// 程式直接關掉: 這時按下 Ctrl+C 會把程式整個終止。
    	// 資料輸入結束為 Ctrl+D (mac OS) 送出程式結尾，會顯示 close 。
        // 這時候因為每一行資料都 push 進去 ， close 時就會有全部資料;
    })
    
---

## solve() 

拿到所有資料的方法:

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    var lines = []
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情，拿到每行資料;
      lines.push(line)  // 把每一行資料都 push 進去  rl.on('line', function (line) { 的陣列內;
    }); 

    rl.on('close', function() {
    	solve(lines)
    	// 程式直接關掉: 這時按下 Ctrl+C 會把程式整個終止。
    	// 資料輸入結束為 Ctrl+D (mac OS) 送出程式結尾，會顯示 close 。
        // 這時候因為每一行資料都 push 進去 ， close 時就會有全部資料;
    })
    
    finction solve(lines) {
    // 在 solve 內拿到所有資料;
    }

看成是一個幫助讀取輸入的位置，這樣好處是動 `solve()` 這一行 `finction solve(lines) {` 函式的地方就可以了，這是實際上解題的程式碼會放的位置。

---

## 如何測試 ?

### A+B 
實際上只有一行資料
輸入 1 2  然後輸出 3
這是直接執行的方式:

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    var lines = []
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情，拿到每行資料;
      lines.push(line)  // 把每一行資料都 push 進去  rl.on('line', function (line) { 的陣列內;
    }); 

    rl.on('close', function() {
      solve(lines)
    	// 程式直接關掉: 這時按下 Ctrl+C 會把程式整個終止。
    	// 資料輸入結束為 Ctrl+D (mac OS) 送出程式結尾，會顯示 close 。
        // 這時候因為每一行資料都 push 進去 ， close 時就會有全部資料;
    })

    function solve(lines) {
    // 在 solve 內拿到所有資料;
      var line = lines[0]  // line 的每一行都是字串; 這是第一行， 12 ;
      var temp = line.split(' ')  // 隔開 1 2 的空白;
      console.log(Number(temp[0]) + Number(temp[1]))  // 把 1+2 輸出為 3 ; 
    }
    
第一種測試範例，直接在 CLI 上執行上面的程式碼 `node name.js` name 為你存上述程式碼為 .js 的檔名:

![](https://i.imgur.com/03XnYQn.png)

3 表示輸出

第二種是呼叫函式的測試:

    var readline = require('readline');
    var rl = readline.createInterface({
      input: process.stdin // 標準輸入;
    });
    
    var lines = []
    
    rl.on('line', function (line) {
    // 當使用者輸入一行資料時要做的事情，拿到每行資料;
      lines.push(line)  // 把每一行資料都 push 進去  rl.on('line', function (line) { 的陣列內;
    }); 

    rl.on('close', function() {
      solve(lines)
    	// 程式直接關掉: 這時按下 Ctrl+C 會把程式整個終止。
    	// 資料輸入結束為 Ctrl+D (mac OS) 送出程式結尾，會顯示 close 。
        // 這時候因為每一行資料都 push 進去 ， close 時就會有全部資料;
    })

    function solve(lines) {
    // 在 solve 內拿到所有資料;
      var line = lines[0]  // line 的每一行都是字串; 這是第一行， 12 ;
      var temp = line.split(' ')  // 隔開 1 2 的空白;
      console.log(Number(temp[0]) + Number(temp[1]))  // 把 1+2 輸出為 3 ; 
    }
    
    solve([
    '1 2'
    ])
    
會印出 3 ; 表示程式碼是對的。

---

第三種是新增檔案來表示的執行方式:
比較推薦的方式。

先新增 sublime 檔案，裡面放輸入 1 2 如下圖:

![](https://i.imgur.com/GHF0OmH.png)

用 CLI 指令 `cat name.js` 印出檔案內容，再用 `|` 把前面指令的輸出轉到後面指令的輸入為:

`cat name.js | node name.js`

使用 Windows git-bash 會發生 | 指令出錯的情況
假設原本示範的是：`cat input.txt | node code.js`
可以改用：`cat input.txt | command node code.js` 或是  
`cat inptu.txt | env node code.js`

好處是只要更改檔案，跑指令就可以確定答案是不是對的。

__note__ 如果要使用轉 .txt 檔案 | 成 node 輸出，記得要把程式碼寫在 `function {}` 內:
```
var readline = require('readline');
var rl = readline.createInterface({
  input: process.stdin
});

var lines = []

// 讀取到一行，先把這一行加進去 lines 陣列，最後再一起處理
rl.on('line', function (line) {
  lines.push(line)
});

// 輸入結束，開始針對 lines 做處理
rl.on('close', function() {
  solve(lines)
})

// 上面都不用管，只需要完成這個 function 就好，可以透過 lines[i] 拿取內容
function solve(lines) {
// 程式碼寫在這。
}
```
