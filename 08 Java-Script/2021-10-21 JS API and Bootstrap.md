# 2021-10-21 JS  API and Bootstrap   
###### tags: `JS` `2021/10/21` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 早上的部分  

# Ajax 概念  

- Ajax 是 Asynchronous JavaScript and XML 的縮寫   

> 過去較流行的是 jQuery 的 ![ajax()](http://api.jquery.com/jquery.ajax/)        

- 之前還沒有 html5 /css3, 有使用 jQuery 來使用非同步的狀況  - jQuery 使用上會越來越少, 其資源消耗也比較大   

- JS 成熟之後, 有許多新的替代方法產生, 例如  
![ ``axios:``  Promise based HTTP client for the browser and `node.js` ](https://github.com/axios/axios)  

- 或是現在最常使用的, 如 HTML5 提供了
![Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)   

- Fetch 使用上跟 `$.ajax` 使用上相近  

# 參考資料 - AJAX 與 Fetch  

[AJAX與Fetch API · 從ES6開始的JavaScript學習生活 (gitbooks.io)](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/ajax_fetch.html)

[web中的同步请求和异步请求的差别(重点是ajax中的同步与异步)_前端小白-CSDN博客_ajax异步请求和同步请求的区别](https://blog.csdn.net/u014516981/article/details/53243564)

[什麼是 Ajax？ 搞懂非同步請求 (Asynchronous request)概念｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/ajax-asynchronous-request)

[鐵人賽：ES6 原生 Fetch 遠端資料方法 | 卡斯伯 Blog - 前端，沒有極限 (wcc723.github.io)](https://wcc723.github.io/javascript/2017/12/28/javascript-fetch/)   

---

# Fetch 使用方式 - 天氣狀況  

- 中央氣象局大概隔很長才會更新一次  

- 使用 Fetch 的時候, 藍色部分不太會改動
- >  ![](https://i.imgur.com/KQPj1Am.png)      

![](https://i.imgur.com/olpXrDY.png)   


![](https://i.imgur.com/axgzlyJ.png)   

- 中央氣象局的 API 位置  
> [https://opendata.cwb.gov.tw/api/v1/rest/datastore/F-C0032-001?Authorization=CWB-B5282D9D-8FDD-40E9-AD48-B1DF3270465D](https://opendata.cwb.gov.tw/api/v1/rest/datastore/F-C0032-001?Authorization=CWB-B5282D9D-8FDD-40E9-AD48-B1DF3270465D)   

- 通常會這樣寫  
> ![](https://i.imgur.com/s1nnTZD.png)   

- 成功的話就會 call 到一堆資料  
> ![](https://i.imgur.com/6JrvomF.png)  
> 不過有需要查文件的地方  

---

# 需要查詢文件的狀況   

- 例如這個 POP, wx 是甚麼  
![](https://i.imgur.com/Szgssql.png)   

- 可以上開放平台做查詢  
> [政府資料開放平臺 | 政府資料開放平臺 (data.gov.tw)](https://data.gov.tw/)  
>> 找到 [資料主題 (cwb.gov.tw)](https://opendata.cwb.gov.tw/dataset/observation/O-A0003-001)   
>>> 開啟 |  [說明資料](https://opendata.cwb.gov.tw/opendatadoc/DIV2/A0003-001.pdf) |  


- 可以試著 fetch  
> ![](https://i.imgur.com/uVWCtnU.png)   

- ![](https://i.imgur.com/l2rW1Mn.png)   
> 網址的換行會出點狀況   
> 可以用 `+` 強制換行  
> 不過比較常用底線去做兩個位置表示  

- 可以一直 then 下去  
> ![](https://i.imgur.com/yoOvRmb.png)  

- 如果對 json 宣告  
> ![](https://i.imgur.com/CPoEjbx.png)  
> 會出現 promise 會很難作使用  
> 然後會再弄個 function 作接下來的處理  
> promise 比起變數更像 function  

- 自己試一下~
> ![](https://i.imgur.com/3QEmyL5.png)  


# 參考資料 - 天氣狀況  

[Using Fetch - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Fetch_API/Using_Fetch)

[JavaScript Fetch API 使用教學 - OXXO.STUDIO (oxxostudio.tw)](https://www.oxxostudio.tw/articles/201908/js-fetch.html)  

[資料主題 (cwb.gov.tw)](https://opendata.cwb.gov.tw/dataset/observation/O-A0003-001)   

[AJAX與Fetch API · 從ES6開始的JavaScript學習生活 (gitbooks.io)](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/ajax_fetch.html)

[DAY 24. JavaScript Fetch API - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10194107)   

[JavaScript基本功修練：Day28 - Fetch練習(GET和POST請求) - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10252941)   


---

# 對 fetch 內作一些事情  

> ![](https://i.imgur.com/UGT9a2s.png)  
> 會 undefined 
> 因為 
```
.then 開始是個 function 外面會無法取用到值
```
```
fetch 是併行處理的
所以 console.log 的時候上面的值可能還沒處裡完
```

- 那要怎麼得到 promise 的 result 呢?  
> ![](https://i.imgur.com/yULqD5M.png)   
> 所以通常不會寫在外面 作 call back function  

- 這樣可以抓到宜蘭縣  
> ![](https://i.imgur.com/UVazjZ4.png)  

- 試著抓一下縣市名稱~  
> 自己 try   
> ![](https://i.imgur.com/N0zI94N.png)   


----

# 網路上有很多讀取 JSON 的方法  

- 因為 JSON 格式可以到非常複雜  

- 例如 [https://jsonpathfinder.com/](https://jsonpathfinder.com/)  / [jsonpath online evaluator](https://jsonpath.com/)   

- 或是 [Online JSON Viewer (stack.hu)](http://jsonviewer.stack.hu/)   

```
用
console.log(JSON.stringify(weather))
把物件轉陣列後去使用
```
> 陣列後  
> ![](https://i.imgur.com/H107USE.png)   

----

> 丟到整理(工具)網站  
![](https://i.imgur.com/v9FtwJA.png)   
> 會幫你整理  
> 資料大的時候好用  

----

# 中場休息  

---

# 試著把宜蘭縣資料串上  

- ![](https://i.imgur.com/BwPcH9z.png)  

- 開始串資料  
> ![](https://i.imgur.com/E6z5oww.png)  
> ![](https://i.imgur.com/w7Viro8.png)  

- 完整的串出一個天氣卡片  
- 一個一個串完  
> ![](https://i.imgur.com/MuEiIg9.png)  

> ![](https://i.imgur.com/8cuNMl6.png)  

- 串完後可以發現  
> ![](https://i.imgur.com/DOwHyuk.png)   
> 很多重複的  

- 所以可以用代名詞 (變數 variable) 去代替  
> 像是這樣  
> ![](https://i.imgur.com/2tQpMkL.png)  

----

# 完成後可以練習串圖片  
- 圖片的條件  
```
當降雨機率 <= 30% => 晴天(太陽圖)
30% < 當降雨機率 < = 60% => 陰天(太陽圖)
當降雨機率 > 60% => 下雨(下雨圖)
```

![](https://i.imgur.com/8Gm6iT0.png)   

- 基本處理好了後可以增進圖片, 動畫  
- 這是個很好的處理資訊, 看 API 的能力訓練  
- 可以做出不見的作品
- 大數據後 > python 抓資料  

- 如果用 SVG 檔案m 去做圖形綁點擊事件  
- onclick 要綁數值傳進去就比較多東西要處理  

---

# 下午的部分   

# 串圖片   

![](https://i.imgur.com/jtsFxc3.png)


![](https://i.imgur.com/86gWHEN.png)  

- 如果用 css 來寫網址的位置就很難做修改  
> ![](https://i.imgur.com/4LijFVc.png)
> 修改會很不方便, 每次新增/修改都要動到 CSS  

----

# 用 inline style 去切換圖片  

- 需要後端配合的'方法  
- 也可以上網址  
> ![](https://i.imgur.com/A43iBEl.png)

----

# 接著用 if 來判斷切換圖片   

- 一開始用 if   
> ![](https://i.imgur.com/7cZmyp1.png)   
> 後面可以再精簡化  

-----

# 可以把所有東西精簡化!  

- 將陣列做變數儲存  
> ![](https://i.imgur.com/IfHlny3.png)  
> ![](https://i.imgur.com/Q3ldznJ.png)   

> ![](https://i.imgur.com/8YdV4jR.png)   

----

# 可以用 for loop 把東西包起來  

- for loop 的長度就是 location 的長度  
> ![](https://i.imgur.com/iDNKM83.png)   
> ![](https://i.imgur.com/njstsPB.png)   
> ![](https://i.imgur.com/AfmsH5M.png)    


- 如果用 = 賦予, 會出現最後一個個縣市蓋過所有值  
> ![](https://i.imgur.com/Is6ORf8.png)  

- 把所有的 index 替換 location[7] 的位置  
> ![](https://i.imgur.com/Ilwbc5e.png)
> 記得做出累加 `+=`

----

# 如果都好了可以去看一下 
[Bootstrap · The most popular HTML, CSS, and JS library in the world. (getbootstrap.com)](https://getbootstrap.com/)   

[Bootstrap 5 繁體中文文件 - 六角學院 · 使用全球最流行的前端開發工具 Bootstrap，快速設計及自定義響應式網站，其擁有豐富的 Sass 變數與 mixins、響應式網格系統、大量預設元件以及強大的 JavaScript 插件。 (hexschool.com)](https://bootstrap5.hexschool.com/)   

----

# 如果用 innerHTML   
> ![](https://i.imgur.com/TMkPyRY.png)    
> 沒有宣告的話   
> 因為是 innerHTML 他會去幫你抓 html 上的 .content  

---

# 如果每個值都要跑  

- 你就可以用 for each  
> ![](https://i.imgur.com/E1K9u9t.png)  

- 如果你要取到值, 就要稍微思考一下  

- for 的玩法  
- for loop   
```
for (let i = 1; i <= 11; i++) {
	console.log(i)
可以印出 1~11
}
```
- 但如果是 for each  
- 沒辦法直接這樣做  
> for each 的話要用到陣列才能跑  
> ![](https://i.imgur.com/i5eO4AB.png)   
> ![](https://i.imgur.com/e2qGYxU.png)   
> ![](https://i.imgur.com/ZHBO77a.png)   
```
number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
array.foreach((e, i) {
	console.log(i + 1)
})
```
> 這樣的話會是 0~ 10  

> ![](https://i.imgur.com/7qmWZI7.png)  

# 課堂練習  
- 內容: 完成天氣卡片的製作   
- 需有: 顯示基本資訊(天氣狀況/氣溫)    
- 須根據降雨機率呈現不同圖片    
- 須至少有1個偽類效果(:hover)   
- 須至少有1個動態效果 (css animation或JS套件也可)    

----

# What is bootstrap  
- Framework, 為了要完成某個 task  
> 你需要甚麼功能?  
> 你需要甚麼工具?  
```
如果要蓋房子, 不可能從原料開始製作, 
一定會跟個個廠商買材料, 這樣會比土法煉鋼來得快很多 ! 
```

- 自動化  
- 減少編寫的時間  

---

# 使用之前  
- 先引入框架系統!  
- 目前上課用 4.6 版本  
- 現在 4.X 還是蠻多人用的  
- 4 跟 5 差別在部分命名  
![](https://i.imgur.com/nIIocXC.png)  
```
5 版本也會修正一些問題, 例如在特定語句前加上 bs
```

- 如果你今天引入的是 4.6 的版本!  

> ![](https://i.imgur.com/HM8k7rL.png)
```
那必須要搭配使用的是 4.6 版本的 文件!
```
> 要選擇相對應版本的文件來對應版本 !   
> Bootstrap 的底層會用到 jQuery, 所以你可以寫加 jQuery  
> 不過, 5 版後應該沒了  
> 盡量使用原生 ES 6 寫法!  


- 記得, 因為底層有用到 jQuery !  
> 所以引入的行數要注意  
> ![](https://i.imgur.com/ZBA36uH.png)   
```
code.jQuery....這一行必須在 cdn 的前面 ! 
```

- 自己試一下  
>  ![](https://i.imgur.com/9XZKPEz.png)  

# 連 RWD 都幫你引入了  
- 如果你只加個 container ...

> ![](https://i.imgur.com/MXbtUBx.png)   
> 可以看到 RWD 效果   

---

# Bootstrap 是建立在網格系統的  
- 主要是十二欄位  
- 最大值是 1140px  
- 所以會幫你預留旁邊兩邊的寬度  
	-   方便切版  
	-  限制寬度  

- 十二欄位例如 ↓  
[東京都中央卸売市場 (tokyo.lg.jp)](https://www.shijou.metro.tokyo.lg.jp/)  
> 左右兩邊的背景, 會拿來扣除某些特定螢幕寬度空間   
> 通常網頁都會注意寬度, 比較不會注意長度, 因為可以一直往下滾動  
> 扣除寬度的限制, 這樣會比較好做 RWD  
> 因此在更寬的螢幕, 像是 2K 背景就會更大   
> 十二欄位會因為視野的寬度, 去設計視野的限制範圍   
> 十二欄位常應用在 PC, 但到了平板、手機 不適用十二欄位  
```
因為十二欄位套在平板、手機蠻精細的, 所以設計師會自由發揮, 例如: 4 欄, 6 欄
```

- Bootstrap 也幫你實作了 Grid system   
> ![](https://i.imgur.com/Pmls3nS.png)  
 
> ![](https://i.imgur.com/7biURa1.png)   

----

# 用網格系統排出一個網球場  
- 用 col 來排~  
- Total height 是 2400px  
- Total width 是 1140px
- 底色綠色  

> ![](https://i.imgur.com/TvQ63af.png)  
> 不能用 CSS 寫XD 
> ![](https://i.imgur.com/wQaI0q9.png)   

- 怎麼解決?  
- 先分幾排  
> ![](https://i.imgur.com/h2iKoOe.png)   
> ![](https://i.imgur.com/FftriJq.png)   

- 找顏色!  
> ![](https://i.imgur.com/9L67Eg4.png)   
> ![](https://i.imgur.com/BL3Ihf6.png)   
> ![](https://i.imgur.com/aZsQoAj.png)   

- 找線框顏色   
> ![](https://i.imgur.com/pMQbC2E.png)   
> ![](https://i.imgur.com/hxdqh0Q.png)   
> ![](https://i.imgur.com/pbObc0g.png)   

- Done  
![](https://i.imgur.com/xffoykM.png)   
> 列出 class 來作到畫面生成~  

- 自己 try  
> ![](https://i.imgur.com/kTEdvX7.png)   
> ![](https://i.imgur.com/ag1s6bp.png)   

---

# 練複製貼上  
![](https://i.imgur.com/ikRxT5o.png)   

---

# Bootstrap 的設定是 min-width  


![](https://i.imgur.com/U2mjr93.png)   

- sm 
- 500 以上的時候變  
![](https://i.imgur.com/qon2Fkg.png)  

- lg   
- 992 以上的時候變兩個   
> ![](https://i.imgur.com/M6f7YjI.png)   

- 裡面內建好了一堆東西   
- 可以在 html 下一堆東西  
![](https://i.imgur.com/A0O0b6m.png)   
> bootstrap 的很多值都有 ``!important``  
```
所以不一定改得動, 應該說幾乎  
```

- 權力遊戲, 要比權重很難!  
> ![](https://i.imgur.com/SR7Xwfi.png)   
> ![](https://i.imgur.com/3vkH00b.png)  
> 如果沒有辦法打贏他, 就加入他一起用! 
```
!important
```

# 回家作業 - 試著用 Bootstrap 去切微軟?!    
- 微軟 width 最大值 超過 1140px  
> 變版時間點不太一樣  
> 微軟他是 1600px  
```
或者是可以用 !important  
```
> 4 變 2, 2 變 1  
> 因為被框架固定了, 所以客製化難度高  
> 不過有些元件好用, 像是彈跳視窗  

- 內容: 使用boostrap提供的元件  
- 去完成微軟官網架構的仿切   
- 外觀不須完全一樣   
- 但變版方式與架構需一致   

- 兩個禮拜  
- 購物車  
- 一個公司頁面  

- 比較 cheap 的 case 可能會用  
- 客製化的設計, 注重設計理念的公司可能會少用  

# 參考資料  - 框架  

[Day21 - 何謂框架? - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10248882)

[Bootstrap · The most popular HTML, CSS, and JS library in the world. (getbootstrap.com)](https://getbootstrap.com/)   

[Bootstrap 5 繁體中文文件 - 六角學院 · 使用全球最流行的前端開發工具 Bootstrap，快速設計及自定義響應式網站，其擁有豐富的 Sass 變數與 mixins、響應式網格系統、大量預設元件以及強大的 JavaScript 插件。 (hexschool.com)](https://bootstrap5.hexschool.com/)   

[從0開始學習架構和框架，零基礎小白入門絕對要看 | 數據分析不是個事 (medium.com)](https://medium.com/%E6%95%B8%E6%93%9A%E5%88%86%E6%9E%90%E4%B8%8D%E6%98%AF%E5%80%8B%E4%BA%8B/%E5%BE%9E0%E9%96%8B%E5%A7%8B%E5%AD%B8%E7%BF%92%E6%9E%B6%E6%A7%8B%E5%92%8C%E6%A1%86%E6%9E%B6-%E9%9B%B6%E5%9F%BA%E7%A4%8E%E5%B0%8F%E7%99%BD%E5%85%A5%E9%96%80%E7%B5%95%E5%B0%8D%E8%A6%81%E7%9C%8B-7f3b1bd90b34)


[軟體框架 \- 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/wiki/%E8%BB%9F%E9%AB%94%E6%A1%86%E6%9E%B6)   

[8.2 程式語言的框架 - 基礎教材 (f5ezcode.in)](https://docs.f5ezcode.in/cs-basic/di-ba-zhang-gong-cheng-de-gong-ju/8.2-cheng-shi-yan-de-kuang-jia)   

[軟體框架和軟體架構的區別？ \- IT閱讀 (itread01.com)](https://www.itread01.com/content/1548028476.html)   



[從一個軟體開發經驗，看整個人生. “Frameworks are bad; libraries are… | by Heron Yang | Heron’s Blog 海龍的部落格](https://blog.heron.me/%E5%BE%9E%E4%B8%80%E5%80%8B%E8%BB%9F%E9%AB%94%E9%96%8B%E7%99%BC%E7%B6%93%E9%A9%97-%E7%9C%8B%E6%95%B4%E5%80%8B%E4%BA%BA%E7%94%9F-1f4694090d25)


----