# 二十三、 綜合練習 Lv1
###### tags: `JavaScript` `JS101` `2020七月第三週` `進度筆記` `Lidemy心得` `7/14`

---
## 練習一:請你分別用 for loop 以及 while 迴圈，印出 1~9。
    for(var i = 1; i<=9; i++) {
	    console.log(i)
    }

    var i = 1

    console.log(i)

    do {
      console.log(i++)
    } while(i<=9) {
      console.log('i:', i)
    }

---

## 練習二：寫一個能夠印出 1~n 的函式

    function print(n) {
      for (var i=1; i<=n; i++) {
        console.log(i)
          }
        }
        print(1)
    // 會印出 1  


    function print(n) {
      for (var i=1; i<=n; i++) {
        console.log(i)
          }
        }
        print(3)
    // 會印出 1 到 3 (隔行)。

    function print(n) {
      for (var i=1; i<=n; i++) {
        console.log(i)
          }
        }
        print(9)
    // 會印出 1 到 9 (隔行)。
---
## 練習三：寫一個能夠印出 n 個 * 的函式 

    function star(n) {
	  var result = ""
      for (var i=1; i<=n; i++) {
        result = "*"
        console.log(result)
          }
    }
    star(1)


    function star(n) {
      var result = ""
      for (var i=1; i<=n; i++) {
        result = "*"
        console.log(result)
          }
     }
     star(5)
    
    function star(n) {
	  var result = ""
      for (var i=1; i<=n; i++) {
        result = "*"
        console.log(result)
      }
    }
    star(10)
    
---

## 練習四：寫一個能回傳 n 個 * 的函式 

star(1) 會回傳 *
star(5) 會回傳 *****

所以 console.log(star(5)) 的預期輸出是：
***** 
    
    function star(n) {
      var result = ''
      for (var i = 1; i<5; i++) {
      result = '*'
      console.log(result)	
      }
      return result
    }   
    console.log(star(5))
---

## 練習五：判斷大小寫

請寫一個叫做 isUpperCase 的 functuon，並且接收一個字串，
回傳這個字串的第一個字母是否為大寫。

isUpperCase("abcd") 正確回傳值：false

isUpperCase("Abcd") 正確回傳值：true

isUpperCase("ABCD") 正確回傳值：true

isUpperCase("aBCD") 正確回傳值：false 


    var isUpperCase = "abcd"
    console.log(isUpperCase >= 'A' && isUpperCase <= 'Z')

    var isUpperCase = "Abcd"
    console.log(isUpperCase >= 'A' && isUpperCase <= 'Z')

    var isUpperCase = "ABCD"
    console.log(isUpperCase >= 'A' && isUpperCase <= 'Z')

    var isUpperCase = "aBCD"
    console.log(isUpperCase >= 'A' && isUpperCase <= 'Z')

---
## 練習六：回傳第一個大寫字母以及它的 index

請寫一個 function position，接收一個字串並回傳這個字串裡面的第一個大寫字母跟它的 index，若沒有則回傳 -1。

position("abcd") 正確回傳值：-1

position("AbcD") 正確回傳值：A 0

position("abCD") 正確回傳值：C 2

        
    function position(str) {  
      var indexOfLetter = []  
      var from = 'A'.charCodeAt(0)  // 可以找字母，從 A 找到 Z ;
      var to = 'Z'.charCodeAt(0)
      for(var i=from; i<=to; i++) {
  	    var char = String.fromCharCode(i)
  	    indexOfLetter.push({
  		    char: char,
  		    index: str.indexOf(char)
  	    })
      }

      indexOfLetter.sort(function(a, b) { 
  	    return a.index -b.index  // A 到 Z 數字的排序;
      })

      indexOfLetter = indexOfLetter.filter(function(item) { // 回傳 . push 後的 obj ;
  	    return item.index >=0  // 找不是 -1 的數字，留下 >= 0 ;

      })

      if (indexOfLetter.length ===0) {
  	    return -1  // 如果沒有任何大寫字母，因此回傳 -1 ;
      }

      return indexOfLetter[0].char + ' ' + indexOfLetter[0].index
       // 如果有大寫字母就回傳;
    }

    var a = position('abcd')
    console.log(a)

// 比較簡單的寫法，從第一個字開始找，找到大寫後就回傳

    function position(str) {
	    for (var i = 0; i<str.length; i++) {
		    console.log(str[i])
		    if (str[i] >='A' && str[i] <='Z') { // 代表大寫字母;
			    return str[i] + ' '+ i // i 表示 index; 
		    }
	    }
	    return -1
	    // 整個迴圈跑完後看字串沒有大寫字母就回傳 -1 ， 有的話就照大寫字母順序回傳順位 0, 1, 2... ;
    }

    var a = position('abcd')
    console.log(a)

---

## 練習七：回傳陣列裡面所有小於 n 的數的數量

請寫出一個函式 findSmallCount，接收一個陣列跟一個數字 n，回傳有多少個數小於 n。

findSmallCount([1, 2, 3], 2) 預期回傳值：1

findSmallCount([1, 2, 3, 4, 5], 0) 預期回傳值：0

findSmallCount([1, 2, 3, 4], 100) 預期回傳值：4

    // 找出最小值後印出第一個數字

    function findSmallCount(arr, n) {
	    var counter = 0
	    for(var i=0; i<arr.length; i++) {
		    if (arr[i] < n) counter++

	    }
	    return counter
    }

    console.log(findSmallCount([1, 2, 3], 2))
    console.log(findSmallCount([1, 2, 3, 4, 5], 0))
    console.log(findSmallCount([1, 2, 3, 4], 100))


    function findSmallCount(arr, n) {
	    return arr.filter(function(item) {
		    return item < n
	    }).length
    }

    console.log(findSmallCount([1, 2, 3], 2))
    console.log(findSmallCount([1, 2, 3, 4, 5], 0))
    console.log(findSmallCount([1, 2, 3, 4], 100))

---

## 練習八：回傳陣列裡面所有小於 n 的數的總和

請寫一個函式 findSmallerTotal，接收一個陣列以及數字 n，回傳陣列裡面所有小於 n 的數的總和。

findSmallerTotal([1, 2, 3], 3) 正確回傳值：3

findSmallerTotal([1, 2, 3], 1) 正確回傳值：0

findSmallerTotal([3, 2, 5, 8, 7], 999) 正確回傳值：25

findSmallerTotal([3, 2, 5, 8, 7], 0) 正確回傳值：0


    function findSmallerTotal(arr, n) {
	    var sum = 0
	    for(var i=0; i<arr.length; i++) {
		    if (arr[i] < n) sum+=arr[i]
	    }
	    return sum
    }

    console.log(findSmallerTotal([1, 2, 3], 3))
    console.log(findSmallerTotal([1, 2, 3], 1))
    console.log(findSmallerTotal([3, 2, 5, 8, 7], 999))
	console.log(findSmallerTotal([3, 2, 5, 8, 7], 0))
    
---


## 練習九：回傳陣列裡面所有小於 n 的數 
請寫一個函式 findAllSmall，接收一個陣列跟一個數字 n，回傳一個裡面有所有小於 n 的數的陣列（需按照原陣列順序）。

findAllSmall([1, 2, 3], 10) 正確回傳值：[1, 2, 3]

findAllSmall([1, 2, 3], 2) 正確回傳值：[1]

findAllSmall([1, 3, 5, 4, 2], 4) 正確回傳值：[1, 3, 2]

// 也可以用 .filter

    function findAllSmall(arr, n) {
	    var small = []  
	    for(var i=0; i<arr.length; i++) {
		    if (arr[i] < n) {
		      small.push(arr[i])
	        }
	    }
	    return small
    }

    console.log(findAllSmall([1, 2, 3], 10))
    console.log(findAllSmall([1, 2, 3], 2))
    console.log(findAllSmall([1, 3, 5, 4, 2], 4))
    
---

## 練習十：回傳陣列總和

請寫一個 function sum，接收一個陣列並回傳陣列中數字的總和。

sum([1, 2, 3]) 預期回傳值：6

sum([-1, 1, 2, -2, 3, -3]) 預期回傳值：0

accumulator 的初始值會是陣列的第一個元素，詳情可參考 [MDN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

	function sum(arr) {
		var ans = 0  
		for(var i=0; i<arr.length; i++) {
			ans += arr[i]
		}
		return ans
	}

	console.log(sum([1, 2, 3]))
	console.log(sum([-1, 1, 2, -2, 3, -3]))

---
### `.reduce`

用 array 的時候背後通常有參數，就是現在的 value 和 index ，
會是:

    function(accumulator, currentValue) {
	return currentValue + accumulator
    }  
表示跑迴圈時，我對第一個元素用的時候，我回傳我現在的元素 + 累積起來的值，因此跑完後會累積起來成為總和。

    [1, 2, 3].reduce(sum)

對 1 執行函數時 accumulator 是 null ， currentValue 是 1   

return currentValue + accumulator 會是 1 。

對第二圈開始跑的時候，對 2 執行函數時 accumulator 是 1 ， currentValue 是 2   

return currentValue + accumulator 會是 3 。

第三圈開始跑的時候，對 3 執行函數時 accumulator 是 3， currentValue 是 3  

return currentValue + accumulator 會是 6 。

範例:

	function sum(arr) {
	  return arr.reduce(function(accumulator, value) {
	  	// reduce 有點像是把 ans 的值放到 accumulator 的位置;
	  	return accumulator + value
	  }, 10)  // 10 是初始值;
	}
	console.log(sum([1, 2, 3]))
	console.log(sum([-1, 1, 2, -2, 3, -3]))
加上初始值跑出來就是 10 跟 16 。

也可以這樣，跑出 total 的值:

	function sum(arr) {
	  return arr.reduce(function(total, value) {
	    return total + value
	  })
	}
	console.log(sum([1, 2, 3]))
	console.log(sum([-1, 1, 2, -2, 3, -3]))
其想要把第一個參數存起來變成可以記得的狀態。

變種:

	console.log(
	  [1, 2, 3].reduce(
	  	function(obj, value) {
	      obj['a'+value] = value
	      return obj
	    }, {}
	  )
    )

--

### 用 `.map` 也行

	function sum(arr) {
	  var ans = 0
	  arr.map(function(value) {
	  	ans = ans + value
	  	return value
	  })
	  return ans
	}
	console.log(sum([1, 2, 3]))
	console.log(sum([-1, 1, 2, -2, 3, -3]))

###  還有 `.forEach` 跑每個元素
但他不用 return 值回來:


	function sum(arr) {
	  var ans = 0
	  arr.forEach(function(value) {
	  	ans = ans + value
	  	return value
	  })
	  return ans
	}
	console.log(sum([1, 2, 3]))
	console.log(sum([-1, 1, 2, -2, 3, -3]))
