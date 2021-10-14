# 9/29 CSS -  plug in 介紹   
###### tags: `CSS3 基礎實作` `2021/09/29` `進度筆記` `前端心得`  
---

# 今日講課 -- 上午的部分 -  Microsoft old hompage - carousel discussion    


# 做完的試著研究 AOS - plug in 用法   
[https://michalsnik.github.io/aos/](https://michalsnik.github.io/aos/)    

---

# Carousel 檢討   
找到父層的 div 位置   
![](https://i.imgur.com/LiOKoaB.png)   

↓ 小螢幕, 1083px 的時候會變小   

![](https://i.imgur.com/wd6j6Zz.png)   

如果沒變小, 記得去 CSS 把 Swiper    

---

手機版的時候會變大   

![](https://i.imgur.com/pnAnG7W.png)   

調整 high  

![](https://i.imgur.com/Wjnj9P6.png)   


----

# 滑鼠移到圖片上會顯示出左右按鈕   

![](https://i.imgur.com/j59cIAQ.png)   

## 先幫他加上圓形外框   

- 找到 swiper-button   
![](https://i.imgur.com/kQi9i8X.png)   

- 開以拉看一下   
![](https://i.imgur.com/F45pPE2.png)   

> 給他個背景顏色和大小   
![](https://i.imgur.com/CXtHf66.png)    



- 把按鈕的文字 ">"  "<"  弄小   
> 觀察 CSS 結構, 發現是 after 的樣式   
![](https://i.imgur.com/nuYJlan.png)   

![](https://i.imgur.com/c3vjCGA.png)   

----

# CSS 陰影  - box shadow   

- 幫按鈕上陰影   
![](https://i.imgur.com/2pz09pt.png)   

↓ 跟以拉的陰影有點像, 開以拉來看   
![](https://i.imgur.com/cUxkAtr.png)  


通常設計師有用以拉的話會在以拉內的圖片放圖案的陰影, 可以照著寫一下   
![](https://i.imgur.com/SxI9CM9.png)   

↓ 然後他是 hover 的時候陰影更深   
X 偏移 量大, 然後多給一個擴散半徑   
![Uploading file..._737v13opc]()   


↓ 如果調整擴散半徑會超糊   
![](https://i.imgur.com/4vP8Swk.png)   

↓ 用 dev tool 去實際操作一下, 就非常像了   ![](https://i.imgur.com/AwACEJ9.png)   

↓ 然後 hover 的時候才有陰影   
![](https://i.imgur.com/LpnDUZk.png)  
> hover 的時候才有陰影   


↓ 當 Swiper hover 的時候, 裡面的按鈕會跑出來  
![](https://i.imgur.com/96C3nYE.png)   


↓ 把按鈕貼邊, 往上調整, 按鈕的定位看起來是各有一個 auto   
![](https://i.imgur.com/yfrEGgo.png)   

↓ 左邊離左邊是 0, 右邊離右邊是 0 就上去了  
![](https://i.imgur.com/C1rGNeO.png)   


# 分頁按鈕是 div   
- 觀察一下   
↓ 如果要微調, 找 Swiper pagination, 權重很小    
![](https://i.imgur.com/HMcNI72.png)  

---

↓ 調整分頁按鈕大小   
![](https://i.imgur.com/lqdJxMA.png)  

↓ 有 active 的時候分頁按鈕本身是黑色的,  而background-color 是淡灰色   
![](https://i.imgur.com/Cyh185L.png)   

↓ border 調整一下   
![](https://i.imgur.com/WdgRoDu.png)   

---

# 下午的部分 - 研究 AOS - plug in 用法   
- 套件如果沒有用 js, 用 CSS 寫的話, 可以用權重去覆蓋(調整 CSS 位置)   

- 卷軸動畫套件(Animate on scroll library)   
 
 - 引入套件試試看, 別忘了寫註解~   

![](https://i.imgur.com/MZWWZy9.png)   

---

# Initialize AOS   
- 啟用這個套件~   
![](https://i.imgur.com/3NeRTPQ.png)   

---

# Set data-aos   

![](https://i.imgur.com/DQYGFPK.png)   

---

# 設定背景, 畫個方塊一下~  
沒有反應, 因為這個 aos 是滾動到某個程度的時候才會有作用, 來加個 banner  

![](https://i.imgur.com/hm5pmIf.png)   
↑ 記得給 box 上個 background-color~  


# 可以給複合的屬性   
delay 50 → 0.05s   
![](https://i.imgur.com/CVqcXzT.png)   

> 會延遲才跳出~   
![](https://i.imgur.com/BU43rOu.png)   

# 全域改變  

全部都延遲 0.05s   

![](https://i.imgur.com/o6tP9VG.png)   

----

# animejs.com   

- 有點像引擎, 要改 js  

[anime.js • JavaScript animation engine (animejs.com)](https://animejs.com/)   

![](https://i.imgur.com/eafuy2n.png)   

----

# animate.css   
- 純CSS plug in  

[Animate.css | A cross-browser library of CSS animations.](https://animate.style/)   
> ↑ 首頁有示範一些效果   

==# 參考資料:==   
[【Day 26】CSS Animation - CSS 動畫資源蒐集與使用教學 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10251903)   

[微動畫簡單做！使用 animate.css 五秒提升作品質感](https://blog.infographics.tw/2016/11/animate-css/)  

[jQuery 筆記 - Animate.css 套件基本認識 | TimCodingBlog (hsuchihting.github.io)](https://hsuchihting.github.io/jQuery/20200713/60669434/)   

[都給我動起來! Animate.css 分享 - 客座投稿 | W3HexSchool](https://w3c.hexschool.com/blog/b800f62e)   


---

# require  

- 引入 CDN  
![](https://i.imgur.com/PT0BvTF.png)   

- 用 class name 的方式加上 CSS  style   
![](https://i.imgur.com/4CIWVIu.png)    
> 添加 animate_animated 到 class as initialize  

---

# 第二種 require 方式  

- 可以用 @keyframes 的方式去啟用   

- 先不定義 @keyframes 去看看  
![](https://i.imgur.com/DUsP72v.png)  

可以直接看到動畫效果, 因為引入的 CDN 已經幫你自動加入 @keyframes 的作用了   

*使用的時候記得把前綴刪除*   
```
animate__wobble
↑ 刪除這個前綴 animate__
```

![](https://i.imgur.com/bLOZAr5.png)   

---

# 全域變數   
==`:root` 可以讓所有的動畫效果都吃到效果==   
![](https://i.imgur.com/pIrGDOR.png)  

---

# 也可以加入後綴   

![](https://i.imgur.com/QTo9urv.png)   

---
---
---
---

# hover.css  

- 有些 plug in 沒有提供 CDN~  
- 要用下載的方式   
[Hover.css - A collection of CSS3 powered hover effects (ianlunn.github.io)](https://ianlunn.github.io/Hover/)   

---

# 下載後用個新創資料夾 dist 裝你的 plug in    
![](https://i.imgur.com/CkxUYCe.png)   


↓ 可以看到裡面有很多檔案   
![](https://i.imgur.com/Qe7T1ag.png)   
> 蠻肥大的   

---

- initialize  
> 實際上要用的只有這隻檔案   
![](https://i.imgur.com/26iPChf.png)   

- 可以複製出來另外用  
![](https://i.imgur.com/m3Z3aNT.png)   

- 像這樣 ↓  
![](https://i.imgur.com/hIuVAjs.png)   
> 然後刪掉你下載後不需要的其他 CSS 檔案   

- 展示:   
![](https://i.imgur.com/IRMiWcG.png)   

- icon 是用 fontAwsome 的~   
![](https://i.imgur.com/60mK6Ae.png)   

---
---
---

# Website style guide  
- 定義了按鈕大小, 顏色, 設計   
- 一個優秀的網站有主色, 輔色, 不會有太多的顏色和過於花俏   
- 大概不會超過十種顏色  
![](https://i.imgur.com/LbwZ4GQ.png)   

# ==參考資料:==   

[Project style guide template by Ivan Bjelajac for Five on Dribbble](https://dribbble.com/shots/2688568-Project-style-guide-template)  

---

# Sass / SCSS 的宣告方法   

==參考資料:==  
[30天掌握Sass語法 :: 2013 iT 邦幫忙鐵人賽 (ithome.com.tw)](https://ithelp.ithome.com.tw/users/20040221/ironman/562)   

[30天掌握Sass語法 - (3)如何透過「變數」提升撰寫CSS效率 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10127206)  


---
---
---

- 先在另外一隻檔案 `_variables.sccs` 宣告變數:   
- 要有意義的命名變數~  
![](https://i.imgur.com/h0Uqblg.png)   

---

- 使用方法:  
![](https://i.imgur.com/oMY5mGg.png)   

![](https://i.imgur.com/GR2nU51.png)   
> 不過沒顯示出來~!?   

---

# 沒顯示是因為要引入外部檔案: @import  

# ==參考資料:==   
[30天掌握Sass語法 - (5)利用Sass「@import」進行CSS檔案模組切割 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10127832)   


- 編譯方式:  

- - 做模組化的引用  
- - 加入@import   
![](https://i.imgur.com/UNJwui2.png)   

---

![](https://i.imgur.com/wPiLbQN.png)   

---

![](https://i.imgur.com/9Tbl2ZN.png)   

![](https://i.imgur.com/k0bsNeU.png)   

![](https://i.imgur.com/JbZF4RF.png)   

---

# 文字也可以模組化 - @import     
在 _variables.scss 中定義好   
![](https://i.imgur.com/AgMKJnJ.png)   
定義好後~   
![](https://i.imgur.com/bL8dyXF.png)   

去正在寫的 scss 檔案中, 用 @import 可以引入, 把變數拿進來用   
![](https://i.imgur.com/PUGiYUm.png)   

---

# scss 可以定義 @mixin   
# ==參考資料:==   
[30天掌握Sass語法 - (6)利用Sass「@mixin」，讓你省去重複撰寫相同CSS樣式的時間 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10128138)  

[Sass:@mixin指令介绍 | Sass中文网](https://www.sass.hk/skill/sass142.html)  

 - @mixin (mixin 混入, 混合) 的用法   
 - 可以包含任意數值, 並且傳遞參數!  
 - 相較 @extend 更有彈性   
 - 如果要使用相同的 CSS 片段, 且不被相關元素所拘束限制, 可以用 mixin, 他可以用在任何地方   
- @mixin size() 定義了一組變數, 專門用來控制寬高圓角   
![](https://i.imgur.com/xkDAsDy.png)   

![](https://i.imgur.com/rMbQ4DW.png)   


- @include size() 可以連到 @mixin, 之後就可以拿去用:  
![](https://i.imgur.com/Qp6aCMl.png   )

![](https://i.imgur.com/fZfbetR.png)   

- 邊框變成圓角     
![](https://i.imgur.com/wqMtqXc.png)   

## 宣告定義位置   

- 先定義:   
![](https://i.imgur.com/VpvthmP.png)   

- 修 html  
> 多加一個 span   

- 然後讓 span 水平垂直置中   
![](https://i.imgur.com/rzFDudZ.png)   


- 結果   
![](https://i.imgur.com/i0m58lY.png)   

---

# 比較少用的 @extend   
# ==參考資料:==   
[30天掌握Sass語法 - (7)利用Sass「@extend」，讓你無痛合併CSS樣式 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10128359)   

[SASS : extend繼承 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10204606?sc=iThelpR)   

[Sass教程 Sass中文文档 | Sass中文网](https://www.sass.hk/docs/#t7-3)   
  
[鐵人賽 26 - 實戰心法 - 應避免的 Sass @extend (https_wcc723.github.io)](read://https_wcc723.github.io/?url=https%3A%2F%2Fwcc723.github.io%2Fcss%2F2016%2F12%2F26%2Fsass-extend%2F)  

[Sass：@mixin和@extend该如何选择 | Sass中文网](https://www.sass.hk/skill/sass141.html)  

- extend 延展, 常用來借用或省略重複的屬性與數值(key & value)  
- 可用來製造 dry css(相同的樣式在不同的選擇器內有重複內容的發生)   
- 但問題是, 無法傳參數到 extend 內   
- 而且會把增加選擇器間的聯繫, 把他們堆在一起! 造成維護比較困難   
- super-h1 寫了跟 h1 重複的屬性   
- 但 super-h1 可能還有其他顏色, 像是 border 和 background-color   

![](https://i.imgur.com/FhkZIDx.png)   
- 可以用 @extend 去借 h1 重複(或是想要)的屬性, font-size, font-weight, color   等     
![](https://i.imgur.com/lk8D24e.png)   


- h1 加了 % 後, 這個 CSS 選擇器的屬性就不會被顯示, 然後被借用到其他人那      
> 你想要的重複或是拿過來的屬性, 使用 @extend % 的用法就可以拿到~   
![](https://i.imgur.com/Jjup17O.png)   

![](https://i.imgur.com/QRtpMFH.png)   



----

# Sass / SCSS 進階用法   

## 色相環 套法   

# 更改一下 html    
- 多一個按鈕   

![](https://i.imgur.com/A9phniR.png)   


# SCSS 多一個新增按鈕的顏色  

- lighten 色相環玩法~   
- 有點像用 CSS hsl   

![](https://i.imgur.com/Q4vrAw8.png)  

---

![](https://i.imgur.com/esEZbLJ.png)   

![](https://i.imgur.com/jIcKLxa.png)    

- 讓他亮一點   

![](https://i.imgur.com/Vs8ok28.png)   

- 但不能太亮, % 值 過高顏色會消失   
![](https://i.imgur.com/ZNl0vkQ.png)   

---

# 可以快速幫忙做出用在 hover 的顏色  
- hover 變亮  
![](https://i.imgur.com/EEFu2RS.png)  

- active 的時候變暗   
![](https://i.imgur.com/Ke2tGkf.png)   


> 再丟個 cursor pointer 就會移到按鈕上有手掌符號~   

![](https://i.imgur.com/bflfBpE.png)   


---
---

- 自己玩一次~  
![](https://i.imgur.com/H95KpYy.png)   

![](https://i.imgur.com/O4VTMWV.png)   

- 做 hover, 移動上去變色   
![](https://i.imgur.com/8JeukId.png)   

![](https://i.imgur.com/E2FipIg.png)   



---

# 進階困難玩法 - for 迴圈   
```
for(var n = 1; n < 10; i++ ) {
    print * 
}

i = 1 的情況, 且 i < 10 印出一個 *
i++ 代表 i = i+1 

i=1 拿到一個 *
i=2 拿到一個 *
...
......
i=10 超過 拿不到 * 

所以拿到 9 個 * 
```

# JS 和 SCSS 都有迴圈可以用, 但 CSS 沒有迴圈!   

- to 例如 `1 < 10` 
- through 例如 `1 <=10`  
![](https://i.imgur.com/MH3jwoX.png)   

- 實作 一下  


![](https://i.imgur.com/Hvi5Ipx.png)


四欄位排版  
寬度 = 100 / col 數量的值  
![](https://i.imgur.com/cvfQHw3.png)   
那六欄位就要 / 6   
![](https://i.imgur.com/TRR43ER.png)   
八就 / 8 .... @#%@#!@   
![](https://i.imgur.com/eHxogBR.png)  

---

==以此類推, 慢慢寫固定 % 很麻煩==   

- 所以可以用迴圈   
![](https://i.imgur.com/q5NjxQw.png)   

- 這樣代表 讓 i 從 1 跑到 10, 所以是↓  
![](https://i.imgur.com/ATaTwIn.png)   
> 會一路印到 10   

----

- 那會想, 能不能用算的, 我們讓寬被計算, 100% / i 試試看?  
![](https://i.imgur.com/b2nvaAR.png)   


- 印出來看看 ↓   
![](https://i.imgur.com/YSrSuBA.png)  


> 他一樣印了 i 這個數值 十次!   

- 這是因為 SASS/ SCSS 他不知道 i 是甚麼
![](https://i.imgur.com/TdPR0K9.png)   

- sass/scss 內不用用到 cal, 直接寫出來就行了  
![](https://i.imgur.com/JeJRFPq.png)   


- 那他就會幫你算出, 你跑了 10 次寬度去除以 1, 2, 3...到 10 的數值    
![](https://i.imgur.com/MYrzTgE.png)   



---
---

# 也就是說, 我們不能只讓 i 去跑, 要定義 i  
# ==參考資料:==   
[Sass教程 Sass中文文档 | Sass中文网](https://www.sass.hk/docs/)   

那如果把 i 加上 $, 我們用上變數$      
![](https://i.imgur.com/9uxekeV.png)  
> 會發現有錯, 如果要把變數 $ 用在 width/$i 以外的地方   

- 要用 ``#{}`` 這樣可以轉成 strings   
![](https://i.imgur.com/Mbyup3k.png)   

![](https://i.imgur.com/ehaHxMv.png)   




- 這樣一來他會幫你定義出欄位的數字(數值被轉成字串了)!

![](https://i.imgur.com/cmIU4dz.png)   


---
---
---

# 應用這個寫法到產生欄位   

- 所以可以應用到幫忙來長 SCSS 樣式  
![](https://i.imgur.com/QhZwMR6.png)   


這樣的話, 

![](https://i.imgur.com/LbAUgEZ.png)

![](https://i.imgur.com/r0wTCgU.png)   

- 自動幫你生成欄位 ↓  
![](https://i.imgur.com/32O7era.png)    

---

四欄位 六欄位 八欄位排版都有了   

![](https://i.imgur.com/31wnpwG.png)   

![](https://i.imgur.com/sfE9415.png)   

- 自己試一次:  
![](https://i.imgur.com/ivHlXEo.png)   

---

再多一個三欄位的排版也有了   

![](https://i.imgur.com/hOnKydq.png)   

![](https://i.imgur.com/AMp0IeD.png)   

![](https://i.imgur.com/U0M5Zkh.png)   

- 自己試一次:  
![](https://i.imgur.com/ZORX1J3.png)   


---

