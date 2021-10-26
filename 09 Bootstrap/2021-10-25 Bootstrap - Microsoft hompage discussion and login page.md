# 2021-10-25 Bootstrap - Microsoft hompage discussion and login page   
###### tags: `Bootstrap` `JS` `2021/10/25` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 早上的部分 - 微軟的仿切  

- Bootstrap 十二欄位的寫法有些限制  
- 沒法太隨心所欲  
- 在專案開始前會評估要不要使用框架, 使用的 Bootstrap 是那些版本  
- 有沒有其他套件會跟 Bootstrap 相衝   
- 如果要在 IE, 就要考慮到 Vue 還有 Bootstrap 的相容問題   
```
BS 市佔率 5X %, 很多業界通用化規格都會用到  
```
```可以省 2/3 的工, 剩下的 1/3 要花兩倍力氣去配合刻出來(?  
```
> 可以有需要要用到 BS 的地方, 再用 BS 就好  

- 4.6 版的因為沒有 5 版的 ``-bs-`` 前綴  
![](https://i.imgur.com/tFEU6sy.png)   
> 改的時候要注意共通的 class name  
> 五代前面有加個 bs   
>   ![](https://i.imgur.com/TpCOSai.png)   
> 4.6 坑蠻多的  

----

# 看同學的範例    

# 找色塊 - 計時器  
![](https://i.imgur.com/24WKI1w.png)   
> 因為每按一次開始就會扣一次秒數  
> 按十次就按十秒!  
> 所以開始後蓋起來開始按鈕   

---

# 同學的範例  

![](https://i.imgur.com/IH3DDSP.png)  
> header → conatiner → section  

- 有手機變版的選單  
> ![](https://i.imgur.com/8wTwDet.png)   

- 寬高用父層定位, 用 padding  
> ![](https://i.imgur.com/iSKKFzr.png)   
> 文字換行可能會跑掉  

- 中間三卡片可以左右對齊, padding  

- 複製 Bootstrap 的 col 的時候有 rem  
> ![](https://i.imgur.com/gFrU4c7.png)   
> 複製的時候有寬高或是其他數值記得刪除, 或覆寫   
> rem 會造成寬高問題, 爆版   

----

# 同學的範例 - 2 

- BS 的結構 → container 再來是 row 下面才有 col  
> ![](https://i.imgur.com/T48Lefk.png)  
> 如果沒 container 就會被 row 的屬性蓋掉  

- id 命名注意  
> ![](https://i.imgur.com/EMM3YVn.png)  

- col 都有照寫法規定~  
> ![](https://i.imgur.com/rOfGD7t.png)  

- 適用於商務  
> ![](https://i.imgur.com/HsWhfct.png)   
> 適用於商務包在四個卡片內的 container  
> ↑ ![](https://i.imgur.com/4FyBUDV.png)   

- icon 也可以放在 container 內  
> ![](https://i.imgur.com/26dm2LJ.png)  
> 就會橋過去  

- footer 也是要從 container → row → col  
> ![](https://i.imgur.com/S935mTb.png)  
> 可以上個寬度, 在 class 上加上 BS 的 justify content, space between   
> 記得把 container 和 row 之間多的 div 刪除!  


----

# 同學的範例  

- RWD 變版的小玩法, 例如 "更多"  
![](https://i.imgur.com/l3QRaok.png)  
> 做兩個 html, 兩個不同的區塊  
> 因為其中一個是消失的, 所以變版的時候會直接出現  
> 一次要刻兩個版就會有點小麻煩  

---

# 同學範例  

- 看展示方法再選擇要不要用 container  
> ![](https://i.imgur.com/vU8ZqN6.png)   
> 有些地方不一定要用 container  

----

# 微軟重點   

1. 在引入東西的時候檢查 BS 版本  
2. 不要的樣式可以刪除或覆蓋  
3. 覆蓋可以在 class 上面上你要的樣式  
4. 結構的部分要注意, container → row → col  
5. 盡量照 BS 的規範走  

---

# 老師示範 Nav 的 logo 和漢堡條 RWD 變版  

- 可以用 position 移到中間置中  
> ![](https://i.imgur.com/IyOgDiE.png)  
> 檢查 container 內的東西有沒有對齊
> 加個 relative  
> ![](https://i.imgur.com/CKqd6o4.png)   

- 如果變版多追加一個判定點  
> 不過 position 沒有列入變版時間點  

---

## CSS 的 position layout  
- 如果懶得打名字就直接用 BS 的屬性命名  
> ![](https://i.imgur.com/ChDR2Vb.png)   
> ![](https://i.imgur.com/IjzGdDg.png)   
> 讓他離開正常的排版狀態  
> 漢堡排選單會自動下來  
> 調整漢堡排選單位置  
> ![](https://i.imgur.com/f5SgLNQ.png)   
> 就會出現滑動效果  

---

# 怎麼固定展開漢堡排? 
> ![](https://i.imgur.com/Ns0XqTn.png)   

---

# 左右兩邊的漢堡排和 icon 互換位置  
> ![](https://i.imgur.com/Xj4Oy1X.png)   
> 大於 992px 會執行  

- 應該要反過來  
1. 多寫一個預設值蓋掉  
2. 改成 max-width  
> ![](https://i.imgur.com/4mq3Dcm.png)  

> ![](https://i.imgur.com/ACivEQR.png)   

---

# 換 icon 位置的方法   

- 盡量不要移動出來  
> 因為是 ul, li 結構  
> 還要另外給 CSS layout    

- 試著用 position 看看   
> 先找出 BS 調整的東西有哪些  
> 觀察變版的屬性變化  
> ![](https://i.imgur.com/kv1DAX1.png)   
> 他改成 flex direction row  
> 所以可以加個新屬性去覆蓋   

- 預設都是一排  
> 控制的位置都是在父層   
> ![](https://i.imgur.com/fxgRlsA.png)   
> 也是要用 position 去做控制  
> 調整後會發現 NAV 旁邊的 文字會縮起來  
> ![](https://i.imgur.com/K83y5YG.png)

- 父層被 display none 掉了  
> 所以用 position 就比較難處理  

- 可以另外寫個新的 html  
> 去做 991 的時候這塊選單 display none 掉   

> ![](https://i.imgur.com/kYXy6cb.png)  
> ![](https://i.imgur.com/j57tmEF.png)   

---

# 寫新的版面塞上選單  
> ![](https://i.imgur.com/LKqQgHu.png)   
> 給他新樣式  
> ![](https://i.imgur.com/P8i5GcV.png)   

- 記得左邊還有個放大鏡  
> ![](https://i.imgur.com/YpUe1Fs.png)   
> 把 div 跟搜尋包起來, 不過這樣會破壞 PC 版的結構  
> 或是保持搜尋的位置, 讓框框變大  
> ![](https://i.imgur.com/7lih4Jb.png)   
> ![](https://i.imgur.com/hR7KpHi.png)
> 多加個 search 板塊  
> ![](https://i.imgur.com/1ltNQrk.png)  
> ![](https://i.imgur.com/ONlYOXh.png)
> 下在 item 位置  
> ![](https://i.imgur.com/CQsI7GR.png)   

![](https://i.imgur.com/xhG5G6D.png)   

## RWD 下下策  

1. 變版的時候把它 display none 掉  
2. 在讓他有版型的時候出來
3. 缺點是會多出很多重複的區塊  
4. 效果會很難套(因為沒有效果), 只能直接出現   
```
沒法做出太流暢的效果
```
5. 好處是甚麼版都做得出來  

---

- 所以 PC 結構改動了  
> 下個 變版指令, PC 的時候不要顯示  
> ![](https://i.imgur.com/RVbDCpo.png)  
> 手機的時候再 display flex 出來  
> ![](https://i.imgur.com/0XFAeK6.png)   
> 保持框架的結構, 和能自定東西  

---

# 作業檢核  
- 天氣 API 是實際可以用的東西  
- 可以好好完成  
- 練習 fetch 會很好用, 因為前端實際工作  
- 常用到 fetch 和切版面, 從後端抓資料  

---

# New stuff - 下午切數位方塊的版型  

> [數位方塊Bootstrap作業 (dev-hub.io)](https://lesson-bootstrap.dev-hub.io/)   

> ![](https://i.imgur.com/4kHW2qu.png)   
>  首頁好像不是 BS 切出來的!?   
> 登入, 和購物車  

- 下午先從登入頁開始  
> ![](https://i.imgur.com/UdENyds.png)  

> [Document (dev-hub.io)](https://lesson-bootstrap.dev-hub.io/login.html)   

----

# 登入頁面   

- 分析頁面  
> ![](https://i.imgur.com/JCBzDRF.png)   
> 頁面分兩邊, 是從左邊 slogan 開始長出來的   
> 看起來是把左邊的頁面 display none 掉  

----

# 實作頁面  

> ![](https://i.imgur.com/1Q36PgX.png)   
> ![](https://i.imgur.com/Au5ivfy.png)   
```
父層 vh-100, w-100
```
> ![](https://i.imgur.com/lAoahCY.png)   
- 然後再上透明度  

> ![](https://i.imgur.com/XD87aWs.jpg)   

---

# 左邊的文字和底部的 logo  

- 在左邊的 login 加入文字的 div   
> 如果要 require bootstrap 的 icon 記得先找 CDN 和授權   
> ![](https://i.imgur.com/0oF9oZ3.png)   
> 也可以在 CSS 中做 import   
> ![](https://i.imgur.com/vLexR7r.png)   


- 對齊東西   
> ![](https://i.imgur.com/M1EHnEj.png)   

- 接著想辦法推 icon  
> ![](https://i.imgur.com/2jmOPK0.png)   
> ![](https://i.imgur.com/boUwFjK.png)   
> 好像不好推, 用 CSS 推   
> ![](https://i.imgur.com/4nDBekx.png)   

- 調整一下文字大小, 和 margin   
> ![](https://i.imgur.com/XACzllC.png)  
> ![](https://i.imgur.com/GxemBfi.png)   
```
↑ 文字大小 標題h1, 文章h2, 
position 定位到 left 20%  
```


---
# 右邊的輸入頁面區塊  
- 分析一下
![](https://i.imgur.com/tWkb6aM.png)   
> 有公司的 logo 和文字   
> 有 logo 提供快速登入  
> 有輸入帳號密碼的 input  
> 有 sign in 按鈕  

 --- 
 
 # 實作輸入頁面區塊  

> ![](https://i.imgur.com/AregPM6.png)   
```
action {
1. company   
2. logo  
3. name
}
```
```
Fast-login {
icon*3
}
```
```
hint 
text
password
forget
submit

```
> ![](https://i.imgur.com/obFH40G.png)   
> 結構大概是這樣   

---

# 上 BS layout  

- 置中整個表單位置  
> ![](https://i.imgur.com/96p9FW6.png)  

- 幫 Compant logo 位置上個圖片  
> 整個 SVG 包含圖片和文字  
> ![](https://i.imgur.com/RoHIgbB.png)   

- Logo 的部分  
> 在 Logo 下  m-auto  
> 沒有效的話, 因為 svg 是 inline-flex  
> ![](https://i.imgur.com/PzMiq6o.png)   
> 在 Logo 下 flex, justify content center   

- 快速登入的三個 logo  
> ![](https://i.imgur.com/wbR9HMN.png)   
> 下白色邊框, 並調整成圓形  
> ![](https://i.imgur.com/KwLUNEY.png)  
> 因為沒有高寬, logo 都擠在一起  
```
給高寬, 希望是 px 
```
>![](https://i.imgur.com/6pceCvn.png)  
> 然後給 margin left, right  
> ![](https://i.imgur.com/ud8nATc.png)   

- 最後把 logo 置中  
> ![](https://i.imgur.com/CvmB4kg.png)   

- 加上 role button  
> ![](https://i.imgur.com/J51Jx6p.png)  

----

# 調整快速登入下面的文字  

> ![](https://i.imgur.com/ZJMwzZv.png)   
> ![](https://i.imgur.com/PfjorKX.png)   

> ![](https://i.imgur.com/BplyCJz.png)   

> 調整 input ↓  
> ![](https://i.imgur.com/1Ln13JL.png)  
> ![](https://i.imgur.com/OooE8EY.png)   

- 調整輸入框內的 內距  
> ![](https://i.imgur.com/QGBOXX4.png)  
> p-3  

- 讓字體變白  
> ![](https://i.imgur.com/MXgKsjZ.png)
> 讓忘記密碼移到右邊, 同時有 margin  
> ![](https://i.imgur.com/hd5Ky5U.png)   

- 讓 submit 按鈕有彈性  
> ![](https://i.imgur.com/cpVp4bH.png)   

>  ![](https://i.imgur.com/fVhc2yy.png)   
> 讓按鈕變圓 ↑  

- Layout 調整
> ![](https://i.imgur.com/ktukJeI.png)   

- 按鈕文字換顏色   
> text-white  
> ![](https://i.imgur.com/SdteMZN.png)   

- 文字淡一點  
> ![](https://i.imgur.com/hl8wSQ6.png)   

> ![](https://i.imgur.com/eaOjKXj.png)   


- 如果是 button 又是 bg-info 他會幫你上 hover  
> ![](https://i.imgur.com/dg6HLsf.png)   

---

# RWD 變版  

- 其實 BS 都幫你 R 完了大部分  
> ![](https://i.imgur.com/ABObovm.png)   
> 縮到一定程度不會繼續縮   

- 991, 992 有斷點換版  

---

# Bootstrap 的特點  
- 其實 BS 的斷點先從小開始做比較好  
- 因為 BS 一開始是從手機的 RWD 開發作考量   
```
sm → m 
```
> 如果用 CSS 去覆蓋, 要確保權重的比較   
>   注意自己想寫的 CSS的值有沒有比 BS 的大, 才能覆蓋掉！  

---

# 左邊這塊  

- 預設值要改成 none  
> ![](https://i.imgur.com/6wQUh8C.png)   
> 991 是 lg  

- 下面這塊  
> ![](https://i.imgur.com/8w6ajHq.png)   
> ![](https://i.imgur.com/h1ryUPq.png)

- 讓他變版的方法  
> ![](https://i.imgur.com/lS0rYMw.png)  
> 讓內容的寬度去撐鄰層, slogan 是 100%, login-form也是 100%, 剛好 1:1  

> 所以不能加 flex wrap 
> ![](https://i.imgur.com/RjltDqw.png)   
> 會變形, 上下分版   


- 發現 991 無法變版  
> ![](https://i.imgur.com/6vRri5g.jpg)   
> 權力遊戲一下, 因為 BS 是 `!important`  
> ![](https://i.imgur.com/RkCalW7.png)   
> 所以 CSS 也用 ``!important`` 去蓋掉!  

---

# 發現三個社群 logo 沒有變版  

> ![](https://i.imgur.com/3wMm87g.png)   
1. 再多放一組  
> ![](https://i.imgur.com/2e8tnS8.png)   
2. 只想寫一次, 但 logo 三連星是 display none  
```
可以把它放到父層  
或是擺到未來的目的地, 變版時出現
```
- 如果選變版時移到藍色下方 ↓  
> ![](https://i.imgur.com/O2M9tCR.png)   
> 這樣可能比較好做？！  

---

# 把社群 logo 移到右邊  
> ![](https://i.imgur.com/eBrMCTL.png)   

- CSS LAYOUT 調整  
> ![](https://i.imgur.com/bvE9JHM.png)   
> 因為沒有下 relative, 所以往父層找了  
> ![](https://i.imgur.com/pBjgRQ9.jpg)   
> 這樣不是很方便的話, 換個參考點  
> ![](https://i.imgur.com/7VZWRv3.png)   
> 會一直在畫面下面  
> ![](https://i.imgur.com/pyjgT5b.png)  
> ![](https://i.imgur.com/jWdMxKz.png)   

- 還有一個比較棒的做法, 不給 position  
> ![](https://i.imgur.com/F32Zoqb.png)   
> ![](https://i.imgur.com/Ro1HxiY.png)  
> m-auto 讓他預設的時候(小版面)就能變版  
> ![](https://i.imgur.com/K1rK2kQ.png)   
> 因為有 logo 有推到父層, 所以把  margin 還回去  
> ![](https://i.imgur.com/Gu8rXqd.png)  

- 發現問題, 把 margin 每個值分開設定  
> ![](https://i.imgur.com/cQNZQ6L.png)   
> 調整一下就完成了  
> ![](https://i.imgur.com/59mBp15.jpg)  

---

# 加上  dynamic effect CSS   

- 直接覆蓋XD  
> ![](https://i.imgur.com/scU1uzX.png)   
```
transistion 可以調整到 0.3s 比較快一點
```

---

# 購物車有 1, 2, 3, 4 步驟  

- 今天晚上跟明天一整天都是這些~
- 很多重複頁面   
> ![](https://i.imgur.com/A5PFVV4.png)   
> 不用真的秀出來, 沒有在前端存資料  

----

