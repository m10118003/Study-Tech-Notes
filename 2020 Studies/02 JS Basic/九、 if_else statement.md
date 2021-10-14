# 九、 `if/else` statement 
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得` `7/4`

---

## `if` 的基礎形式
基礎判斷式:

    if () {    // ( )接條件; { } 為區塊 (block)
               // 縮排有區塊的感覺
    }
    
---

## 條件設成 true or false:

    if (true) {
    console.log(123)    
    }
    
    // 條件為 true 印出 123; 

    if (false) {
    console.log(123)    
    }
    
    // 條件為 false 不會印出 。

---

## 也可以與變數合用:
如果我要設定 60 分為及格，而有學生是 70分的話:

    var score = 70
    if (score >= 50) {
      console.log('pass')
    }
    // 會印出 pass
    
那如果設定了 3 個條件的話:

    var score = 65
    if (70 >= score >= 60) {
      console.log('pass')
    }
    // 如果設定 3 個條件，因為 ( ) 內是從左作到右，所以會先判斷 70 >= score ， 因此沒 pass 不會印出。
    
多個條件要用 && 、 || :    

	var score = 65
    if (70 >= score <= 60) {
      console.log('pass')
    }
    // 其實這樣可以印出，而用邏輯運算的成分則是:

    var score = 65
    if (score >= 60 && score <= 70) {    // >= 和 <= 同時只能用一組在一個條件 ( ) 內，如果要用多組要用到邏輯運算;
      console.log('pass')
    }
    // 這樣會印出 pass 。

## `else` 的使用方式
`else` 基礎形式:

    if (){    // 區塊 1 { };
      
      } else {    // 區塊 2 { } ， else {} 可以在第一個區塊 {} 的下一行縮排; 
    
    }

用到 else 的情況，如果是 59 分:

    var score = 59
    if (score >= 60) {    // 這一行也有這種寫法 if (score >= 60 == true){ ; 不過，如果 score >= 60 已經是 true 的情況後面可以不用使用一般相等 ==; 
      console.log('pass')    // 這行條件判斷完不是 60 分才會到下個區塊;
    } else {
      console.log('false')   // 'false' 字串可以置換，如 'undefined'
    }
    // 就會印出 false 。
    
## 簡單範例
今年如果可以撿到 5 倍的鑽石，我撿了 10 顆:

    var number = 10
    if (number % 2 === 0) {    // 如果沒有嚴格檢查 === 0 ， 假設撿到 11 顆，會因為是基數而被判斷是 true ;
      console.log(' 5 倍的祝福 ')
    } else {                  // 如果上面沒嚴格檢查 ===0 ， 會變成不是基數，可以整除的情況才跑到這裡。
      console.log('*今年不是 5 倍嗎 ?*')
    }
    // 如果有設定 === ，因此 10 % 2 會產生 0 ， 答案會是 5 倍的祝福。
    
如果沒設定嚴格檢查，但我用 ! 反轉了:

    var number = 10
    if (!(number % 2)) {    // 如果沒有 ! ， 假設撿到 11 顆，會因為是基數而被判斷是 true 5 倍的祝福;
      console.log(' 5 倍的祝福 ')
    } else {                  // 如果上面沒 ! ， 會變成不是基數，可以整除的情況才跑到 false  *今年不是 5 倍嗎 ?*
      console.log('*今年不是 5 倍嗎 ?*')
    }
    // 如果有設定 === ，因此 10 % 2 會產生 0 ， 答案會是 5 倍的祝福。

因此 `if (!(number % 2)) {` 和 `if (number % 2 === 0) {` 是一樣的。

---

# 十、 `if` 和 `else` 的判斷不只兩種，還有小三 `else/if`

以區分年齡層為例，只用 if 的寫法:
    
    // 單行註解
    /*多行註解*/
    /* 
    age >= 65, old man;
    65 > age >= 20, young man;
    age < 20, youngster
    */
    
    var age = 70
    if (age >= 65) {
      console.log('old man')
    }
     if (65 > age && age >= 20) {
       console.log('young man')
     } if (age < 20) {
         console.log('youngster')
    }
   ![](https://i.imgur.com/dv52y53.png)

以區分年齡層為例，用 `if/else` 的寫法:

    var age = 70
    
    if (age >= 65) {        // age >= 65 的情況成立時，則印出 old man;
      console.log('old man')
    } else {
      if (age < 20) {       // age < 20 的情況則印出 youngster;
        console.log('youngster')
      } else {              // 除以上兩種情況外印出 young man 。  
        console.log('young man')
      }
    }
    
抑或者可以這樣寫:

    var age = 70
    
    if (age >= 65) {
      console.log('old man')
    } else {
      if (age >= 20) {
        console.log('young man')
      } else {
        console.log('youngster')
      }
    }

## 小三介入 ， else/if 
用 else/if 區別年齡層的作法:

    var age = 70
    
    if (age >= 65) {        // 如果年齡 >= 65 old man; 
      console.log('old man')
     } else if (age >= 20) { // 如果以上不成立，要再判斷 ( ) 內的條件;
       console.log('young man') 
      } else if (age < 20) {
        console.log('youngster')
     }
     // 則會印出 old man 。
     
如果更簡潔一點，去掉一個 else if ， 但最後要用 else 結尾:

    var age = 10
    
    if (age >= 65) {        // 如果年齡 >= 65 old man; 
      console.log('old man')
     } else if (age >= 20) { // 如果以上不成立，要再判斷 ( ) 內的條件;
       console.log('young man') 
      } else {
        console.log('youngster')
      }
      
小三 else if 可以有很多個:

    var age = 60
    
    if (age >= 60) {        // 如果年齡 >= 65 old man; 
      console.log('耳順的 old man')
     } else if (age >= 50) { // 如果以上不成立，會一直往下判斷 ( ) 內的條件;
       console.log('知天命')
       } else if (age >= 40) {
         console.log('40 不惑的壯年')
       } else if (age >= 30) {
       	 console.log('30 而立的 young man')
       } else if (age >= 20) {
         console.log('肝很新鮮的 young man')
       } else if (age >= 10){
         console.log('中二的 youngster')
       }
       // 可以依據條件來分得很細。

else if 會比純用 if 來得簡潔有力。

---

# 十一、 類似的判斷式 switch
如果寫月份的條件很多的時候，用 else if 會顯得很跟長貓一樣長:

    var month = 1
    
    if (month === 1) {
      console.log('Jan.')
    } else if (month === 2) {
      console.olg('Feb.')
    } else if (month === 3) {
      console.olg('Mar.')
    } else if (month === 4) {
      console.olg('Apr.')
    } else if (month === 5) {
      console.olg('May.')
    } else if (month === 6) {
      console.olg('Jun.')
    } 

## switch 的架構

常用在條件多的時候根據數字來輸出文字:

    switch(代入的參數){
        case '條件1':
            程式碼區塊
        break;
        
        case '條件2':
            程式碼區塊
        break;
        
        default:
            程式碼區塊
        break;
    }
    // 也可以合併 case :

    switch(代入的參數){
        case '條件1':
        case '條件2':
            程式碼區塊
        break;    
    
[參考來源:](https://ithelp.ithome.com.tw/articles/10211560)

因此用 else if 寫月份的情況可以修改成 switch :    

    var month = 1
    
    switch(month) {
      case 1:
      console.log('Jan.')
      break              // 如果沒有加 break 他就會把所有月分都執行一遍。
      case 2:
      console.log('Feb.')
      break
      case 3:
      console.log('Mar.')
      break
      case 4:
      console.log('Apr.')
      break
      case 5:
      console.log('May.')
      break
      case 6:
      console.log('Jun.')
    default:             // 如果輸入超過 6 的數字，會跳出這個值。
      console.log('沒有這個月份別喔')  
      
    } 

## 其實可以用陣列一次排開
用陣列 [ ] 也可以讓月份排排站，班長不用再晚點名囉:

    var months = 1
    var monthsInName = ['Jan.', 'Feb.', 'Mar.', 'Apr.', 'May.', 'Jun.']
    console.log(monthsInName[months - 1])

如果是變數和 switch 並用:

    var months = 1
    
    switch(months) {
      case 1:
      console.log('Jan.')
      break              // 如果沒有加 break 他就會把所有月分都執行一遍。
      case 2:
      console.log('Feb.')
      break
      case 3:
      console.log('Mar.')
      break
      case 4:
      console.log('Apr.')
      break
      case 5:
      console.log('May.')
      break
      case 6:
      console.log('Jun.')
    default:             // 如果輸入超過 6 的數字，會跳出這個值。
      console.log('沒有這個月份別喔')  
      
    } 
    
    var monthsInName = ['Jan.', 'Feb.', 'Mar.', 'Apr.', 'May.', 'Jun.']
    console.log(monthsInName[months - 1])
    
    // 這樣會印出 Jan. Jan. 

如果是 `lengths - 1` 這種比較適合單純的排法的條件。

## if/else 和 else if 的補充
假設分數 60 就會讓學分不被當掉是 true 的話:

    var score = 60
    var isPass = false
    
    if (score >= 60) {
      isPass = true    // 如果 score >= 60 跟 isPass一樣是 true;
    } else {
      isPass = false   // 抑或者是 score >= 60 的值跟 isPass 一樣是 false 的話; 
    }
    // 這式子不會印出東西，而且 if 的值如果跟 isPass 是一樣的話，可以縮短:
    
    var score = 60
    var isPass = score >= 60 // var isPass = (score >= 60) 可以括號。

---

# 十二、 三元運算子 ternary 像是 P 助 ? 小雞嘴 :
## 如果運用 : 在 if/else 
推薦三元運算在兩個條件的情況下使用。

    // 三元運算子範例語法是;
    
    condition ? exprIfTrue : exprIfFalse
    
    // 條件 ? (? 是固定用法) 如是 true 就回傳值 : 如是 false 就回傳值。
    
如果一個看似不可能作案的 100 分密室:

    var score = 100
    var message = ''
    
    if (score >= 100) {
      message = 'pass'    // 如果 score >= 100 跟 message 一樣是 pass;
    } else {
      mesage = 'fail'    // 如果 score >= 100 跟 message 一樣是 fail;
    }
    // 作案手法完美到不可能印出來。

讓偵探 ? : 派上用場吧:
 
    var score = 100
    var message = ''
    
    if (score >= 100) {
      message = 'pass'    // 如果 score >= 100 跟 message 一樣是 pass;
    } else {
      mesage = 'fail'    // 如果 score >= 100 跟 message 一樣是 fail;
    }
    // 作案手法 > 黃金比例 1.618 ? 
    
    console.log(100 > 1.618 ? '完美' : '有瑕疵' )
   
    // 會印出完美 。
    
如果用放大鏡看，可以更簡略:

    // 如果 score >= 100 跟 message 值一樣的話;

    var score = 100
    var message = score >= 100 ? '完美' : '瑕疵'
    console.log(message)
    
    // 會印出完美。

## 根據線索層層剝開蜂巢 !
三元運算子是可以在多於兩個條件的情況下使用，像是蜂巢狀:
        
    var score = 100
    var message = score >= 100 ? (score === 100 ? '如此完美' : '一流') : '瑕疵'
    console.log(message)
    
但會比較難讀出來。   

---

## 練習

    var score = 60
    var say = score >= 60 ? 'pass' : 'fail'
    console.log(say)
    
    
    var score = 60
    var say = score

    if (score >= 60){
      console.log('pass')
    } else {
      console.log('fail')
    }

## 進階練習
滿分 you are no1!

    var score = 100
    var say = score

    if (score === 100) {
      console.log('you are no1!')
    } else if (score >=60)
      console.log('pass')
    else {
      console.log('fail')
    }

        
    var score = 100
    var message = score >= 60 ? (score === 100 ? 'you are no1!' : 'pass') : 'fail'
    console.log(message)

---

BMI test:

    var bodyWeight = 150
    var height = 1.8
    var BMI = (bodyWeight/(height ** 2))
      console.log(BMI)

   	if (BMI < 18.5) {
   	  console.log('體重過輕')
   	} else if (18.5 <= BMI && BMI < 24) {
   	  console.log('正常範圍')
   	} else if (24 <= BMI && BMI < 27) {
   	  console.log('過重')
   	} else if (27 <= BMI && BMI < 30) {
   	  console.log('輕度肥胖')
   	} else if (30 <= BMI && BMI < 35) {
   	  console.log('中度肥胖') 
   	} else if (35 <= BMI) {
   	  console.log('重度肥胖')
   	}
    // switch 印不出 ''
    
    var bodyWeight = 70
    var height = 1.8
    var BMI = (bodyWeight/(height ** 2))
      console.log(BMI)

    switch(BMI) {
      case (BMI < 18.5):
      console.log('體重過輕')
      break
      case (18.5 <= BMI && BMI < 24):
      console.log('正常範圍')
      break
      case (24 <= BMI && BMI < 27):
      console.log('過重')
      break
      case (27 <= BMI && BMI < 30):
      console.log('輕度肥胖')
      break
	  case (30 <= BMI && BMI < 35):
      console.log('中度肥胖')
      break
      case (35 <= BMI):
      console.log('重度肥胖')
      break
      
    }

