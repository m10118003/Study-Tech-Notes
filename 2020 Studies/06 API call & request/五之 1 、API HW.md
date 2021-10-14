# 五之 1 、API HW   
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/15  

基於 API 文件 來呼叫 API ， 寫寫看。  

---
![](https://i.imgur.com/hLjQnFr.png)

---

## HW1 寫程式來呼叫 API 前十本書和書名。  
- Base URL: https://lidemy-book-store.herokuapp.com  
- 閱讀開頭給的 [API 文件](https://github.com/request/request#custom-http-headers) 並串接，用 node.js 寫出一個程式，執行後會在 console 列出前十本書籍的 id 以及書名。  
- 輸出範例:
 ```
node hw1.js1 克雷的橋
2 當我想你時，全世界都救不了我
3 我殺的人與殺我的人
....
 ```
知道怎麼在網址後面接上 `books` 和 `limit` 就好辦多了~
根據提示完整的 API 位址就能列出來。  

```
/* eslint-disable */ // 在該檔案關閉 ESLint
const request = require('request');

request(`https://lidemy-book-store.herokuapp.com/books?_limit=10`, 
  (error, response, body) => {
    if (error) {
    return console.log('抓取失敗', err);
  }
  let data
  try {
    data = JSON.parse(body);
  } catch(error) {
    console.log(error);
    return
  }
  for (let i = 0; i < data.length; i += 1) {
    console.log(`${data[i].id} ${data[i].name}`);
  }
})

```

---

## HW2 串更多 API 。  

請你閱讀開頭給的 API 文件並串接，用 node.js 寫出一個程式並接受參數，輸出相對應的結果，範例如下：
```
node hw2.js list // 印出前二十本書的 id 與書名
node hw2.js read 1 // 輸出 id 為 1 的書籍
node hw2.js delete 1 // 刪除 id 為 1 的書籍
node hw2.js create "I love coding" // 新增一本名為 I love coding 的書
node hw2.js update 1 "new name" // 更新 id 為 1 的書名為 new name
```
這個用到 ``.argv()`` 就比較小複雜，要用判斷式和 ``if...else...`` 或是 `switch` 來進行條件變換:  
```
/* eslint-disable */ // 在該檔案關閉 ESLint
const request = require('request');
const args = process.argv;
const apiUrl = 'https://lidemy-book-store.herokuapp.com';
const action = process.argv[2]
const params = process.argv[3]

switch (action) {
  case 'list':
    listBooks();
    break;
  case 'read':
    readBooks(params);
    break;
  case 'delete':
    deleteBooks(params);
    break;
  case 'create':
    createBooks(params);
    break;
  case 'update':
    updateBooks(params, process.argv[4]);
    break;
  default:
    console.log('Available commands: list, read, delete, create and update');
}

function listBooks() {
  request(`${apiUrl}/books?_limit=20`, (error, res, body) => {
    if (error) {
      return console.log('抓取失敗', error);
	}
    const data = JSON.parse(body)
    for (let i = 0; i < data.length; i += 1) {
      console.log(`${data[i].id}. ${data[i].name}`);
    }
  });
}

function readBooks(id) {
  request(`${apiUrl}/books/${id}`, (error, res, body) => {
    if (error) {
	  return console.log('抓取失敗', error)
	}
    const data = JSON.parse(body)
    return console.log(data.id + '.', data.name)
  });
}

function deleteBooks(id) {
  request.delete(`${apiUrl}/books/${id}`, (error) => {
    if (error) return console.log('刪除失敗');
    return console.log('刪除成功');
  });
}

function createBooks(name) {
  request.post({url: `${apiUrl}/books`, form: {name,}}, (error) => {
    if (error) return console.log('新增失敗', error);
    return console.log('新增成功')
  });
}

function updateBooks(id, name) {
  request.patch({
	url: `${apiUrl}/books/${id}`, 
	form: {
	  name
	}
  }, (error, res) => {
    if (error) {
   	  return console.log('更新失敗', error);
	}
    return console.log('更新成功!?');
  });
}

```
參考了解答和 [同學的筆記](https://hackmd.io/PhfjuTVzQPaiXYMiJ3F4qQ) ， 整理得真的很漂亮 !  
同時看到了 [Swift 起步走](https://itisjoe.gitbooks.io/swiftgo/content/apps/taipeitravel/intro.html)  。  

---  

## HW 3 找現成 API ， 看懂這個 API 和回傳。  

主要是使用這個 [佛心 API ](https://restcountries.eu/#api-endpoints-name)  。  
這個程式很簡單，只要輸入國家的英文名字，就能夠查詢符合的國家的資訊，會輸出以下幾項：
```
    國家名稱
    首都
    使用的貨幣名稱
    電話國碼
```

輸出範例如下:  
```
node hw3.js tai

============
國家：Taiwan
首都：Taipei
貨幣：TWD
國碼：886
============
國家：United Kingdom of Great Britain and Northern Ireland
首都：London
貨幣：GBP
國碼：44
============
國家：Lao People's Democratic Republic
首都：Vientiane
貨幣：LAK
國碼：856
```
用到之前學的  process.argv() 命令行參數來實戰，需要在 node xxx檔名.js + 名稱，例如:  
- `node index.js Taiwan` 就會跑出 Taiwan 的名稱、資訊...等等。 
- 觀察了一下，需要用到結果傳入迴圈來執行 。  
- 同時運用到狀態代碼，並輸出結果。  

```
const request = require('request');
const args = process.argv;
const API_ENDPOINT = 'https://restcountries.eu/rest/v2';

const name = args[2];

if (!name) {
  return console.log('請輸入國家名稱');
}

request(`${API_ENDPOINT}/name/${name}`, (err, res, body) => {
  if (err) {
    return console.log('抓取失敗', err);
  }
  const data = JSON.parse(body);
  if (data.status === 404) {
    return console.log('找不到國家資訊')
  }

  for (let i = 0; i < data.length; i++) {
    console.log('============')
    console.log('國家：' + data[i].name);
    console.log('首都：' + data[i].capital);
    console.log('貨幣：' + data[i].currencies[0].code);
    console.log('國碼：' + data[i].callingCodes[0]);
  }
})
```


## HW4 從 [Twitch_V5 API](https://dev.twitch.tv/docs/v5) 文件中來看如何串 API (備註:這是舊版)。  
```
- 1. 先執行兩部驗證，過程很繁瑣，主要是要在 Twitch ， Account Settings => Security and Privacy => Two-Factor Authentication 給啟用。  

- 2. 接著回 https://dev.twitch.tv/console 設定 Applications ， Name 隨意但不能跟他人重複 ， 然而用這組 http://localhost 在 URL 設定上會出問題，參照 http://localhost:8000/ 這組才能執行。  

- 3. 註冊好後，去按下 Manage Application => 就可以看到 Client ID ， 並且如何用註冊的 Client ID 來玩和加入 request header 就很有趣。
```
```
const request = require('request');
const options = {
  url: 'https://api.twitch.tv/helix/games/top',
  headers: {
    'Client-ID': 'You can't see this ID,
	'Accept': 'application/vnd.twitchtv.v5+json'
  },
};function callback(error, response, body) {
  if (!error && response.statusCode === 200) {
    const info = JSON.parse(body);
    for (let i = 0; i < info.data.length; i += 1) {
      console.log(info.data[i].id, info.data[i].name);
    }
  }
}request(options, callback);


```

---

HW4 參考資料:

[Configuring Onion Services for Tor](https://2019.www.torproject.org/docs/tor-onion-service.html.en)

[關於OAuth 2.0-以Facebook為例](https://medium.com/@justinlee_78563/%E9%97%9C%E6%96%BCoauth-2-0-%E4%BB%A5facebook%E7%82%BA%E4%BE%8B-6f78a4a55f52)

[Twitch streams API 串接實例](https://chriskang028.wordpress.com/2017/07/29/twitch-streams-api-%E4%B8%B2%E6%8E%A5%E5%AF%A6%E4%BE%8B/)

[OAuth 2.0 筆記 (4.2) Implicit Grant Flow 細節](https://blog.yorkxin.org/2013/09/30/oauth2-4-2-implicit-grant-flow.html)

[10分鐘理解OAuth和facebook登入原理](https://gigenchang.wordpress.com/2014/01/26/10%E5%88%86%E9%90%98%E7%90%86%E8%A7%A3oauth%E5%92%8Cfacebook%E7%99%BB%E5%85%A5%E5%8E%9F%E7%90%86/)

[暗網架站首部曲-Tor](https://pincong.rocks/article/699)

[Getting Started with the Twitch API](https://dev.twitch.tv/docs/api/)

[Invalid redirect URI on spotify auth](https://stackoverflow.com/questions/32956443/invalid-redirect-uri-on-spotify-auth)

[Twitch API 串接（一）申請用戶端ID及尋找所需API](https://medium.com/@winny3531/twitch-api-%E4%B8%B2%E6%8E%A5-%E4%B8%80-%E7%94%B3%E8%AB%8B%E7%94%A8%E6%88%B6%E7%AB%AFid%E5%8F%8A%E5%B0%8B%E6%89%BE%E6%89%80%E9%9C%80api-ef4d562fe9b0)

[ 第十七天：怎麼讓別人連到我作好的網站？ ](https://ithelp.ithome.com.tw/articles/10195920)

---

## HW5 簡答題
-----------------------------------------------------------------------------------------------------------------------------------------

## 1.請以自己的話解釋 API 是什麼？  

__應用程式介面 (Application Programming Interface) ， a.k.a. API 。__  

- 介面很重要，透過介面來溝通。  
- 電腦要透過介面存取和溝通。  

因此可以分為使用 API 和提供 API:  

- 不希望直接被存取資料庫。  
- 定義那些資料要被存取。  
- 例如: 作業系統提供 API、檔案透過 API 讀取。  
- 串接 API = 拿取資料。  
- 提供 API 給他人來網站存取資料或是新增資料。  

__重點: 透過 API 即可讓雙方交換資料。__  

-----------------------------------------------------------------------------------------------------------------------------------------

## 2.請找出三個課程沒教的 HTTP status code 並簡單介紹。  

參考了 [MDN 技術手冊 - HTTP 狀態代碼](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Status) 還有 [HTTP 狀態碼 (Status Codes)](https://notfalse.net/48/http-status-codes):  

### 205 重設內容 (reset content)  

- 伺服器接受請求，並且 User 的代理端應重新設置內容。  
- 像是 User 送出表單，結果收到 205 的情況代表瀏覽器希望把表單內容清空。  
- 大概是方便接下來提交新的表單或是美觀要求。  

### 206 部分內容 (partial content )  
- 會產生此狀態是因 User 端送出的範圍標頭 (range header) 將造成下載分流。  
- 將動作 GET 用在範圍請求的情況，像是使 Server 傳輸大型文件的單個頁面。  

### 207 多個狀態 (multi-status, WebDAV)
- 需要多個狀態代碼才能響應傳達有關多種資源的資訊。  
- 用於多個獨立操作來提供不同狀態。  
-----------------------------------------------------------------------------------------------------------------------------------------

## 3.假設你現在是個餐廳平台，需要提供 API 給別人串接並提供基本的 CRUD 功能，包括：回傳所有餐廳資料、回傳單一餐廳資料、刪除餐廳、新增餐廳、更改餐廳，你的 API 會長什麼樣子？請提供一份 API 文件。  。
```
http://www.měishí píngtái.com/
"food_restaurant" [
  {
    "id": "1",
    "food_restaurant_name": "Tamsui_A-gei",
    "food_restaurant_classification": "street_food",
    "food_restaurant_address": "Zhenli street., Tamsui Dist., New Taipei City",
  },
   {
    "id": "2",
    "food_restaurant_name": "TNT",
    "food_restaurant_classification": "western_food",
    "food_restaurant_address": "Zhongzheng E. Rd., Tamsui Dist., New Taipei City",
  },
   {
    "id": "3",
    "food_restaurant_name": "Red Castle",
    "food_restaurant_classification": "chinese_food",
    "food_restaurant_address": "Sanmin St., Tamsui Dist., Taipei City",
  },
   {
    "id": "4",
    "food_restaurant_name": "Shenghong Teppanyaki",
    "food_restaurant_classification": "taiwanese_teppanyaki",
    "food_restaurant_address": "Beixin Rd., Tamsui Dist., Taipei City",
  },
   {
    "id": "5",
    "food_restaurant_name": "Hi-Lai-FOODS",
    "food_restaurant_classification": "all_you_can_eat",
    "food_restaurant_address": "Zhongshan N. Rd., Shilin Dist., Taipei City",
  },
],```| 說明 | Method | path | 參數 | 範例 |
|--------|--------|------------|----------------------|----------------|
| 獲取所有餐廳 | GET | /food_restaurant | _limit:限制回傳資料數量 | /food_restaurant?_limit=5 |
| 獲取單一餐廳 | GET | /food_restaurant | :id  | /food_restaurant/:id  |
| 新增餐廳 | POST | /food_restaurant | 餐廳名稱 | :add |
| 刪除餐廳 | DELETE | /food_restaurant | 無 | 無 |
| 更改餐廳資訊 | PATCH | /food_restaurant | 變更的項目: 內容 | 無 |
```
GET http://www.měishí píngtái.com/food_restaurant/:id 
獲取其中一個餐廳時： GET /food_restaurant/:id 
```
```
GET http://www.měishí píngtái.com/food_restaurant/:add
新增餐廳：POST /food_restaurant/:add
```
```
POST http://www.měishí píngtái.com/food_restaurant/:id 
更替餐廳：DELETE /food_restaurant/:id 
```
```
DELETE http://www.měishí píngtái.com/food_restaurant/:del
刪除餐廳資訊：PATCH food_restaurant/:del
```
```
PATCH http://www.měishí píngtái.com/food_restaurant/:alt
修改餐廳資訊：PATCH food_restaurant/:alt
```

-----------------------------------------------------------------------------------------------------------------------------------------