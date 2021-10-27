# 2021-10-27 Bootstrap - Login and cart page matters   
###### tags: `Bootstrap` `JS` `2021/10/27` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 早上的部分 - 網頁資料夾管理  

- 多個網頁就像多個檔案  
> 會在一個資料夾下, 有所有的 hmtl 檔案, 一個 CSS 資料夾..等等  
> ![](https://i.imgur.com/yDa4JBq.png)  

```
把所有的 CSS / SCSS 檔案, 
放在同一個 CSS / SCSS 資料夾內
```

> 進階一點的話會再分資料夾內的排序  

---

# 引入的時候會越來越多  
## 相同樣式不重複從不同檔案引入  
> ![](https://i.imgur.com/A5nj2FW.png)   

> ![](https://i.imgur.com/y7fwXRW.png)  

- 如果網頁相同的樣式部分很多  
> 可以只取不同的地方, 多加一個 class    
> ![](https://i.imgur.com/dJPNGHx.png)   
> 看重複的東西有多少, 在 SCSS 用 `&` 的方式去做引入  
> 可以覆蓋掉  
> ![](https://i.imgur.com/7DmFstF.png)   

- 將你重複的樣式只寫在同一個 CSS, 例如進度條
> ![](https://i.imgur.com/bb2Rcnt.png)    
1. 在不同的 HTML 上, 針對你重複的地方, 相同的 Class name 下多另外一個 Class, 例如 step-01   
> ![](https://i.imgur.com/18nlMPP.png)   
2. 在 SCSS / CSS 檔案上多寫這個另外的 Class, step-01   
3. 當你用 a 連結換過去另外一個網頁的時候, 另一個網頁去吃這個 step-01 的 屬性  

# 參考資料  
[CSS 的引入方式有哪些?. 有 4 種方式可以在 HTML 中引入 CSS。 | by 余小魚 | Medium](https://medium.com/@small2883/css-%E7%9A%84%E4%B8%89%E7%A8%AE%E5%BC%95%E5%85%A5%E6%96%B9%E5%BC%8F%E6%9C%89%E5%93%AA%E4%BA%9B-58dc7570bb9c)   

[CSS 引入方式 - SegmentFault 思否](https://segmentfault.com/a/1190000003866058)   

[CSS引入方式及區別 (firbug.com)](https://www.firbug.com/a/202110/1303095.html)  


----

# 實作不同網頁套用相同樣式  
## 複習一下天鵝的用法  

> ![](https://i.imgur.com/CHyIs9j.png)   
> 每個地方加個 class, step-01, step-02...等等   

- 這樣可以用同一個 SCSS, 讓四個不同網頁套用這個相同屬性  
> ![](https://i.imgur.com/SOTd92J.png)   
> 然後在對的位置套用對的屬性, 例如進度條  

> ![](https://i.imgur.com/93eDjEP.png)  

- 這邊示範讓每一頁的 html 一樣, 不過  
> ![](https://i.imgur.com/IuaLe4H.png)   
> 進度條後面的 class 不一樣, 多了 step-01  
> 不同頁面多了不同的 額外 class  

- 因為大部分樣式都一樣   
- ![](https://i.imgur.com/GjFa2Pt.png)  
> 只有線圖, 和圓標的部分不一樣   
> 所以只要針對這個改就好  

- 可以用 `&` 去區別, 可以讓 HTML 的結構都接近  
> ![](https://i.imgur.com/laEynAp.png)  
> 在 CSS 比較不一樣的位置去改就可以  

----

# 或是更精簡  

![](https://i.imgur.com/RDstEvF.png)   

![](https://i.imgur.com/7uVJKUc.png)   

----

# 使用 CSS 框架的問題  

1. HTML 比較冗長, 可能會不太好維護, 因為樣式會很長  
> 但也有這種做法  
> ![](https://i.imgur.com/jSMKkuu.png)  

2. 裡面的屬性權重全是 `!important`   




---

# 複習 BS 變版的設定  

> ![](https://i.imgur.com/PQO50mP.png)  
```
lg > 992px 的時候會套用
md > 768px 的時候套用
```

----

# 下午的部分 - CSS 的東西  
假設不同頁面有共通元素  

> ![](https://i.imgur.com/D1YT5e0.png)

- 假設上方顯卡和下面 "你的選擇" 是不同頁面  
> ![](https://i.imgur.com/aShbDLW.png)   

- `&` 可以用在不同頁面選相同元素上   
> ![](https://i.imgur.com/Ymc5IjE.png)   
> 可以把前面所寫的東西連接起來  
> ![](https://i.imgur.com/DcDTUiX.png)  
> 可以把 good 和 last-child 連在一起  
> 除了連結偽類外, 也可以連接其他屬性  
```
如果是在 & 下面
例如 & img (不要有空格 
```

- 也可以把 class 串在一起  
> ![](https://i.imgur.com/TFQA2Oc.png)  
> 可以吃到上一個屬性  

- 應用在 hovcer  
> ![](https://i.imgur.com/zn2uIYv.png)   
> ![](https://i.imgur.com/iDB6vrZ.png)   
> 可以不用從頭開始寫  

1. 這樣可以更有系統性質  
2. 寫起來也比較簡短  
3. 也比較好讀  

----

# 複習 SVG 用法  

- 新增 svg 檔案  
> ![](https://i.imgur.com/vt9SYbo.png)   
> 把 SVG 的路徑放進去這個檔案  
> 用 img 把它 load 進來  
> ![](https://i.imgur.com/bALngzj.png)  
> 這樣比較方便以後可以換檔案  
> 比較好維護  

----

# 爆版的狀況  

- 出現下方也卷軸的情況就是有點爆版  
> ![](https://i.imgur.com/Y5idKlF.png)   
> 如果用 md-4 就會是 4x4 = 16, 變成 16 格  
> 如果設了 flex, 子層有東西的情況下, 就會壓縮父層  
> ![](https://i.imgur.com/Lo8SVOo.png)   
> 如果用 md-3 就會進去了  
> 要讓 footer 空間滿十二格欄位  
> ![](https://i.imgur.com/aHpl8JX.png)  

- 所以要讓 8 / 4 = 2   
> ![](https://i.imgur.com/e6yWsUR.png)  
> 可以限制字數  
> 或是不讓左邊的 文字跟右邊文字排在一起  

- 一般情況 col-md-4 的情況  
> ![](https://i.imgur.com/ouHfxpu.png)  
> 這樣會滿版  

- 記得 container 下面有 row 再來才是 col  
> container 左右各有 15 padding  
> ![](https://i.imgur.com/AgiDD2P.png)  
>![](https://i.imgur.com/WmC7WfB.png)   
> 總大小要算一下, 不然會超過就爆版惹  

---

# 首頁的部分  

- col-6, 3, 3 圖片要怎麼擺~  
> ![](https://i.imgur.com/q9nbE5l.png)
> 順序位置  
> 左上先, 再來是右上, 最後是 600x360  

----

# 專案開發概念  

1. 要用 Bootstrap 還是混合用之前在先進行構想  
2. 注意 Bootstrap 的規則~  

----

# 進階挑戰  
- 數位方塊的進階切版(Recruitment ques)  
> 要可以 input  
> ![](https://i.imgur.com/2GC7DvT.png)  
> 按下去要能上傳圖片, 留言, 刪除留言    
> 但那是要跟後端傳遞圖片  
> 可以不 AJAX 和 Fetch 就傳圖片嗎?  

- 那麼要怎麼用呢？
> ![](https://i.imgur.com/ACIuCMZ.png)  
>  上傳檔案也可以用 input !  
>  ![](https://i.imgur.com/OSyrh17.png)   
> 也可以指定 w3c 所定義好的 media type  
> ![](https://i.imgur.com/vlWgM5i.png)  
> ![](https://i.imgur.com/Al0jNno.png)   

- 沒加 accept 的話, 就可以上傳檔案(不指定類型)  
> ![](https://i.imgur.com/tGJZCoc.png)  



- 應用 `createObjectURL`  
- ![](https://i.imgur.com/WNZBFJi.png)  
> 用 img.src 去改成 URL 接 dom object  
> ![](https://i.imgur.com/XDfihIN.png)  
> 也可以考慮多個檔案上傳的情況  
> ![](https://i.imgur.com/vReATRl.png)  
> 拿進去的圖片或檔案會是預設陣列  
> ![](https://i.imgur.com/NqnXldP.png)   

> 那怎麼去選好圖片, 可以使用 eventListener  
```
change envet
```
> ![](https://i.imgur.com/jl26ofH.png)   
```
參數
你要做甚麼, 做甚麼事情
```
> ![](https://i.imgur.com/lepFsnp.png)  
```
this
如果用 this 就會指向你的 function 
```
> ![](https://i.imgur.com/oNYnqgb.png)  
> ![](https://i.imgur.com/Hsb2P4i.png)
```
blob 這個開頭代表這次上傳的檔案後, 幫你新增一個網址給你預覽
```
> ![](https://i.imgur.com/Wm6MYhU.png)   

1. 好處是不會存在 cookie 內  
2. 除了對資安安全, 關掉網頁就會清空  

> ![](https://i.imgur.com/UDmII9I.png)  


# 參考資料 - ObjectURL  
[URL.createObjectURL() - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/URL/createObjectURL)  

[EventListener - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/EventListener)   

[this - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)   

[MDN現提供Deno相容性資料 | iThome](https://www.ithome.com.tw/news/146360)   


----

# 題外話 - Node.JS 也能開發後端  

[Node.js 是什麼？NPM又是什麼？為什麼前端與後端都需要用它們呢？ (progressbar.tw)](https://progressbar.tw/posts/291)   

[Node.js-Backend見聞錄(09)：關於後端觀念(五)-關於框架-Express - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10194773)

----  

# 後端 MVC  
![](https://i.imgur.com/78doWHP.png)   
> 前端, 畫面呈現  
> 後端, 資料處理  
> 前端資料接收後回傳 / 輸出  


- MVC 架構  
> MVC是個建議 / 概念   

1. Write in Model  
> Code writing / Design and management data-base  
2. See the View  
> 你切版后的東西, UI 設計在 view 的這個概念 / 畫面的處理
3. Control w/ request  
> Process request   

![](https://i.imgur.com/TcOB07n.png)   

----

# 盡量把數位方塊的頁面切完  
- 講 View 觀念的時候就可以帶到  

- 來不及趕稿的話先, 寫購物車兩頁, 趕 mock up  

----