# 2021-10-20 JS fetch,  detect color game, json form   
###### tags: `JS` `2021/10/20` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師  

---

# 早上的部分  

- 網頁的部分因為, 資料其實是不會存在網頁上的   
- 都是存在後端的系統  
- 前端是怎麼跟後端聯繫的方法   

# 參考資料 - 直接操作 dom 的問題  

[前端为什么操作 DOM 是最耗性能的呢？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/324992717)   

[总结js常用的dom操作（js的dom操作API） (haorooms.com)](https://www.haorooms.com/post/js_dom_api)  

[為什麼放棄jQuery | IT人 (iter01.com)](https://iter01.com/542147.html)  

----

# 現代前端跟後端串接資料的方法   
- 談一點網頁架構   
- http 通訊協定  
```
是主從式的架構, 是以送出請求的這個動作
去登入 server 去拿取東西(資料)的這種方式
```
```
還有 P2P, BT 沒有主從式的架構, 可以彼此交換資料
```

> 要如何傳資料給 server  

# 參考資料 - HTTP  
[HTTP基本介紹. WWW | by 陳品宏 | Medium](https://medium.com/@lion6396643/http%E5%9F%BA%E6%9C%AC%E4%BB%8B%E7%B4%B9-42fcf9333285)

[https://zh.wikipedia.org/wiki/超文本传输协议](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)

[簡介 HTTP 協定 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10217426)

[HTTP | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/HTTP)

[一文搞懂 HTTP 和 HTTPS 是什麼？兩者有什麼差別｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/http-https-difference)

[鳥哥的 Linux 私房菜 -- 基礎網路概念 (vbird.org)](http://linux.vbird.org/linux_server/0110network_basic.php)

[了解 HTTP/2 的特色與 HTTP/1.1 的差異 | 星辰網站知識 - 尋找網頁設計前必讀的好文章 (the-allstars.com)](https://the-allstars.com/knowledge/site-build/68-about-http2-and-http11.html)


---

---

# 如何跟 Server 溝通 ?  

- 會使用 form 的形式  
> ![](https://i.imgur.com/5C6EuYF.png)   

- 其實對 Server 請的這個動作有點像是請櫃檯小姐幫忙  

- 跟他說出的請求( GET, POST), 你要找誰(甚麼東西, 資料或是 url)然後她會跟你說, 這個要找誰(給你個目標)~  

- 通常後端拿到資料會存起來, 然後再回傳一個訊息回去  
> 例如資料存起來 ↓  
> ![](https://i.imgur.com/fQtlAsH.png)   

> 例如, 回傳訊息 ↓    
> ![](https://i.imgur.com/cQsGQd8.png)  

- 例如以 youtube 為例   
> 開啟 youtube 後, 會先以 JS 幫你先傳一個請求  
> JS 傳請求給 server 後, 就會先幫你把卡片, 欄位那些顯示出來   
> 再顯示圖片文字, 畫面~  
>  ![](https://i.imgur.com/7KM5Wl4.jpg)  

# 參考資料 - 動作  
[HTTP介紹和HTML簡介 | IT人 (iter01.com)](https://iter01.com/576585.html)

[HTTP基本知識 - IT閱讀 (itread01.com)](https://www.itread01.com/content/1541135009.html)

----

# Fetch 後端跟前端溝通  

- 用 input tag 的時候 
> 他的 name 就會帶有資訊(參數)給後端  
> ![](https://i.imgur.com/fLV0636.png)   
> 可以跟 host 做聯繫, 去代資料   

> 例如你在一個表單輸入資料  
> ![](https://i.imgur.com/pHagery.png)   

- 他會在 server 端有這樣子的資料接收  
> ![](https://i.imgur.com/WqhKv5r.png)   

- 假設你改了 city  
> 然後再輸入到 form table  
> ![](https://i.imgur.com/obuA3AZ.png)  
> 他就會幫你做一點小改變  

- 就會是

- 到時候的 vue 框架會有點小後端的概念   

# 參考資料 - input 代參數   
[基礎訓練－－(04)HTML資料傳遞與Server後端接收 @ 台灣的Web工程師 :: 痞客邦 :: (pixnet.net)](https://akuma1.pixnet.net/blog/post/224677216-%E5%9F%BA%E7%A4%8E%E8%A8%93%E7%B7%B4%EF%BC%8D%EF%BC%8D%2804%29html%E8%B3%87%E6%96%99%E5%82%B3%E9%81%9E%E8%88%87server%E5%BE%8C%E7%AB%AF%E6%8E%A5%E6%94%B6)  

[HTML的 id 和 name - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10243720)   

[後端基礎概念：php 與 資料庫基本知識. 什麼是後端？ | by Hugh's Programming life | Medium](https://hugh-program-learning-diary-js.medium.com/%E5%BE%8C%E7%AB%AF%E5%9F%BA%E7%A4%8E%E6%A6%82%E5%BF%B5-8643ca1f5315)   

[從前端傳資料給後端（GET, POST）、從 PHP 連線到 MySQL 資料庫 (coderbridge.io)](https://saffranblog.coderbridge.io/2021/02/25/get-post/)   

[Form與常見的element. 什麼是HTML Form | by JiaHung Lin | Medium](https://medium.com/@pk60905/form%E8%88%87%E5%B8%B8%E8%A6%8B%E7%9A%84element-35e08e760da2)   

[後端如何給 <input type="text" id="tt" name="tt" .> 值- 藍色小舖 BlueShop](http://www.blueshop.com.tw/board/FUM20041006161839LRJ/BRD20100731204203D0F.html)   

[HTML <input> 表單元件 - HTML 語法教學 Tutorial (fooish.com)](https://www.fooish.com/html/input-tag.html)   

----

# 使用 Fetch  
- 在 js 中, 與 server 溝通, 其中一種方式是以 fetch  
- 是一種異步請求  
> ![](https://i.imgur.com/2Mw2lxl.png)   
> 使用 fetch  的好處是可以不用重新整理頁面  
> 例如 youtube, 可以不用重新整理頁面, 然後一直往下讀取  
> ![](https://i.imgur.com/qWC4biy.jpg)   


# 參考資料 - AJAX 與 Fetch  

[AJAX與Fetch API · 從ES6開始的JavaScript學習生活 (gitbooks.io)](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/ajax_fetch.html)

[web中的同步请求和异步请求的差别(重点是ajax中的同步与异步)_前端小白-CSDN博客_ajax异步请求和同步请求的区别](https://blog.csdn.net/u014516981/article/details/53243564)

[什麼是 Ajax？ 搞懂非同步請求 (Asynchronous request)概念｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/ajax-asynchronous-request)


---

# Fetch 格式  

![](https://i.imgur.com/zd90vOR.png)  

- 要送的資料選在, fetch 下面  

- 例如以天氣 API 的方式去做 fetch 
> fetch 回來的資料會是一個 http 的 response  
> 會跟你說你跟誰請求資料的狀況, 成功或失敗等等的狀況  
> 會有很多屬性
> response 的 資料會給瀏覽器去看 , 例如這就是結果 ↓  
> ![](https://i.imgur.com/iwCPynB.png)   

- 例如這種回來, recall 的就是 json 格式的資料  
> ![](https://i.imgur.com/GGPKMwq.png)  
>會顯示各個縣市 ↓  
>![](https://i.imgur.com/StXSxJG.png)  


> 會顯示詳細資料...等等  
> ![](https://i.imgur.com/AEaxp5J.png)   
> 資料都會在 json 的請求結果中  

---

# 印天氣的卡片 - 氣象局拿資料  

- 首先 html  
- 放卡片的空間   
>  ![](https://i.imgur.com/r48MFH6.png)  

## 天氣卡片的需求  

- 需要有這些資訊  
- 要根據降雨機率去輸出對應的資訊以及圖片  
> ![](https://i.imgur.com/L8k277R.jpg)   

- 先暫停, 等等講 練習以 json 形式印出卡片  

[課後任務](#課後任務)


----

# 檢討 json 形式印出卡片  

- 陣列內的格式會影響印出的形式   
> ![](https://i.imgur.com/AHsaEOj.png)   
> 例如, "紅燒牛肉麵 ", "滷肉飯 "後面多了個空格, 會影響跑出來  

---

# 檢討找色塊遊戲  


![](https://i.imgur.com/BuwXCqh.png)   

- 倒數結束的時候做一個 block  
> ![](https://i.imgur.com/MXl1NHv.png)    
> ![](https://i.imgur.com/vGmfwoC.png)   
> ![](https://i.imgur.com/JiQoE5I.png)   

----

## 加上註解會比較清楚  

> ![](https://i.imgur.com/LktAiWY.png)   

> ![](https://i.imgur.com/Zi1SqUW.png)  

> ![](https://i.imgur.com/8tfigWf.png)   

---

# 呼叫倒數計時  

- 先宣告一個變數去儲存倒數計時器 timer
> ![](https://i.imgur.com/SW6l6Mk.png)  

- 最後才有辦法停止  
> ![](https://i.imgur.com/AfotgUL.png)  

---

# 先宣告所有會操作的 dom 或變數  

- 這樣之後拿來操作會比較好用  
> ![](https://i.imgur.com/QOia06l.png)   
> function 就像是待辦清單懶人包  
> 在裡面列出 to do list 就會幫你去執行   
> 你要做的事情, 幫你記錄下來  
> 等你去執行遊戲的時候就會開始做   

---

# function 複習  

- 假設以天氣預報   
- 那個(2)  就是狀況   
> ![](https://i.imgur.com/vA33euN.png)   

- 例如晴天的狀況   
> ![](https://i.imgur.com/g1b0aWQ.png)   

- 所以你可以根據 天氣(誰)的 "狀況(甚麼時候)"
![](https://i.imgur.com/oPeuaGf.png)   

- 等到要做這件事情, 像是要去便利商店(要做甚麼)的時候去把這個待辦清單拿出來  

----

# 長出方塊的狀況  

1. 可以長大邊框, 但也可以縮小邊框內的方塊   
> ![](https://i.imgur.com/COvmxaI.png)  
> ![](https://i.imgur.com/5q14SS7.png)   
> 設定寬高才能長出方塊  
> ![](https://i.imgur.com/0o7ocZK.png)   

- 整體長方塊狀況  
![](https://i.imgur.com/7Mij5DI.png)  
> 如果 95 沒有清空(舊的)方塊, 他就會一直往下長出方塊   
> ![](https://i.imgur.com/VVqq1Kh.png)   

- 用到 Math.random 的狀況  
> ![](https://i.imgur.com/F2tIKGc.png)  
> 因為你有個設定值, 假如是 9x9, 也就是 81  
```
那他生成的亂數無限趨近你的設定值, 0~80.99999999999999999
```
- 再加上 Math.floor 就會去掉小數  
```
這樣就會是 0~80  
```

- 應用  
```
Math.floor(Math.random()*49)+1
這樣就會是 1~48

```

# 下午的部分 - 繼續複習色塊  

# 如何印出方塊   

![](https://i.imgur.com/WkzwYAe.png)  

---

# 如何檢查方塊有沒有被按對 !?  

![](https://i.imgur.com/1h2hQUZ.png)   

----

# 如何讓遊戲在時間內結束 ?  

> ![](https://i.imgur.com/gr3pTQF.png)   
> 每秒都在執行 timeruning
----

# 實際上這樣跑一遍  
- 可以發現都是宣告!  
> 包含 function 在內都是  

- 可以畫個流程  
- 打開網頁後!   
> ![](https://i.imgur.com/FshN51f.png)   
> 把一件大的粉複雜的事情, 分成幾個小事情  
> 再從小事情去找出怎麼做   

---

# 如果畫面的指令被 alert 卡住的話  

![](https://i.imgur.com/VRq9gtv.png)  
> 用個 settimeout 在背景執行, 這 alert 就不會擋到  

---

# 課外  

可以跟工程師溝通, 可以用工程師的話講(轉譯)  
不只可以跟工程師, 業主講, 還能告訴額外的資訊(下一步)給業主   

----

# 檢討練習用 json 格式去製造卡片欄位  

![](https://i.imgur.com/UQl9lVf.png)    

![](https://i.imgur.com/T5ZZy47.png)

![](https://i.imgur.com/boAuXFI.png)   


----

# 課後任務    
- 天氣預報的卡片切版  
- 降雨機率  
- 天氣預報  
> ![](https://i.imgur.com/50SlSZi.png)   
> layout 的時候可以填上一下假資料   

> ![](https://i.imgur.com/fq161Kn.png)   

> ![](https://i.imgur.com/Bzkt6j6.jpg)   

[印天氣的卡片 - 氣象局拿資料](#印天氣的卡片---氣象局拿資料)

----