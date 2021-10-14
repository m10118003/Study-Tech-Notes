# 三之 1 、 API - 介面很重要 !  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

__應用程式介面 (Application Programming Interface) ， AKA API 。__

- 介面很重要，透過介面來溝通。
- 電腦透過介面存取。

因此可以分為使用 API 和提供 API:

- 不希望直接被存取資料庫。
- 定義那些資料要被存取。
- 例如: 作業系統提供 API、檔案透過 API 讀取。
- 串接 API = 拿取資料。
- 提供 API 給他人來網站存取資料或是新增資料。

__重點: 透過 API 即可讓雙方交換資料。__

---

# 三之 2 、 API & Web API  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

__Web API => HTTP API ， 即透過 HTTP 協定的 API ， 來交換資料。__

- FaceBook - 圖形API 。
- Twitch API - V5 :  
    - 可以拿參數 、HTTP API request & response 。
    - 串接 API 來拿  request & response 。
    - 歐付寶 SDK - 軟體開發套件 (Software Development Kit) ， 裡面做好許多的 API ，可以直接使用。
    - PokeAPI - 輸入怪物名稱就能拿到例如技能資料之類，有一定資料格式。
    - picsum 呼叫圖片的 API 。
    - HackerNews API ， 幫找網站的結構後做處理，拿到 response 。

---

# 三之 3 、 API 實作  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/13  

之前用了 npm 的 library Request ， 這次實作以檔案 index.js 的內容來改:  
```
const request = require('request');

request(
  'https://github.com/Lidemy/mentor-program-4th', 
  function (error, response, body) {
    console.log(response.headers)
    // console.log('body', body);
    }
);
```
在 https://reqres.in/ 有方便實用的 API ，可提供測試用，我們拿 url: "https://reqres.in/api/users" 來使用:  
```
const request = require('request');

request(
  'https://reqres.in/api/users', 
  function (error, response, body) {
    console.log(body);
    }
);
```
- 這樣就能發一個 request 到   https://reqres.in/api/users ， 並且印出 body 。  
- 實際用 node.js 執行會有這個 API 返回資料。  

## 拿資料
根據 https://reqres.in/ 的 API 格式，要得到 SINGLE USER 的 ID 資料，則要這樣做:   
```
Request
/api/users/2 
```

因此:  
```
const request = require('request');

request(
  'https://reqres.in/api/users/2', 
  function (error, response, body) {
    console.log(body);
    }
);
```
__印出 response 會發現這資料格式跟物件很相像。__  

- 如何完成 API 串接 ?  
- 試著讀懂文件並執行。  
- 這樣就完成了 API 串接。  

---

## 直接在 CLI 打指令 串接 API  
  
以 node.js 指令為例。  
 
- 一般執行指令是 `node index.js` 這樣可以做到上面提到的 API串接。  
- 如果想要  `node index.js 2` 就直接拿到 SINGLE USER 的 ID 資料 ?  

在 node.js 可以用內建模組 process 引入進來:  
```
const request = require('request');
const process = require('process');

console.log(process.argv)

request(
  'https://reqres.in/api/users/2', 
  function (error, reponse, body) {
    console.log(body);
    }
);
```
- 印出來會是一個 array ， 三行綠字。  
    - 第一行會是 node 的參數。  
    - 第二行會是 index.js (檔案)的參數。  
    - 第三行則是所串接的 API 資料，我們要拿的資料。  
    
- argument vector (argv) 能夠執行一個文件達到多行命令的效果，假設 `node process-args.js 參數1 參數2 參數3` 輸出則會是:  
  0: /usr/local/bin/node  
  1: /Users/mjr/work/node/process-args.js  
  2: 參數1  
  3: 參數2  
  4: 參數3  

- 這個很有用處。假如在 bat 文件這樣寫 node app 127.0.0.1 7001 ， 其透過 `.argv [2]` 得到 IP ， `argv[3]` 得到連接埠，更方便修改配置。  

---

## 直接拿第三個元素  

一樣以 index.js 這個檔案為例:  
```
const request = require('request');
const process = require('process');

// console.log(process.argv)

request(
  'https://reqres.in/api/users/' + process.argv[2], 
  function (error, reponse, body) {
    console.log(body);
    }
);
```
然後執行指令 ` node index.js 2` 我們就能拿串接的 API 資料，會拿到 "id": 2 的 SINGLE USER 資料。  
-  ` node index.js 3` 則會拿到 "id": 3 的 SINGLE USER 資料，以此類推。  

---

## 可以用 POST 去新增 USER  

一樣以 index.js 這個檔案為例。  
參考 [GitHub 技術文件](https://github.com/request/request#forms)，來寫 request 的 Forms :  
```
const request = require('request');
const process = require('process');

// console.log(process.argv)

request.post(
  {
    url:'https://reqres.in/api/users/', 
    form: {
    name:'User',
    job:'Full'
  }
},
  function (error, reponse, body) {
    console.log(body);
    }   
);
```
多按幾次 `node index.js` 指令會看到建立每次 id 都不同的 User 資料。  
- 主要是接  {form:{key:'value'} ， 裡面皆所要串接的 API 。  
- 將 url: http://service.com/upload 置換成 https://reqres.in/api/users/ 。   
- 第一個參數是物件 `form:{}` ， 將 key:'value'  改成 https://reqres.in/api/users/ 所需格式。  
- 並不會真的寫入到 https://reqres.in/api/users/ 的資料，只是模擬寫入 response 這樣。  
---

參考資料:  

[ process.argv命令行參數 ](https://riptutorial.com/zh-TW/node-js/example/10945/process-argv%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%83%E6%95%B8)

[process.argv](http://nodejs.cn/api/process/process_argv.html)

[process.argv与命令行工具](https://juejin.im/post/6844903568365846536)

[引數 (Argument) vs. 參數 (Parameter)](https://notfalse.net/6/arg-vs-param)

[ process.argv 这个有什么用途？ ](https://cnodejs.org/topic/515a40836d38277306084809)

---