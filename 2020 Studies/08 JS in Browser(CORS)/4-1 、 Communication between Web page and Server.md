# 4-1 、 Communication between Web page and Server
###### tags: `FE102` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/07

- Client 與 Server 做溝通。  
- Server 的 Response 可以是 .html 、 JSON 、 JS 。  

## .html
![](https://i.imgur.com/78doWHP.png)  

- ==如果 Response 是 .html 檔案的話，是平常瀏覽器在做的事情。==  

- 如重新整理頁面的時候，瀏覽器幫 User 發一個 Request 到這個頁面網址。  

- 這網址回傳的 Reponse 就是 User 看到的視覺化頁面本身。  

- 平常用瀏覽器就是 Client 跟 Server 溝通。  

## JSON
- Server 的 Response 也可以是 JSON 格式檔案。  
- 如之前用過的 https://reqres.in/api/users ， 會發一個 GET 的 Request 到 https://reqres.in/api/users 。  
- 而其 Response 就是回應酬載 : {"page":1,"per_page":6,"total":12,"total_pages":2,"data"... 。  

![](https://i.imgur.com/MhmO2D0.png)  

## JS
- JS 透過瀏覽器發Request 得到 Response 。

*** 

# 4-2 、 Node.js 呼叫 API 與在網頁上的呼叫差異  
###### tags: `FE102` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/07

## Node.js 與 Server 溝通  
- Node.js 發出的 Request 和 Response 到 Server 不會被干擾。  
- 中間的東西不會被改動，沒被限制太多東西。  

![](https://i.imgur.com/twuAE4G.png)  

---

## 瀏覽器上的 JS 與 Server 溝通  
- 透過送 Request 的 API ， 瀏覽器上的 JS 會先透過瀏覽器。   
- 瀏覽器再透過作業系統發 Request 到 Server 。   
- Server 透過作業系統再到瀏覽器，透過瀏覽器傳 Response → 瀏覽器上 JS。  
- 但瀏覽器上的 JS Request 和 Response 均被瀏覽器限制。  

![](https://i.imgur.com/4RKBDpd.png)  

1. 瀏覽器會限制 User 做的事情。  
2. 瀏覽器可能會幫忙加額外資訊 ， Server 端收到的 Response 就會有額外資訊。  

---

# 4-3 、 網頁前端傳資料到後端的方式 (1)
###### tags: `FE102` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/08

## 透過表單形式 - 傳資料
```
<!DOCTYPE HTML>

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>瀏覽器上執行 JS</title>
  <style>

  </style>
</head>
<body>
  <div class='app'>
    <form method="GET" action="https://www.google.com/">
      name: <input name="username" />
      <input type="submit" />
    </form>
  </div>
  <script>


  </script>
</body>
</html>

```
![](https://i.imgur.com/RrScluG.png)  

- `action="HTTPS"` ， 實際的 Request 是發到 https://www.google.com/?username=0123 。  
- 用 GET 的動作，參數會附加在網址上。  
- 登入一般會用 POST 的動作，會在 body 內，不會在網址上被看到。  
- 瀏覽器本身的 html 元素發的 Request ， 瀏覽器接收到的 Response 會直接 Render 出來結果。  
- 因此 Google 回傳的結果就是怎樣的結果，即發一個 Request 到新的頁面。  
- 這方法跟 JS 本身無關聯性，是直接代參數。  
- 每次要求新的資料都要換頁面。  

---

# 4-4 、 網頁前端傳資料到後端的方式 (2)
###### tags: `FE102` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/08

- 透過 JS 交換資料，不用換頁。  

## 透過 AJAX (**Asynchronous JavaScript and XML**) - 傳資料

- 任何非同步跟 Server 交換資料的都可以算是 AJAX 。  
- 早期都用 XML ， 現在比較多用 JSON 格式。  
- 從瀏覽器上的 JS 透過瀏覽器再透過 O.S. 發 Request 到 Server 。  
- 但 Server 回傳的 Response 會回到瀏覽器，但瀏覽器再轉傳給 JS 。  

```
<!DOCTYPE HTML>

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>瀏覽器上執行 JS</title>
  <style>
    body {font-size: 38px;}
  </style>
</head>
<body>
  <div class='app'>

    </form>
  </div>
  <script>
    const request = new XMLHttpRequest()
    request.onload = function() {
      if (request.status >= 200 && request.status < 400) {
        console.log(request.responseText)
      } else {
        console.log('err')
      }
  }

  request.onerror = function() {
    console.log('error')
  }

  request.open('GET', 'https://google.com', true)
  request.send()
  </script>
</body>
</html>
```
![](https://i.imgur.com/DcwqT32.png)  
錯誤訊息:  

```
已封鎖跨來源請求: 同源政策不允許讀取 [https://google.com/](https://google.com/ "https://google.com/") 的遠端資源。（原因: 缺少 CORS 'Access-Control-Allow-Origin' 檔頭）。
已封鎖跨來源請求: 同源政策不允許讀取 [https://google.com/](https://google.com/ "https://google.com/") 的遠端資源。（原因: CORS 請求未成功）。
```
表示瀏覽器不准現在這個網頁發 request 到 google.com 。  

---

- 概念上很像事件監聽，類似這種寫法:  
```
    btn.addEventListener('click', function()..) 
    btn.onClick = function()...
```
- ``request.onload = function() {}`` 放一個 function 到 onload 上。  
     
- `if (request.status >= 200 && request.status < 400)` 判斷 request 的動作結果。   

- ``request.onerror = function()`` 有錯誤的時候。  

-  ``request.open('GET', 'https://google.com', true)`` :  
    - 第一參數，動作。  
    - 發 request 到這個地方，位址。  
    - 第三個參數， false 表示要同步(等到 response 回來，等待期間怎麼按瀏覽器都沒反應)。
    -  true 表示非同步表示能同時做很多事情。  

- 如果改成 `request.open('GET', 'https://reqres.in/api/users', true)` :  
發了一個 Request 到這個位址，動作 GET 也成功，也能拿到 Response 。  

-  ``request.send()`` 才能發送出去。  

***
參考資料:  

[Ajax - Web 開發者指引| MDN](https://developer.mozilla.org/zh-TW/docs/Web/Guide/AJAX)  

https://zh.wikipedia.org/wiki/AJAX  

[什麼是 Ajax？ 搞懂非同步請求 (Asynchronous request)概念](https://tw.alphacamp.co/blog/ajax-asynchronous-request)  

https://medium.com/%E9%A6%AC%E6%A0%BC%E8%95%BE%E7%89%B9%E7%9A%84%E5%86%92%E9%9A%AA%E8%80%85%E6%97%A5%E8%AA%8C/js-ajax-%E7%AD%86%E8%A8%98-b9a57976fa60  

[Day1 甚麼是Ajax? (part1) - iT 邦幫忙 - iThome](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjSxef63YHsAhWFLqYKHQAXCTEQFjAFegQIDBAB&url=https%3A%2F%2Fithelp.ithome.com.tw%2Farticles%2F10200409&usg=AOvVaw1kVx-E-2i4TXBK3qDE1aEZ)  

---

# 4-5 、 XHR 的餵食方式  
###### tags: `FE102` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/08

- ``const request = new XMLHttpRequest()`` 我要發一個新的 request 。  

- ``request.addEventListener('load', function()`` request 被載入就可以拿一些資訊。  

- 因為是純文字，因此用 JSON parse 成物件後才能做一些事情。  

- 如果是 ``console.log('err')`` 改成 `console.log('request.status, request.responseText')` ， 則會回傳 Response 。  

![](https://i.imgur.com/LbdWMGr.png)  

==不一定每個 Response 都會回傳 responseText 。==  

---
參考資料:  

https://blog.techbridge.cc/2017/05/20/api-ajax-cors-and-jsonp/  