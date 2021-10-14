# 一之 1 、 網之呼吸 - HTTP
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/9
---

HTTP 協定、標準，為了了解這個協定是甚麼，網頁前端跟後端溝通的時候就是透過 HTTP ， 是網際網路通訊的基礎，分成應用層、傳輸層、網路層和連結層，之後會提到。

參考資料:

[淺談網址 HTTP 與 HTTPS 的差別](https://www.webdesigns.com.tw/HTTPorHTTPS.asp)

[一文搞懂 HTTP 和 HTTPS 是什麼？兩者有什麼差別](https://tw.alphacamp.co/blog/http-https-difference)

[「筆記」- 何謂 HTTP 傳輸協定](https://medium.com/pierceshih/%E7%AD%86%E8%A8%98-%E4%BD%95%E8%AC%82-http-%E5%82%B3%E8%BC%B8%E5%8D%94%E5%AE%9A-1d9b5be3fd24)

[TCP/IP 協定與 Internet 網路：第十五章 全球資訊網系統](http://www.tsnien.idv.tw/Internet_WebBook/chap15/15-5%20HTTP%20%E5%82%B3%E8%BC%B8%E5%8D%94%E5%AE%9A.html)

---

# 一之 2 、 網之呼吸 - HTTP request
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/9
---

- HTTP request => Client request 請求 => Server response 。

以 GitHub https://github.com/Lidemy/mentor-program-4th 為例，在頁面後按下 F12 或 Ctrl+Shift+I 開啟網頁工具箱:  

![](https://i.imgur.com/TdKezNQ.png)  

- 在 Network 這一分頁會將瀏覽器所有 request (請求) 印出來 (如看不到要重新載入) ， 火狐跟 Chrome 的瀏覽器介面不太一樣。
- Headers 可以看到很多 request ; 而 Response (回應) 則是頁面的 html 。

整個網頁流程:

1. 瀏覽器 => 傳 HTTP request 至 server 。
2. Server 處理後 => 回傳一個 response ， 即:  

![](https://i.imgur.com/tdyeTNn.png)  

- 右邊回應內的這整段文字，只有瀏覽器看得懂。  
- 可以用 [Charles](https://www.charlesproxy.com/download/) 看 Request 和 Reponse 長甚麼樣子。   
- 用火狐的話可以省略安裝 Charles ， 在網路工具箱的檔頭內看到 Request 和 Reponse (請求檔頭和回應檔頭)。  
- GET https://github.com/Lidemy/mentor-program-4th ， GET 表示動作 ， http 表示指定地址，版本是 HTTP/1.1 ，通常會有 body ， 如果只是 GET ， 拿資訊，就不會看到 body 。  
- 在回應可以看到 [body](https://i.imgur.com/DyHtWBD.png) ， 許多的文字。
- request & response 都有一定格式。

---

參考資料:

[HTTP/1.1 — 訊息格式 (Message Format)](https://notfalse.net/39/http-message-format)  

---

# 一之 3 、 網之呼吸 - Domain Name System (DNS)
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/9
---

### 傳東西的話，理論上要看 IP 位置，但是 request 這只有要求網址:  

-  因此背後有機制將 https/Lidemy/mentor-program-4th (Domain Name) 轉成 IP 。
-  所以 Client 就會去問 DNS Server  ，  github.com 是在哪 ?  ~~我是誰 ? 我在哪 ?~~ 
``{"GET":{"scheme":"https","host":"github.com","filename":"/Lidemy/mentor-program-4th","remote":{"地址":"140.82.113.4:443"}}}``
-  實際上電腦最底層是把 request 送到 IP位置，可以看到 remote address 地址: 140.82.113.4:443 。
-  可以在 CLI 輸入指令 `nslookup github.com` 查詢 Domain Name ， 會得到:
 ```
未經授權的回答:
伺服器:  hitronhub.home
Address:  192.168.0.1

名稱:    github.com
Address:  140.82.112.3
 ```
---
參考資料:
[DNS 伺服器是什麼？如何運用？](https://www.stockfeel.com.tw/dns-%E4%BC%BA%E6%9C%8D%E5%99%A8%E6%98%AF%E4%BB%80%E9%BA%BC%EF%BC%9F%E5%A6%82%E4%BD%95%E9%81%8B%E7%94%A8%EF%BC%9F/)

---

### Host Database

- 假設電腦今天傳個 request 到 localhost ， 那電腦會先去 Host Database 查詢要傳到哪個 localhost 的 IP ， 優先配對規則 。

- 通常在測試的時候會用到 Host Database 的檔案，通常 localhost 就是代表自己的電腦(跑的服務) 。

---

# 一之 4 、 網之呼吸 - 瀏覽器概念
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/9
---

拜訪網頁時:
1. 瀏覽器幫 User 發 request 到 address。
2. 拿到 response 後呈現視覺渲染出來，成為看到頁面。
3. 根據回傳的 html 資訊下載資源，呈現文字、圖片、影片等。
---

## 拿拿看 response

但其實沒有瀏覽器的話，一樣可以拿到 response ， 在 node.js  內有個 library 就是 Request 可以去做這些事情。

https://www.npmjs.com/package/request

在有 npm ， node_modules 資料夾和 package.json 檔案的目錄下，安裝: `npm i request` ， 好了後可以新建一個 index.js 檔案直接使用下段 code :  
```
const request = require('request');
request('http://www.google.com', function (error, response, body) {
  console.error('error:', error); // Print the error if one occurred
  console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
  console.log('body:', body); // Print the HTML for the Google homepage.
});
```

- 首先會將 request 給 require 進來 ， request 後面會接網址，可改成 https://github.com/Lidemy/mentor-program-4th 。
- 如果有 error 會將 error 印出。
- 如果沒有錯誤會將 statuscode 給印出。
- 可以先將 body 隱藏不印出。

執行 `node index.js` 會得到 ， response :  
error: null
statusCode: 200

沒有錯誤，請求成功。

---

## 印出 body 試試看
```
const request = require('request');
request(
  'https://github.com/Lidemy/mentor-program-4th',
  function (error, response, body) {
// console.error('error:', error); // Print the error if one occurred
// console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
    console.log('body:', body); // Print the HTML for the Google homepage.
});
```
就會得到以 `<!DOCTYPE html>` 開頭的一大串組成 body 的 code 。

也因此可以自行轉成網頁，運用上面的 code ， 存成 index.js 檔案:  

```
const request = require('request');
request(
  'https://github.com/Lidemy/mentor-program-4th',
  function (error, response, body) {
// console.error('error:', error); // Print the error if one occurred
// console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
    console.log('body:', body); // Print the HTML for the Google homepage.
});
```
使用以下指令:

- mac 似乎可以直接使用這個 `node index.js > github.html` 指令。
- win 的話可以用這 `env node index.js -i > github.html` 指令。

就會得到一個 github 的課綱頁面，https://github.com/Lidemy/mentor-program-4th 跟這個應該是一樣的。  
脫離瀏覽器後，我們可以發 request 到 server 去，自行寫 code 也可以 get 頁面。

---

參考資料:

[[Node.js]request](https://blog.johnsonlu.org/node-jsrequest/)

---

# 一之 5 、 網之呼吸 - Header 與 Body（不是網頁的那個）
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/10

- Header : 額外資訊。
- Body : 主要資訊。

---

而 request & response 都有 Header ， 分別帶有不同資訊。

先前是 request body ， 其實也能 request header :  

```
const request = require('request');
request(
  'https://github.com/Lidemy/mentor-program-4th',
  function (error, response, body) {
     console.log(response.headers)
});
```
可以看到內容有 date 時間 ， 'content-type' 表示是 html ， 編碼是 utf-8 ， server 是 GitHub.com 。

---
參考資料:
[解決 win 將 .js 檔案轉 html 的問題](https://superuser.com/questions/1011597/what-does-an-output-is-not-a-tty-error-mean)

---

# 一之 6 、 網之呼吸 - GET 與 POST
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/10

- GET 動詞表示動作，蠻常用到 GET 只是省略，幾乎很多 request 都是 GET 。
- POST 執行動作，登入頁面的時候會有，用網路工具箱去看 session 的 Headers 就會看到 Form Data ， 有 key:value ， 例如 login: 是帳號 ， password: 密碼。
- POST 內的 session 的 Headers ， Form Data  在 View source 的地方，表示在 request body 內其實是以 encode (不一樣的有不同規範) 形式:
![](https://i.imgur.com/T0ROxcX.png)

---

# 一之 7 、 網之呼吸 - HTTP other method
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/10

- 常用的動作有: GET 、 PUT 、 POST 、 DELETE 。
- 可以參考  [MDN HTTP 請求方法](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Methods)
- PUT 和 PATCH 有點類似，但 PUT 會更新狀態資訊。
- 例如用 PUT 雞腿飯*3 ，會把原本訂購雞腿飯*2 和排骨飯*5 ，直接修成雞腿飯*3 ， 排骨飯就消失了。
- PATCH 則是會讓原本訂購的排骨飯存在，這個比較不會蓋掉所有東西。
- OPTIONS 會讓 server 回傳給你，這 server 支援甚麼方法。

---

# 一之 8 、 網之呼吸 - HTTP status code
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/10

狀態代碼 (status code) ， 參考 [MDN 網路狀態代碼](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Status) ， 以開頭為區分。  
- 1. 開頭 Client 端需要處理，少見。  
- 2. 開頭，常見的 200 代表成功居多 ， 204 表示刪除資源成功，但是沒有資訊要傳達。  
- 3. 開頭，像是 301 這東西永久被移到新位置，而 302 可能是暫時移到新位置。  
```
今天第一次訪問某個網址得到:
GET aaaaa.com
但 aaaaa.com server response:
statust code: 301
Location: b.com

然後下一次再去 aaaaa.com
瀏覽器 (有存 cookie) 會從第一次訪望這個網址後得知，
該網址被永久移到 b.com ， 因此會自動移過去。

GET aaaaa.com => b.com(瀏覽器幫你自動移形換位)
就像餐廳永久遷址一樣。
---------------------------------------------------------------------------

但如果是這樣子得到 (暫時的移動到 b.com) :
GET aaaaa.com
但 aaaaa.com server response:
statust code: 302
Location: b.com

瀏覽器還是會去 aaaaa.com ， 然後再問一次我要去哪 ?
瀏覽器才會再去 b.com 。
像是餐廳暫停營業，暫時遷址到其他地方，所以我下次再來還是原店舊址。
```
- 4. Client 端出了錯誤，像是 400 語法錯誤，要的東西太多; 或是常見的 404 Not Found ， 要的東西餐廳沒有提供。  
- 5. Server 端錯誤，像是搶票的時候會看到 500 ， 503 Server overload ， 因此要維修。   

![](https://i.imgur.com/2LP3TIT.png)  

---

# 一之 9 、 網之呼吸 - 實作簡易 HTTP Server
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/10

- 之前有實作 Client 端，用 npm library 的 request 去 request body 。  

__這次也用 node.js 的內建 library HTTP 來實作，以下 code 存成 server.js 檔案:__
```
var http = require('http')

var server = http.createServer(handleRequest)
function handleRequest(req, res) {
  console.log(req.url)
  res.write('Hello !')
  res.end()
}
//可以這樣寫 var server = http.createServer(function(req, res) {})，不習慣可用↑
 
server.listen(5000) // 服務代碼 port;
```
- 執行指令 `node server.js` 因為 req.url 沒有指明位置，所以只會看到程式 (server) 一直在跑，按下 Ctrl+c 中斷，實際上 server 端也是要全天候運作。  

- 如果讓 CLI 下的指令 `node server.js` 持續在跑的情況，再去瀏覽器網址列輸入 `localhost:5000/` 會看到瀏覽器印出 Hello ! 。  

- 同時看到 CLI 的介面會出現:
```
/
/favicon.ico
```
- 1. 第一個 / 是根目錄，可以看到 localhost 。
- 2. 第二個 .ico 是瀏覽器分頁左上的小 icon ， 通常會顯示在分頁上，瀏覽器通常預設會去拿。
![](https://i.imgur.com/wSGRUl7.png)
- 3. 也可以在 / 根目錄拜訪不同的 slash ， 例如 /Hello! ， 在瀏覽器開啟網路工具箱 => Network 會看到 localhost 名字變成 Hello! 。

- 如果關掉指令 `node server.js`  ， 瀏覽器也重新整理，網路工具箱 => Network 就會沒有反應，因已經沒有服務在聽 5000 這個 port 。

---

## 根據 req.url 做不同事情
可以根據 req.url 做不同事情:  
```
var http = require('http')

var server = http.createServer(handleRequest)
function handleRequest(req, res) {
// console.log(req.url)
    if (req.url === '/') {
      res.write('Welcome !')
      res.end()	
      return
    }

    if (req.url === '/Hello') {
      res.write('Hello !')
      res.end()	
      return
    }

    if (req.url === 'redirect') {

  }

}
//可以這樣寫 var server = http.createServer(function(req, res) {})，不習慣可用↑
 
server.listen(5000) // 服務代碼 port;
```
然後進行指令 `node server.js` ， 再去瀏覽器網址列輸入 `localhost:5000/` 會看到以下狀況:  
- 只有在 / 的情況，文字被替換成 Welcome ! 。  
- Server 端會根據不同 / 底下的網址輸入給出不同回應。  
- 如果在瀏覽器網址列輸入 /Hello ， 會看到印出 Hello ! 。

---

## 運用重新導向
### 狀態代碼 200 的情況:
```
var http = require('http')

var server = http.createServer(handleRequest)
function handleRequest(req, res) {
// console.log(req.url)
    if (req.url === '/') {
      res.write('Welcome !')
      res.end()	
      return
    }

    if (req.url === '/Hello') {
      res.write('Hello !')
      res.end()	
      return
    }

    if (req.url === '/redirect') {
      res.writeHead(200, {
        'lidemy': 'good'
      })
     res.end()	
      return
  }
  res.writeHead('404')
  res.end()	
  return
 }
//可以這樣寫 var server = http.createServer(function(req, res) {})，不習慣可用↑
 
server.listen(5000) // 服務代碼 port;
```
- 在瀏覽器輸入 / 或是 會跟之前一樣，而網路工具箱下顯示服務狀態代碼則是 200 。  
- 而在 / 後隨便打個 ppap 還是甚麼，就會出現狀態代碼 404 。  
- 而在 /redirect 則會看到網路工具箱內，檔案下 redirect 顯示 200 ，右邊的檔頭內，回應檔頭 (Response Headers) 則有 lidemy	good 訊息。  

### 狀態代碼 302 的狀況:  
狀態代碼 200 的情況:
```
var http = require('http')

var server = http.createServer(handleRequest)
function handleRequest(req, res) {
// console.log(req.url)
    if (req.url === '/') {
      res.write('Welcome !')
      res.end()	
      return
    }

    if (req.url === '/Hello') {
      res.write('Hello !')
      res.end()	
      return
    }

    if (req.url === '/redirect') {
      res.writeHead(302, {
        'Location': '/Hello'
      })
     res.end()	
      return
  }
  res.writeHead('404')
  res.end()	
  return
 }
//可以這樣寫 var server = http.createServer(function(req, res) {})，不習慣可用↑
 
server.listen(5000) // 服務代碼 port;
```
-   /redirec 下如果狀態代碼 302 ， 則要選擇要轉到哪個 / 底下:
```
   if (req.url === '/redirect') {
      res.writeHead(302, {
        'Location': '/Hello'
```
- 網路工具箱內會先顯示狀態代碼 302 ， 然後告訴你轉去 /Hello 底下，再顯示 200 。

---

# 一之 10 、 網之呼吸 - 總結
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/11

- HTTP 協定。
- 瀏覽器程式的限制，不是 HTTP 或是 Server 本身的限制。
- 實作 request 和 server ， 寫程式也能達到瀏覽器效果。

---