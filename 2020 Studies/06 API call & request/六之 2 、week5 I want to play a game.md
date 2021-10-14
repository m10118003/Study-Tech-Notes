# 六之 2 、week5  I want to play a game   
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/22 

## 關卡開始，這是 Lidemy HTTP Challenge。  
一個可以幫助了解 GET & POST 等動作的 API 串接小遊戲。  

https://lidemy-http-challenge.herokuapp.com/start

需要用 node.js 搭配 request 這個 library 來解題。  

像這個就是小提示:  

/lv1?token={GOGOGO}&hint=1

---

https://lidemy-http-challenge.herokuapp.com/lv1?token={GOGOGO}

進到第一關會看到圖書館管理員跟你說話，但其實我看不懂他在說啥，我也沒有能力值還是神裝之類的XD  
他(?) 還會給你這個[資訊](https://gist.github.com/aszx87410/3873b3d9cbb28cb6fcbb85bf493b63ba)說等等可能會用到...也許是拿來查書 ?  

https://lidemy-http-challenge.herokuapp.com/lv1?token={GOGOGO}&name=your_name

會跟你說去下一關的代幣是 {HellOWOrld} 。   
恩 ? 我是免費來打工的嗎 ???   

---

## 第二關

https://lidemy-http-challenge.herokuapp.com/lv2?token={HellOWOrld}&name=your_name

誒不是，我怎麼變成免費打工仔惹，但要幫忙就幫到底吧 QQ

https://lidemy-http-challenge.herokuapp.com/lv2?token={HellOWOrld}&id=56

一路找幫他找到，好像是 56 這本書 ???   
然後你就拿到了另外一個代幣 {5566NO1} XD 。  

---

## 第三關，免費打工仔要幫忙搬書

欸不是，太會使喚人了吧 !? 

https://lidemy-http-challenge.herokuapp.com/lv3?token={5566NO1}

用 &hint=1 看一下，原來要用 &id 拿書，那好! 
寫個 code 挖書本(誒好像哪裡怪怪的 
```
const request = require('request');
// const process = require('process');

// console.log(process.argv)

request.post(
  {  
    url:'https://lidemy-http-challenge.herokuapp.com/api/books',
    form: {
      name:'大腦喜歡這樣學',
	  ISBN:'9789863594475'
    }
  },
  function (error, response, body) {
  console.log(response.statusCode)
  console.log(body)
  }   
);
```
成功後就拿到，狀態代碼 & 如下:  

200  
{"message":"新增成功","id":"1989"}  

https://lidemy-http-challenge.herokuapp.com/lv3?token={5566NO1}&id=1989

輸入後就給我下一關的代幣 {LEarnHOWtoLeArn} 了。

---

## 第四關，所以我說打工費呢?

https://lidemy-http-challenge.herokuapp.com/lv4?token={LEarnHOWtoLeArn}

輸入後，管理員可能吃太多美式牛排老人癡呆了QQ 
跟你說找錯書，要一本書，名字有世界，總不可能是替身吧...
這邊看起來要用作者: 村上春樹 和書名: 世界 去找書  。

https://lidemy-http-challenge.herokuapp.com/api/books?q=世界

在網址後先加上世界，但用作者去找是找不到的，得到:  

{"id":79,"name":"世界末日與冷酷異境","author":"村上春樹","ISBN":"9571313408"} 。

輸入 &id=79 給管理員吧~   
好了後，又給你代幣  {HarukiMurakami} ， 欸不是，我說那個打工費呢 ?  

---

## 第五關，總不會有 100 關吧 @@ ?  

https://lidemy-http-challenge.herokuapp.com/lv5?token={HarukiMurakami}

好喔，捐錯書了所以要刪除書籍，寫個代碼刪除它吧!  
```
const request = require('request');
// const process = require('process');

// console.log(process.argv)

request.delete(
  {  
    url:'https://lidemy-http-challenge.herokuapp.com/api/books/23',
    form: {
      id:'23'
	  
    }
  },
  function (error, response, body) {
  console.log(response)
  console.log(body)
  }   
);
```
看到末行，會跟你說:     
```
body: '{"message":"\\n咦...是刪掉了沒錯，但總覺得哪裡怪怪的，算了，先這樣吧！
下一關的 token 為 {CHICKENCUTLET}\\n"}',
  [Symbol(kCapture)]: false
```
  
---

## 然後你就到了第六關

https://lidemy-http-challenge.herokuapp.com/lv6?token={CHICKENCUTLET}

因為你沒登入就刪除文件超詭異，所以拿到一個新文件:  

https://gist.github.com/aszx87410/1e5e5105c1c35197f55c485a88b0328a

誒，這個帳號密碼很容易被盜用的感覺呢...
時間不早了, 先跑了, 明天再幫忙~



