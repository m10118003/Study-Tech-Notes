# 四之 1 、Data Format   
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/13  

資料結構: 發送跟接收的時候資料都有一定的格式。  

__網路的本質跟溝通有關，且是規模化有標準的溝通方式。__  
__因此需理解使用 API 使用和交換資料以及標準。__  


---

1. 純文字跟自定義格式:  
- 可以定義想要的格式。  
- 但是要寫一些 function 來應對 response 。  
- 但一般很少用。  

2. 熱門的格式 Extensible Markup Language (XML) :  
- 是標記式語言，跟 HTML 很像，但只用傳輸和攜帶資料訊息，不表現或展示資料。  
- 非常古老，但格式統一，可跨平台共享，很多系統如，物流、銀行系統 API 使用。  
- 格式定義完整，因此文件內容資料很大; 在 Server 和 Client 端都不好維護和很耗資源。  

3. JavaScript Object Notation (JSON ) :  
- 很常見且像是 JS 的物件，資料結構體積小，且好讀快寫，可相容和跨平台交換資料。  
- 基於 JS 容易解析，支援多種程式語言，簡化開發量，也可擴充，傳遞速度遠快 XML 格式。  
- 雖然親民但資料的描述性差。

以這個 API 為例，回傳的就是一個 JSON 格式 (stream) :  
```
const request = require('request');
const process = require('process');

// console.log(process.argv)

request(  
  'https://reqres.in/api/users/2', 
  function (error, response, body) {
  console.log(body);
  }   
);
```
- 用 `console.log(body)` 印出來的東西會是 JSON 格式的 "字串" ， 因為拿的是網頁的資料。  
- 但如果想直接存取 用 `console.log(body.data)` 是不行的，因為是 stream ， 因為是字串。  
可以用一個函式來解決 ， JSON.parse(body) ， 傳進去的必須是 JSON 格式的字串:  
```
const request = require('request');
const process = require('process');

// console.log(process.argv)

request(  
  'https://reqres.in/api/users/2', 
  function (error, response, body) {
  const json =  JSON.parse(body)
  console.log(body);
// console.log(json)
  }   
);
```
- 拿到的東西會跟上一個式子相同，但用 `console.log(json)` 會發現印出來的東西會是 JS 的 Obj 。  
- 如果用 `console.log(json.data.first_name)` 就會拿到 Janet 。  
- 通常建議用 parse() 函數解析 JSON 資料，直接用 eval() 函數容易被跨網站指令碼 (XSS) 攻擊。  

用 `console.log(JSON.stringify(obj))` 可以讓 JSON 格式的物件轉成字串:  
```
  const obj = {
    name: 'Haku', 
	job: 'none'
  }
  console.log(JSON.stringify(obj))
```
會印出字串。  
- 其實任何資料格式在任何程式語言都能使用，只是要知道怎麼轉換成物件(解析)的方法。  

---
參考資料:

[簡單介紹標記語言](http://wacoderkingdom.blogspot.com/2015/08/blog-post.html)

[JSON與XML優缺點對比分析](https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/276753/)

[ [Day7] 基本資料格式: XML 和 JSON ](https://ithelp.ithome.com.tw/articles/10203632)

[初探JSON(JavaScript Object Notation)](http://www.syscom.com.tw/Print_Preview.aspx?id=52&group=3)

[Introducing JSON](https://www.json.org/json-en.html)

[ 你懂 JavaScript 嗎？#8 強制轉型（Coercion）](https://ithelp.ithome.com.tw/articles/10201512)

---

# 四之 2 、交換資料 - SOAP  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/14  

肥皂 (x) 全名 Simple Object Access Protocol (SOAP) 。  
- 有定義的資料交換格式，資料交換都透過 XML ， 例如 [SoapUI](https://www.soapui.org/learn/api/soap-vs-rest-api/) ， 但現在較少用。  
- 通常會借用 library 來使用，例如 [node-soap](https://github.com/vpulim/node-soap) ， 連接到 Server 直接呼叫 function 。  
---
參考資料:  

[SOAP  簡單物件存取協定](http://kevin.hwai.edu.tw/~kevin/material/EAssistant/SOAP.htm)  

---

# 四之 3 、交換資料 - 其他 HTTP API  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/14  

- 大多數不是以 SOAP 為基準的交換資料方式。  
- 例如，透過 HTTP 基本 method 或是透過請求代碼 GET 、 POST 還有 JSON 格式在溝通。  

---

# 四之 4 、交換資料 - RESTful API  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/14  

__REST 是一種 Style 而不是標準協議，建議形式。__  

- Representational State Transfer (REST) 表現層狀態轉換架構，可降低資源消耗、降低對 HTTP 連接的重複請求。  

- RESTful 是符合 REST 設計風格的 Web API ， 例如:  
  - Web 透過與服務代碼相同的請求 method (CRUD) 來操作資源 (資源是網路事務的抽象稱呼)。  
  - 看到網址就知道資源，搭配動作就可以對應資源處理方式，比較直覺。  
  - 資源由唯一 URI 指定，和統一的 API ， 且表現方式取決於機器或是人來讀寫。  
  - 簡潔有力的位址、通用的介面且 Stateless ， 由 Client 保存 State 。  

---
參考資料:

[API 是什麼? RESTful API 又是什麼?](https://medium.com/itsems-frontend/api-%E6%98%AF%E4%BB%80%E9%BA%BC-restful-api-%E5%8F%88%E6%98%AF%E4%BB%80%E9%BA%BC-a001a85ab638)

[[不是工程師] 休息(REST)式架構? 寧靜式(RESTful)的Web API是現在的潮流？](https://progressbar.tw/posts/53)

[什麼是REST? 認識 RESTful API 路由語義化設計風格](https://tw.alphacamp.co/blog/rest-restful-api)

[什麼是 REST? RESTful?](https://medium.com/@cindyliu923/%E4%BB%80%E9%BA%BC%E6%98%AF-rest-restful-7667b3054371)

---

# 四之 5 、 實戰 API 串接 DELETE & PUT
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/14  

[官方文件有介紹用法](https://github.com/request/request)  

## DELETE

用指令 `request.del() / request.delete(): Defaults to method: "DELETE".` 來試試:  

```
const request = require('request');
// const process = require('process');

// console.log(process.argv)

request.delete(  
  'https://reqres.in/api/users/2', 
  function (error, response, body) {
  const json =  JSON.parse(body)
  console.log('body:', body);
// console.log(json)
  }   
);
```
- 發現印不出來，因為 body 不是一個 JSON 字串。

而以 `console.log(response.statusCode)` 指令來查看:  
```
const request = require('request');
// const process = require('process');

// console.log(process.argv)

request.delete(  
  'https://reqres.in/api/users/2', 
  function (error, response, body) {
  console.log(response.statusCode)
  }   
);
```
- 會得到狀態代碼 204 (No Content) 代表刪除完後 ， Server 也不知道要回傳甚麼給你，所以 body 是空的，的確有刪除成功。  

---

試試看 `.patch()` 的函式:  
```
const request = require('request');
// const process = require('process');

// console.log(process.argv)

request.patch(
  {  
    url:'https://reqres.in/api/users/2',
    form: {
      name:'hello'
    }
  },
  function (error, response, body) {
  console.log(response.statusCode)
  console.log(body)
  }   
);
```
- 會回傳 200 ，修改成功。  

API 串接即按照要求的格式丟 request 得到 response 。  
實際上有很多自定義交換資料的格式或是標準 (protocol)，也可以自行開發 API 。

---

# 四之 6 、 好用的 CLI 指令 - `curl`
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/14  

curl [官方網站](https://curl.haxx.se/)

- 會發一個 GET 的 request 到你下指令的網址，例如 `curl https://github.com/Lidemy/mentor-program-4th` ， 然後會回傳 response 。  
- 如果要下載就可以 `curl https://github.com/Lidemy/mentor-program-4th > html` ， 就會下載成 html 檔案。  
- 指令 `curl -I https://github.com/Lidemy/mentor-program-4th` 我只要 header ， 他就會給你 header 以及狀態代碼以及其他 content 。  

## curl 可發 POST 送出 JSON 格式的資料

可以對網址發 POST ， 且是 JSON 格式的資料:  

```
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"username":"xyz","password":"xyz"}' \
  http://localhost:3000/api/login
```
成功會得到 response ， 會印出:  
```
me":"xyz","job":"xyz"}'   https://reqres.in/api/users
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   102  100    76  100    26    118     40 --:--:-- --:--:-- --:--:--   159{"name":"xyz","job":"xyz","id":"816","createdAt":"2020-08-17T12:21:41.739Z"}
```

curl 的用法很多，常用在跑 HTTP Server 。  

---

## `nslookup`

例如 `nslookup github.com` 指令:  

- 會得到 Name 、 Address ， 可以解析 domain 的 IP 地址。  

---

## `ping`
例如 `ping github.com` 指令:  

- 可以用來測試能不能連線。  

---

## `telnet`
例如 `telnet 52.74.223.119 80` 指令:  

- 可以上 ppt (O
- 可以測試看連接埠 (port) 有沒有開啟。  
- 也可以傳資料進去，例如 GET 。  
- Telnet 的啟用方式:  
![](https://i.imgur.com/0lOTV17.png)

---
參考資料:

[Linux Curl Command 指令與基本操作入門教學](https://blog.techbridge.cc/2019/02/01/linux-curl-command-tutorial/)

[How do I POST JSON data with cURL?](https://stackoverflow.com/questions/7172784/how-do-i-post-json-data-with-curl)

---

