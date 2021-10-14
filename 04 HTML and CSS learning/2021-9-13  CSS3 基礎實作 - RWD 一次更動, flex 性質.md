# 9/13  CSS3 基礎實作 - RWD 一次更動, flex 性質   
###### tags: `CSS3 基礎實作` `2021/09/13` `進度筆記` `前端心得`  
---

# 今日講課-上午的部分  

# RWD 的一次變換所有版本動作   

跟電腦板差在 XYZ 三個寬度不一樣, 現在課程要求切四個版本的要求, 但在 RWD 的動作是一氣呵成    

## 參考資料:  

https://www.wfublog.com/2015/05/blogger-mobile-rwd-skill.html   



# 從電腦版改成小螢幕板  

- 甚麼時候要換版, 在 view point 邊界碰到 DIV 的時候   
- 觀察兩個版本的差異

![](https://i.imgur.com/plMHgrS.png)   

## 設定斷點 - 有爆板就要發生處理   

![](https://i.imgur.com/tuXP1gz.png)   

大概 1340 左右要換成下一版, 輸入 media screen   

![](https://i.imgur.com/0Wvffds.png)   

當它 max-width 變成 1340 的時候就要換版   

## 因此先改 content   

width 800px    

![](https://i.imgur.com/8E0ubOy.png)

![](https://i.imgur.com/dtaQtaV.png)   

## 接著處理 X Y Z 圖片的間距問題   

![](https://i.imgur.com/uRjPveH.png)   

## 接下來改圖片高度  

![](https://i.imgur.com/4wily3B.png)


X(img1) 50%, Y(img2) Z(img3) 對半分   

![](https://i.imgur.com/5N0Sgxa.png)   

## 調整 X 的 margin   
用X(img-1)的margin-bottom把Y(img-2),Z(img-3)往下推10px

![](https://i.imgur.com/i5xJSLh.png)   

![](https://i.imgur.com/bpzShWJ.png)   

---

# 小螢幕板完成後要讓平板 RWD 接上   

##  思考一下如何接上   

![](https://i.imgur.com/tDSwOn5.png)   

![](https://i.imgur.com/XVgFxbd.png)   

---

# 複習一下 vh & vw   

## View point vh & vw    

==目前可視範圍的百分比==   

- vw、vh→根據可視範圍的百分比設定寬高   

![](https://i.imgur.com/6oE2VXm.png)   

- height: 100vh   
- width: 100vw   

100vw 因為 ==不會去扣除橫向卷軸的 px== 所以很容易爆版   

100vh 也會受 scroll bar 影響爆版, 不過因為垂直滾動的情況比較多, 比較不會去注意到   

## 在寫 CSS 的時候

如果 div 沒有被父元素包著, 他被 body 包的時候, 你下 height 或是 width 的 %, 他會去找 body 的高度, 然而 body 的 height 為 0, 因此找不到   

---

# 想辦法讓左邊(.left)的 bar 長到頂部   

通常斷點跟稿是吻合的, 記得==如果爆版就要提前處裡==   

## 觀察換版的時機   

## 先從大的改  

![](https://i.imgur.com/jlULWMi.png)   

寬 100%, 高 100px    

![](https://i.imgur.com/FyxFeKG.png)   

## 改動 logo 的大小   

![](https://i.imgur.com/UuiBJf4.png)   

## 更動 menu, 讓他浮起來   

![](https://i.imgur.com/11ghdgv.png)   

## 對 menu>btn 字體去做對齊   

![](https://i.imgur.com/pdotOIC.png)

## 更動 logo 的間距(水平垂直置中)   

先從 margin 開始改  

![](https://i.imgur.com/vHQwJKZ.png)   

![](https://i.imgur.com/yZ8NdFq.png)   

## 更動 menu>btn 的間距   

![](https://i.imgur.com/kwqc5gl.png)

- 下 nth-child(1)  可以去選到第一個 btn   

![](https://i.imgur.com/Ta59Hsi.png)   

![](https://i.imgur.com/blzyA3c.png)   

因為 height 是 100px, 拿 ==100px - 字體大小24pt / 2== 就能用 padding 去推字體, 造成上下等距  

---

# 來複習一下選擇器   

[30個你必須記住的選擇器](https://code.tutsplus.com/zh-hant/tutorials/the-30-css-selectors-you-must-memorize--net-16048)   

## pseudo-class    

https://developer.mozilla.org/zh-TW/docs/Web/CSS/Pseudo-classes    

## :nth-child()   

() → 內容很多, 如果寫 1 他會去找第一個   

----

## 最後平板版改好上面橫 bar 後的樣子   

![](https://i.imgur.com/gQQtD2V.png)   

![](https://i.imgur.com/MYZp8VP.png)   

----

# 到平板版的時候不能寫固定的寬度   
  
## 更改 right 的寬度  

![](https://i.imgur.com/RIDCqWR.png)   

## 如何讓 content 符合版面?

- 讓 right 大版面扣掉左右間距   

扣掉左右間距後就會符合[包住三個圖片的 div]的寬度   

![](https://i.imgur.com/xCq5P1O.png)   

因為設計稿是讓左右邊間距都是 34px, 如果用固定寬度就沒有間距的效果, 所以要扣掉左右間距的總和(68px)    

![](https://i.imgur.com/qst3QJO.png)   

更改 content 的高度, 讓間距出來, 並保持水平垂直置中   

![](https://i.imgur.com/C43oOUu.png)   

# 大致修好後  

![](https://i.imgur.com/lR2Tek2.png)

## vh 會隨著 view point 改變   

![](https://i.imgur.com/tJBFRFS.png)   

因為高是 vh, 小於 800px 時就爆版了, 可以 用 min-height 解決   

![](https://i.imgur.com/r3IqReO.png)   

就不會有壓扁爆版的問題   

----

# 最後一個手機板 RWD 版型   

## 手機和網站常見的漢堡標示  

![](https://i.imgur.com/TIVRPDe.png)   

----

# 作網站的時候有常見的斷點   

![](https://i.imgur.com/wb6i4dk.png)   

![](https://i.imgur.com/NX7Q7o8.png)   


# 參考資料:  

[小事之 Media Query](https://ithelp.ithome.com.tw/articles/10196578)   

[Responsive Media Designs: Setting CSS Breakpoints](https://www.bitdegree.org/learn/responsive-media)   

---

# 設定手機版的斷點   

設定 logo 的寬高, 和

![](https://i.imgur.com/0YovRX6.png)   

![](https://i.imgur.com/xTwyIVP.png)   


# 設定手機版的按鈕   

在一開始的 HTML 做更改(不是不用更動嗎?)  
![](https://i.imgur.com/xEAtsh8.png)  

回到一開始的 CSS 樣式去把 menu 做隱藏   

![](https://i.imgur.com/339vvu2.png)   

之後去手機版下 display block 就出來了   

![](https://i.imgur.com/K9IPdb6.png)


手機版的按鈕出來了~   

![](https://i.imgur.com/AT4Malu.png)   


## 算 logo 的垂直置中高度   

(80-55/2)   

![](https://i.imgur.com/T3TZvJC.png)   



## ==記得下 float 後, margin會失效==   

- 所以把 float 下 none  

![](https://i.imgur.com/SvAMQhy.png)   

# 如果改 float 父層是 block 就一樣上不去   

![](https://i.imgur.com/ObeOqY2.png)   


# 如果在 menu-mobile-btn  下 position 記得 去 left 改 relative   

![](https://i.imgur.com/57MDbaW.png)

# 上半部完成了~   

---

# 剩下三塊圖片  

- 別把高度寫死, 可以一起處裡  
- 別設定 height = 195px, 會卡版   

![](https://i.imgur.com/txO4uZz.png)   


# 發現 content 擋住了   

- 解放他的寬高   

![](https://i.imgur.com/GSV7O66.png)   

---

# 了解一下草稿的圖片怎麼擺   

# 先了解整塊的版面高度   

![](https://i.imgur.com/oNlnFeH.png)   

因此 下面的大版面(.right)的高要做 100vh-80px

![](https://i.imgur.com/8HB3xdF.png)

# 因此 我們要調整最小高度    

==要記得在最外層下 min height==, 讓圖片的最小高度被 min height 限制住  

![](https://i.imgur.com/ZNc5B0K.png)   

# 限制高度的情況  

也可以用calc  ( ( 100vh - 80px ) / 3 ), 不過記得要把 min height 拔掉   

==但裝置如果太小會扁調== 因為沒有 min height  

# 調整手機版 RWD 圖片   

可以用 % 數 處理   

![](https://i.imgur.com/ir5O8PW.png)   

並消除 img-1 的空隙, 把 margin 設 0   

![](https://i.imgur.com/brnEZIB.png)   


# 課堂練習-組版完成後, 稍微美化一下 RWD  

- 可以連結   
- 有圖片之類的   

---

# 課堂新進度 display-flex 屬性   

# 參考資料:   

[MDN-CSS彈性盒子用法](https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)   

[CSS | 所以我說那個版能不能好切一點？ - Flex 基本用法](https://medium.com/enjoy-life-enjoy-coding/css-%E6%89%80%E4%BB%A5%E6%88%91%E8%AA%AA%E9%82%A3%E5%80%8B%E7%89%88%E8%83%BD%E4%B8%8D%E8%83%BD%E5%A5%BD%E5%88%87%E4%B8%80%E9%BB%9E-flex-%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-e68cc2906995)   

[深入解析 CSS Flexbox](https://www.oxxostudio.tw/articles/201501/css-flexbox.html)   

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox  

----

# 講解 display flex   

![](https://i.imgur.com/Bv7BIBv.png)   

==藍色的線==: 主軸線   

==橘色的線==: 交錯軸, 相交於主軸線  

# 課堂範例-flex  

![](https://i.imgur.com/PJAfnXX.png)   

把每個 box 下顏色   

![](https://i.imgur.com/eWBNE38.png)   

# 接著把 display 改成 flex   

flex 下在父層後, 子層受到影響  

![](https://i.imgur.com/oOAIyOE.png)   

![](https://i.imgur.com/ZzGf6FC.png)   

# 到底發生甚麼事情????

# 參考資料:   

[MDN CSS Flexibile Box](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout)

# 原本子層 box 是直的   

![](https://i.imgur.com/2mZ949V.png)   

啟用 flex 後他會幫你把 box 排好, 然後全部塞進大 box 內, 就像是俄羅斯娃娃   

![](https://i.imgur.com/2M5ruyB.png)   

## 講古  

以前叫做 display: flexbox, 現在很簡短剩下 flex  

## 參考資料:   

[Flexbox 基本認識](https://ithelp.ithome.com.tw/articles/10238486)   

# flex 的重點   

不管你下多少盒子(假設偶數可以整除的情況), 他都會幫你塞到父層內的大盒子, 而且永遠都是均分(大概) , 會改變 div 佔滿整行的狀況(div 預設是 display block), 然後一直排排下去   

![](https://i.imgur.com/DAYQax3.png)   

==<用這個可以解決 float 讓父層高度塌陷的問題>==  

# 看一下 flex 屬性   

記得主軸線的方向   

- 這些 box 屬性跟主軸線有關, 主軸線去影響排列   
- 記得先啟用 display flex   

![](https://i.imgur.com/mchtY2c.png)   

- flex-direction 預設是橫的 row (主軸線的方向)   

- flex wrap reverse 會讓主軸線反向跑   

- flex-direction: column   主軸線和交錯軸換位置, 由上到下

![](https://i.imgur.com/URUkAm7.png)

# 參考資料:   

https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex-direction   

# 那交錯軸在做甚麼??  

flex-wrap: wrap 換行啟用後(預設是不換行), 他會幫你把 box 換行   

![](https://i.imgur.com/nUbfsNB.png)

==wrap 是根據交錯軸的方向換行的==  

==如果子層的 box width 寬加起來 > 橫的 主軸線, 就會換行==   

## flex 可以跟 wrap 同時使用   

## 同理 wrap-reverse 後, wrap 就換了方向(反向)   

## 參考資料:  

https://ithelp.ithome.com.tw/articles/10239122  

----

# 又一個新東西 justify-content  - 主軸線對齊方向  

- 記得先啟用 display flex   

![](https://i.imgur.com/VRSqY7p.png)   

- justify flex start 是預設主軸線開始跑的位置  

![](https://i.imgur.com/x8eXCz9.png)   

![](https://i.imgur.com/XsUMhU9.png)   

# 參考資料:  

https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content   

---

- justtify-content flex end, 讓方塊跑到主軸線最末端的位置   

- justtify-content flex center, 讓東西在主軸線水平置中對齊(好用, 推薦五顆星)   

![](https://i.imgur.com/xyZZWZw.png)   

- justtify-content space between 左右對齊還幫你均分   
![](https://i.imgur.com/K9i4XBr.png)   

- justtify-content space around 均分剩餘的空白區塊, 而且每個方塊周圍的空間都被均勻分配(一樣大小)    

- justify-content space evently   會把剩下的空間平均分配, 例如有 5 個盒子(元素), 這樣就有6個相同寬度的間隔空間, 間隔空間的數量, 基本等於元素的數量加一   
![](https://i.imgur.com/Hqui4DL.png)   

----

# align-items 交錯軸對齊方向   

- 可以單獨使用, 但一樣要啟用 display flex   

align-items  flex end 會根據交錯軸的 結束方向 跑到最下面  

![](https://i.imgur.com/krony1H.png)   

==align-items: center + - justtify-content  center 可以造就水平垂直置中==   

![](https://i.imgur.com/hzapMrR.png)   


# align-items 換行的問題   

![](https://i.imgur.com/933PyuZ.png)   

# align counter 跟 align items 差別?  

- align counter    
都是交錯軸的對齊方向, 但 counter 會將所有 flex-item 群組化, 然後把這些東西集體對齊, 一起移動, 因為是個群體   
- align items   
會將 align items 個別對齊,每個東西都視為一排的對齊方式, 這一排個別移動  

==沒有 justify items== QQ   

----

# Flex 內元件屬性  

平常很少用, 甚麼時候使用到這些東西???   

- flex basis  會把 width 蓋掉, 不是寬高, 是主軸線方向的長度(可以在子層下 order:1), 當你需要去計算長寬時會用到, 但只能給整數, 不能給小數點   


↓ 假設你有六個 boxes  
![](https://i.imgur.com/MZ4nXQ3.png)  

↓ 你在 box-1 身上下 order 1   

![](https://i.imgur.com/910r1kf.png)   

↓ 會改變 box 的順序(如果其他 box 都沒下 order, 預設為0), box-1下了 1 後會使其數值最大, 移到最後位   

![](https://i.imgur.com/uTEEAqv.png)   

所以移動到 box-6 後面了, 如果是 負值 則往左移動   

![](https://i.imgur.com/dk2HRnj.png)


- flex grow(預習)  
- flex shrink(預習)  

# 參考資料:    

https://wcc723.github.io/css/2017/07/21/css-flex/   

# align self 

寫在自己身上, 對交錯軸對期, 但沒有 justify self    


----

# 課後任務 - 玩 flexbox froggy  

共 24 關, 回家玩這個 - 請你玩到全破!   
[https://flexboxfroggy.com/#zh-tw](https://flexboxfroggy.com/#zh-tw)   by david   

- 大概七顆星難度的上位任務(抖   

這個東西不會檢討, 網路上有教學解釋, 所以 BJ4  

~~盡量別看教學通關~~ 看教學通關大概懂 flex 七八成   

通關教學    
[阿莫斯の網頁料理室 : 用遊戲學 Flex 之 FLEXBOX FROGGY 解關技巧 | 網頁教學 | CSS教學 - YouTube](https://www.youtube.com/watch?v=aAa5EDRjMbE&ab_channel=CSScoke)

![](https://i.imgur.com/r248EYB.png)   

# 參考資料:  

https://yakimhsu.com/project/project_w6_CSS_flex.html  

----