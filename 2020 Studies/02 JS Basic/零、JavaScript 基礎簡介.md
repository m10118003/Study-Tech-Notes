# 零、JavaScript 基礎簡介
###### tags: `JavaScript` `2020六月第五週` `進度筆記` `Lidemy心得`

詳細內容在 JS101 。

---

1. `console.log()` : 可以把 "(  )" 寫在 js 檔案的訊息印出來，表示輸出的意思，括號內也可以放條件 。

        if (70 > 60) {
          console.log('及格了')
        }    
    
如果設定條件 ， 就可以使 70 分 > 60 分的條件成立 ， 並印出及格了 。

---

2. 設定宣告 (var) 和變數 (score):

              //賦值
        var score = 70
        if (score >= 60) {
          console.log('及格了')
        }
    
         if (score < 60){
           console.log('不及格')
        }
       
宣告 70 賦予給 score ， "=": 表示賦值， "{}": 表示區塊 ， 先判斷宣告再判斷 第一個和第二個 if 。

---

3. `if` & `else`: 寫了很多個 if 可能會很冗長，因此可以縮短，如 ↓

              //賦值
        var score = 50
        if (score >= 60) {
          console.log('及格了')
        } else {
          console.log('不及格')
        }
        
如果符合 >= 則進到 "及格了" ， 如果不符合就到 "不及格" 。

---

4. 給一點變形式:

              //賦值
        var score = 50
        if (score >= 80) {
          console.log('你好棒')
        } else if (score >=60) {
          console.log('及格')
        } else {
          console.log('不及格')
        }
        
宣告 50 賦予 score ，"如果" >= 80 印出你好棒，但 "否則" "如果" >= 60 印出及格，"否則" 印出不及格。

----

5. 陣列:

              //賦值
              // Array 陣列
        var scores = [80, 90, 100, 60, 50]
        console.log(scores)
        if (scores >= 80) {
          console.log('你好棒')
        } else if (scores >=60) {
          console.log('及格')
        } else {
          console.log('不及格')
        }
        
"[]": 陣列中可以包含很多個數字；如要取陣列內的某個元素，程式語言第一個以 0 作為表示，表示 "索引" 以 0 作表示:


              //賦值
              // Array 陣列
        var scores = [80, 90, 100, 60, 50]
        console.log(scores[0])

則會印出索引 "[0]" 為第一位要的第 1 個相關數字即 80；"[1]" 則表示第二位 90； "[2]" 第三位為100。

---------------

6. 列出所有元素 `.length`:

              //賦值
              // Array 陣列
        var scores = [80, 90, 100, 60, 50]
        console.log(scores.length) // scores[0] ~ scores[scores.lenght -1]

表示可以列出所有元素，存取範圍為 0 到 scores.lenght -1；如果重複要判斷很多個數字就會變成:

        var scores = [60, 80, 30, 70, 50]
        console.log(scores)
        
        if (scores[0] >= 80) {
          console.log('你好棒')
        } else if (scores >=60) {
          console.log('及格')
        } else {
          console.log('不及格')
        }
                
        if (scores[1] >= 80) {
          console.log('你好棒')
        } else if (scores >=60) {
          console.log('及格')
        } else {
          console.log('不及格')
        }
                       
        if (scores[2] >= 80) {
          console.log('你好棒')
        } else if (scores >=60) {
          console.log('及格')
        } else {
          console.log('不及格')
        }
        
但這樣就會太冗長，因為 scores[] 中都是重複的，所以就有了迴圈。

---

7. 迴圈 `for` : 

        for (var i=0; i<=4; i++) {
        
        }

需要設定: 會先執行起始條件 "i=..."，然後檢查是否符合終止條件 "i<=..."，再執行每圈要做的事情 "i++"，然後再判斷終止條件一直持續到不符合就跳出去:

    var scores = [60, 80, 30, 70, 50]
    console.log(scores)



    for (var i=0; i<=scores.length - 1; i++) 
      if (scores[i] >= 80) {
        console.log('你好棒')
      } else if (scores[i] >= 60) {
        console.log('及格') 
      } else {
        console.log('不及格')
      }

如此就可以判斷陣列中所有的分數是否及格。

---

8. `function` 功能，後面接"( )"可以用來傳參數

       function getRating(scores) {
	     console.log('scores!', scores)
       }
       
       getRating(60)
    
我呼叫 grtRating 並且把 60 這個參數代進去 scores，使 60 變成變數。
如果給點變形:

    function getRating(scores) {
      if (scores >= 80) {
        console.log('你好棒')
      } else if (scores >= 60) {
        console.log('及格') 
      } else {
        console.log('不及格')
      }
    }     
    getRating(60)
    
這樣就會顯示 60 分為及格。
如果拿來判斷所有分數:

    var scores = [60, 80, 30, 70, 50]
    console.log(scores)



    for (var i=0; i<=scores.length - 1; i++) {
      getRating(scores[i])
    }
      
    function getRating(scores) {
      if (scores >= 80) {
        console.log('你好棒')
      } else if (scores >= 60) {
        console.log('及格') 
      } else {
        console.log('不及格')
      }
    }     
    getRating(60)
    
跑第一圈就會把 60 丟進去 scores 判斷是否符合。

----

9. `return` 也可以等於，表示回傳值:

       y = f(x)
       function x () {
         return 123
       }
       
表示執行完 function 的結果是 123 ，回傳完後 funct 就會停止運作，一個 function 只會回傳第一次執行 return 的結果:

    var scores = [60, 80, 30, 70, 50]
    return(scores)



    for (var i=0; i<=scores.length - 1; i++) {
      getRating(scores[i])
    }
      
    function getRating(scores) {
      if (scores >= 80) {
        return('你好棒')
      } else if (scores >= 60) {
        return('及格') 
      } else {
        return('不及格')
      }
    }     
    getRating(60)

但如果直接跑是不會有結果，因為一定要有 `console.log` 才會有輸出:

![](https://i.imgur.com/kwNar3f.png)

因此要 "宣告" t 這個變數， 並把 (scores[i]) 給 getRating 再 "賦予" 給 t ， 
再用 console.log 印出 t 這個值:

    var scores = [60, 80, 30, 70, 50]
 



    for (var i=0; i<=scores.length - 1; i++) {
      var t = getRating(scores[i])
      console.log(t)
    }
      
    function getRating(scores) {
      if (scores >= 80) {
        return('你好棒')
      } else if (scores >= 60) {
        return('及格') 
      } else {
        return('不及格')
      }
    }     
    getRating(60)

---

code war 不看 console.log 輸出(因為不是在 CLI) ， 而是看 return 回傳值。
而 Lidemy.OJ 是根據最後的輸出來看答案對不對。