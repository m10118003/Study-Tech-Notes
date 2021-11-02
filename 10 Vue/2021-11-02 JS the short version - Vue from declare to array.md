# 2021-11-02 JS the short version - Vue from declare to  array   
###### tags: `JS` `Vue` `2021/11/02` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 上午的部分  

# 關於樣版字串或是 JS 的計算  
- 例如每次 BMI 計算機算資料要再按一次更新資料   
- 每次推新的卡片都要做一次清除   

- 之前我的們宣告和抓 DOM 元素可能是這樣   

> ![](https://i.imgur.com/LcoTaZL.png)   


----

# Vue 的變數宣告是像這樣  
>![](https://i.imgur.com/PAQjy10.png)   
> 有一定格式  
> 賦值是用冒號, 而不是用 `=`   
> ![](https://i.imgur.com/sSjmQA7.png)   
> 宣告後在整個頁面中都能使用   

- 使用變數的方式  
- 在 Vue 中打 `script` 然後選  
> ![](https://i.imgur.com/jnxIXkm.png)  
```
<script> javascript.vue
```
> 會幫你生成一個區間   
> ![](https://i.imgur.com/JgPBrrN.png)


> 在 template (html)中用連結變數的話  
> ![](https://i.imgur.com/ogairZw.png)

- 也就是他可以直接串(即時的)  
> ![](https://i.imgur.com/Fqqe1DF.png)   
> ![](https://i.imgur.com/ajIfTZg.png)   

- 那 function 要寫在哪裡呢?  
- "做甚麼" 操作的位置在哪?  
- 但在 Vue 中最重要的問題是 "甚麼時候"   

-----

# Vue 的生命週期  

- 那 methods (是 → function) 和 "做甚麼" 操作的位置一樣在 export 底下, 不過是要在變數宣告的區間 ==`,`== 之後   

> ![](https://i.imgur.com/b67J3S8.png)   

> ![](https://i.imgur.com/r65DLfk.png)   
> 這樣算是一個區間, 區間結束後會用 `,`  

- 函數的宣告  
> ![](https://i.imgur.com/pCdF2iU.png)   

- 練習做個變數宣告, 和給個函數  

- 實際上做出來就會是這樣   
- ![](https://i.imgur.com/Q6lIeGI.png)  
> ![](https://i.imgur.com/m5HmWMx.png)   

> 做完頁面後記得, 因為他不是純 html 檔案, 所以沒法直接用 Vscode 的 ==`Open w/ Live server`== 功能   

- 做完後, 例如本次的 About 練習, 要用 Terminal 的 powershell ==`npm run serve`== 打開
> ![](https://i.imgur.com/gvvPgZZ.png)
> 選 Localhost 8080 這個, Follow link 就會開啟預覽頁面    

- 自己 try 一次  
> ![](https://i.imgur.com/cpO4zJt.png)   
> ![](https://i.imgur.com/di1adC5.png)   

- Vue 的物件   
> ![](https://i.imgur.com/G56BfUx.png)   

# 參考資料 - Vue life cycle  

[1-7 元件的生命週期與更新機制 | 重新認識 Vue.js | Kuro Hsu](https://book.vue.tw/CH1/1-7-lifecycle.html)


[面試官：你對vue生命週期的理解？_Vue中文社群 - MdEditor (gushiciku.cn)](https://www.gushiciku.cn/pl/gkJX/zh-tw)   

[Vue 生命週期 自學筆記 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10232402)  

----

# 試著在 Vue 上做出 BMI 計算機   

# 引入   

- 做一個 bmi.vue 檔案, 丟到 views 底下  
> ![](https://i.imgur.com/Mzg8HPr.png)  
> 把 hmtl 和 scss 丟進去   
> ![](https://i.imgur.com/wsyV91s.png)   
> 看到一些參數, 看不太懂沒關係 
```
像是 src 是 source 之類的參數
```

- 引入
> ![](https://i.imgur.com/qqXPi7w.png)   

> 中間可以看到 lazy-loaded, 如果有人只想看頁面中的兩三頁, 你不想一次載入上百行, 就可以用這個
```
你要用的時候再引入
```

> ![](https://i.imgur.com/lykxB0Q.png)   

---

# 接著做一下  
- BMI 怎麼套樣式  

- 寫出 html 和 SCSS 到 ==`bmi.vue`== 檔案中   
> ![](https://i.imgur.com/Lau5XG1.png)   

- ==`index.js` 中引入 `bmi.vue` 檔案==   
> ![](https://i.imgur.com/QlkLPPP.png)   

- ==`App.router`== 中定義畫面最右上 BMI 連結的位置  
> ![](https://i.imgur.com/iU5BUQl.png)   

---
----

#  指令式程式寫法 vs 渲染式寫法   
- 指令式寫法例如 Dom 你會越寫越多  
> ![](https://i.imgur.com/eWEaO9L.png)   
> 這有個缺點就是會越寫越多  

- Vue 的好處是渲染式寫法  
> ![](https://i.imgur.com/B9nBIF4.png)  
> 每個事件作集中管理(給 state 管理), 然後根據需求去做觸發  
> ![](https://i.imgur.com/jZqzQIf.png)   

# Vue 的功能演進  

> ![](https://i.imgur.com/vIYdNgm.png)   

----

# Vue 中寫 JS  

- 之前寫 JS 可能要一長串 A

> ![](https://i.imgur.com/YQHzmNX.png)   

- 網站打開後, create 到 mount 後, 完成頁面  
> 你可以讓網頁關掉後自動儲存現在的進度  
> 根據你要的甚麼時間點去做甚麼事情   
> 也可以在畫面渲染之前去資料庫拿東西, 然後再去 mount  

> 看時間點, 有非常多的事件可以做  


- 常用的可能是這兩個  
> ![](https://i.imgur.com/TmMLQOX.png)

- 如果寫個   
```
beforeMount() 和  
Mounted
```
> ![](https://i.imgur.com/0UENogQ.png)   

- 這樣就會有時間差(一瞬間)   
> ![](https://i.imgur.com/CyIsGvp.png)   

- 這個從 `beforeCreate` 到 `mounted`   
- 即是 vue 的元件 (component) 掛載完成, 所有東西都可以運行  
> ![](https://i.imgur.com/jVmz3so.png)   

> ![](https://i.imgur.com/y6PYMeC.png)  
 
 - 所以你要用 Vue 的話, 你必須先宣告所有的初始值  
 > ![](https://i.imgur.com/AFFR14K.png)   

----

## 所以要怎麼讓 BMI 計算機動起來?  

- 甚麼時候要動起來?
> 按鈕按下去的時候  
> ![](https://i.imgur.com/xWQwUuP.png)   

- 建立 function 去 load 值  
> ![](https://i.imgur.com/SlGJY7F.png)   

> ==建立 function 有幾個方法去導值進來:==  
1. 原始方法(加入 dom 元素)   
 > ![](https://i.imgur.com/7X5QjeZ.png)   
> ![](https://i.imgur.com/2pXisxd.png)  

2. 然後這個宣告方法要調整  
> 所有的 dom 物件前面都要加上 this  
> ![](https://i.imgur.com/TJWznvF.png)  
> ![](https://i.imgur.com/F7JYYST.png)   
>  ![](https://i.imgur.com/U34QMhK.png)   
> 不過 一般 不會用這種(dom 元素)方法, 不會寫進 querySelector 到 vue 中  

3. 去把要做的事情包起來, `mounted`   
> ![](https://i.imgur.com/2vRJMs4.png)  
> ![](https://i.imgur.com/jtooD0I.png)    
> ![](https://i.imgur.com/gZ4v2g0.png)   


----
 
# 試著讓 BMI 計算機動起來   
 
- 在宣告, `w`, `h`, `bmi` 前面加入 this   
- 把 `.innerHTML` 改成 `consol.log`  

> 自己 try ![](https://i.imgur.com/kgRqWuP.png)   

- `caculate()` 沒有 `()` 也可以動!?  
> 自己 try  ![](https://i.imgur.com/p8aUtai.png)   

- 照課堂範例的寫法, `caculate()` ↓  
> ![](https://i.imgur.com/O0uQo4t.png)   



----

# 下午部分 - onclick 更改  

- 因為是按鈕執行, 綁 onclick 在 html 中  

> ![](https://i.imgur.com/30rge8W.png)   

> 接著把 function 內的待辦事項複製進 bmi.vue caculate() 底下  
> ![](https://i.imgur.com/LySzSmY.png)   

---

- 原本是用 `console.log` 印出到控制台中  
> ![](https://i.imgur.com/btdXCvG.png)   
> ![](https://i.imgur.com/AMwRqU7.png)   

---

- 接著因為 vue 有它的規則, 我們要照他規則走  
> ![](https://i.imgur.com/7Ko7H8M.png)
> 而因為原本畫面輸出是用 innerHTML  
> 為了 import 到 vue 內, 我們先改成 `console.log`   
> ![](https://i.imgur.com/z2S3DUq.png)   

---

- 原本是宣告變數, 然後給他 documentSelector  
> ![](https://i.imgur.com/byTW8td.png)  

---

> 寫到 vue 後, 先宣告變數 ``= ""``  
> ![](https://i.imgur.com/CeU356i.png)   
> 讓他按下按鈕去抓初始值  

---
 
- this 是代名詞(暫時這樣記)  
- 接著用 this 去抓 weight, height, bmi, result  
> ![](https://i.imgur.com/cEsVbxp.png)   

---

- 然後把值加進來  

>  最後就完成了  
>  ![](https://i.imgur.com/jqJOZlm.png)   

---

- var 執行完後, 因為生命週期消失了, 這個 var 也跟著消失了  
> ![](https://i.imgur.com/V4Eckvb.png)   
> 但也是有方法能帶出去!  

----
----


# Vue 的黑魔法指令 - 表單類的指令   
> ![](https://i.imgur.com/2W7Z8vF.png)  

- 現在我們不要這兩行   
> ![](https://i.imgur.com/SSYa3dg.png)  
> 直接被消失的兩行  

---

> ![](https://i.imgur.com/LnzpuIE.png)  
> 不要用 this指向    

---

## 直接綁定 html    
> ![](https://i.imgur.com/abiK5cM.png)   
---
> ![](https://i.imgur.com/jAcatVU.png)   

---

=> 表單控制用 v-model 去綁定表單的值   
> 像是把 `v-model` 參數綁定在 input  
> 比較能應用的就是在表單類的值  
> 是雙向的, 很像 data attribute 的寫法   

---

> ![](https://i.imgur.com/CoRnPtX.png)  
---
> ![](https://i.imgur.com/FNr44YB.png)   
---
> ![](https://i.imgur.com/yUG51Ks.png)   
> 下面程式的值 (export ) 那邊更改, 上面 html 也可以被更動, 可以達成同步化    

---

> 全部自動化, 很方便, 不用去按按鈕和綁事件   
> ![](https://i.imgur.com/yYEXG3y.png)   
> 而且寫的程式碼會非常簡便  


# 參考資料 - V-model  
[「Vue.js 學習筆記 Day2」- v-model資料雙向綁定 | by Pierce Shih | 皮爾斯的自學旅程 | Medium](https://medium.com/pierceshih/vue-js-%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-day2-v-model%E8%B3%87%E6%96%99%E9%9B%99%E5%90%91%E7%B6%81%E5%AE%9A-9d54a82e23e5)  


[Vue.js: data、v-model 與雙向綁定 | Summer。桑莫。夏天 (cythilya.github.io)](https://cythilya.github.io/2017/04/14/vue-data-v-model/)

[用範例理解 Vue.js #13：v-model and data binding - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10193270)

[v-model | Vue.js (vuejs.org)](https://v3.cn.vuejs.org/guide/migration/v-model.html)

---
  
# 樣板修改的問題  
  
- Vue 樣板不能修改在 CSS 屬性這邊  
> ![](https://i.imgur.com/ovhkLXb.png)  

- 如果想做出我們之前的 BMI 計算機
> 有輸出結果的時候有動畫效果要怎麼做?  

- 這時候可以用 v-bind  

----

# 顏面修正的 v-bind  

- 給 html 一個變數值  
> ![](https://i.imgur.com/jNO2MXI.png)  
> 
> 下面 JS 也要用變數值  
> ![](https://i.imgur.com/QAC01vn.png)   
- output 也給一個 show 值  
> ![](https://i.imgur.com/7vqyUPu.png)  

- 也就是可以這樣寫  
- 把按下按鈕的時候給他 show  
> ![](https://i.imgur.com/6xXvBMc.png)   
---
> ![](https://i.imgur.com/zsRUFY0.png)   

- 整體架構  
> ![](https://i.imgur.com/t34MpnY.png)   

----

## 自己 try 一下 各種寫法  
- 指向一般 BMI 計算機, document.querrySelector 的寫法  
> ![](https://i.imgur.com/ubLheJF.png)  

- v-model 的寫法(沒加到 h, w 的 CSS)  
> ![](https://i.imgur.com/aipDmzP.png)   

- v-bind + v-model 的寫法(加入 CSS)  
> ![](https://i.imgur.com/zbb3wCr.png)   
> ![](https://i.imgur.com/vbsGmhe.png)   


----

# 顯示畫面~  

- 還記得前面怎麼印出名字的嗎?  
```
樣板字串用法!
{{}}
```
- 所以我們可以開始直接在 html 上做樣板  
> ![](https://i.imgur.com/e27PqYk.png)   
---
> ![](https://i.imgur.com/fRfDP3h.png)   

- 接著, 你有了 output 顯示在螢幕上  
- 那你之前寫的文字建議也可以顯示, 用 advice  
> ![](https://i.imgur.com/SRpSoBf.png)   
- 接下來就可以顯示 BMI 的東西 !  
> ![](https://i.imgur.com/7j6nlSA.png)  

- 顯示 BMI  
> ![](https://i.imgur.com/V9ugGgp.png)   
> 不用另外宣告  
> 因為是用 state 去驅動的, 所以不用 innerHTML, 都不用另外宣告了~  

- 自己 try  
> ![](https://i.imgur.com/jOqv9UP.png)   

---

# 清除畫面~   
- 先把 show 給拿掉  
> ![](https://i.imgur.com/yIJleRs.png)  
- 再來是數值   
> ![](https://i.imgur.com/2kRxFVp.png)   

- 自己 try 一下  
> ![](https://i.imgur.com/tLX6gpi.png)  
> 綁定 `@click 到 html`, 並且渲染有畫面   
> ![](https://i.imgur.com/rTp4kt5.png)   
> Reset, 因為綁定 `@click`, 並導至 `clear()` 清空畫面  
> ![](https://i.imgur.com/n1fXzya.png)  



---

# 小結一下  
```==
v-bind 改 HTML 屬性用
v-model 表單數值雙向連動 
{{ }} 直接同步輸出變數
```

---

# Vue 條件判斷 / 
```
常常會有一種狀況, 今天判斷一個東西, 
但他今天不是需要的就不用印出, 這時候要怎辦?  
```

----

# 明早講 SEO(搜尋優化) / Google Analytic 學科  
> 概念, 實作很複雜  

----

# 明天學科後有一對一訪談  
- 對這堂課的發想....  
- 目前的想法...   
- 比較不擅長的項目  
- 分組依據, 考量  

-----

---

# Tab 改法  
- 用之前寫的分頁標籤來改  
- 改 route~  
> ![](https://i.imgur.com/CRQQh56.png)  

---
- 改頁面顯示位置  
> ![](https://i.imgur.com/BCjWGso.png)   

---

- 接下來就是寫 html, css, js~   
> 放好 html,  css  
> ![](https://i.imgur.com/uPBDEY0.png)   

---

- 讓他有頁面可以分  
> ![](https://i.imgur.com/xYHxYOr.png)   

---

- 頁面內容也有順序   
> ![](https://i.imgur.com/3GuvP5U.png)  
---
> ![](https://i.imgur.com/UvxZa34.png)   

---

> ![](https://i.imgur.com/WBRBIGs.png)   

- 讓他按按鈕可以換頁面  
> html 綁上點擊事件    

---

> ![](https://i.imgur.com/0UFRvA8.png)   

---

- 接下來讓分頁按鈕發光  
> ![](https://i.imgur.com/euCDeRT.png)   
---
> ![](https://i.imgur.com/jQRcXFJ.png)  
---
> ![](https://i.imgur.com/Kqm8EqW.png)   

---

- 單純用 now 就會全部都發光  
> ![](https://i.imgur.com/0NV5Fny.png)  

---

- 分頁按鈕比較秀的做法  
> ![](https://i.imgur.com/tB6sGLg.png)   
> 可以給值後用 for loop  

----

- 開始用 if   
> ![](https://i.imgur.com/LRqrIql.png)   

---

> 老方法
> ![](https://i.imgur.com/isjPSoy.png)   

- show 是 class 屬性, :" 是變數名稱"
> ![](https://i.imgur.com/SxmVcjY.png)   

![](https://i.imgur.com/WyuTnPi.png)



- 土法煉鋼法  
- 改按鈕和分頁  
> ![](https://i.imgur.com/SWu2nvj.png)   
- 改分頁發光  
> ![](https://i.imgur.com/UYbfvZQ.png)  

![](https://i.imgur.com/LHdeInC.png)   

- 以上是 lazy load 作法  
> 不一次全 load 整個頁面 / 烤肉 不一次全出  
> 先拿一部分資訊 / 先上一部分肉盤給你  
> 剩下的頁面資訊慢一點再出來 / 剩下的料慢慢給  

# 參考資料 - lazy load  
[Lazy loading - Web Performance | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/Performance/Lazy_loading)   

[Lazy loading - Wikipedia](https://en.wikipedia.org/wiki/Lazy_loading)   

[透過 lazy loading 延遲載入圖片. Lazy… | by Ming-jun | Medium](https://medium.com/@mingjunlu/lazy-loading-images-via-the-intersection-observer-api-72da50a884b7)   

[Lazy Load 延遲圖片載入，讓網站更順暢 - 香腸炒魷魚 (sofree.cc)](https://sofree.cc/lazy-load/)   

[圖片延遲載入外掛 Lazy Load__Blogger 最佳安裝方式＠WFU BLOG](https://www.wfublog.com/2012/05/lazy-loadblogger.html)   


---

## 而 v-if 和 v-show 的性質都會消失  

- 但是使用 v-if 的話, 本身元素會不渲染   
- 直接拔掉元素   
- 在 html 上不會顯示     
> ![](https://i.imgur.com/BQQvpUs.png)  
> ↑ 會變一行註解   

- 不過用 v-show, 畫面就算沒有符合條件  
- 都會渲染出來  
- ![](https://i.imgur.com/IkcCcT3.png)  
> 一樣會消失, 像是傳統用法 display none    

-----
-----

# 篩選菜單跟分頁 - 商品清單改法  
- 陣列用法  

- 頁面增加商品清單的分頁  
![](https://i.imgur.com/ATW3ZSY.png)   

---

- 增加 route     
> ![](https://i.imgur.com/KQ1yyyP.png)   

---

![](https://i.imgur.com/6srPeXI.png)

- 基本測試, 看按鈕有沒有出來  
- 再來是看圖片有沒有出來  
- ![](https://i.imgur.com/6QoiX2G.png)   

---

- 將整個卡片根據 v-for 去印  
> ![](https://i.imgur.com/PHibXwd.png)  

---

> 但需要索引值 (index) 作根據去印  
> ![](https://i.imgur.com/KYtMt7Z.png)  

----

- 接著根據樣板字串  
> ![](https://i.imgur.com/cmWpYb0.png)   

---

- 連 show 都不用就能印出來了  
> ![](https://i.imgur.com/B1DuQ8J.png)   

----

> ![](https://i.imgur.com/Oy9RL0o.jpg)   

----

- 最好不要同時使用  v-for 和 v-if  
> ![](https://i.imgur.com/A87V5nt.png)   

---

- 改個做法 
> ![](https://i.imgur.com/5WN0Y3D.png)  
> 這樣才能上 v-if  

----

> ![](https://i.imgur.com/rOPMoXE.png)  
> 接著 讓 rule = all  

----

> ![](https://i.imgur.com/O8OTdwx.png)  

---

![](https://i.imgur.com/oOLcKhZ.png)  

---
![](https://i.imgur.com/jCzyJo1.png)   


--- 

# 重理一遍  
1. 類似樣板字串, 和印出來的功能  
> ![](https://i.imgur.com/BAQpOAM.png)   

2. 產品給個值 = 索引值  
> 用 v-for, 根據 SY_goodgoodEat_Product 的長度  
> 去印出 html 樣板  
![](https://i.imgur.com/w0Ww6zF.png)  

----

> 接著用 v-if 決定此區塊要不要顯示在版面上  
> ![](https://i.imgur.com/Yfakjlt.png)   

---

> 因為 div 沒有給高寬, 所以這樣寫  
> ![](https://i.imgur.com/Kn70Fi6.png)
> 其實為了安全給個 display none 比較好   


3. 新的規則給予規則  
> ![](https://i.imgur.com/xtdLbim.png)   

4. 好好吃 → 產生 `<p>`  換成 產生 食物卡片 這樣  

----


# Vue 陣列取值  
> ![](https://i.imgur.com/B78zAIL.png)   

> ![](https://i.imgur.com/QGr5oX5.png)  

-----

# 參考資料 - Vue 學法    
[Alex 宅幹嘛 - YouTube](https://www.youtube.com/c/AlexOtakuWhat/search)   

[重新認識 Vue.js | Kuro Hsu](https://book.vue.tw/)   

----