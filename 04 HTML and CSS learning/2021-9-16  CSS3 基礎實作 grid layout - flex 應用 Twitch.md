# 9/16  CSS3 基礎實作 grid layout - flex 應用 Twitch   
###### tags: `CSS3 基礎實作` `2021/09/16` `進度筆記` `前端心得`  
---

# 今日講課-上午的部分  

# 老師示範-雕完 Twitch 上半部   

----

# game card 外觀有圓角   
加上 border radius 5px   

![](https://i.imgur.com/dKqhB5T.png)   

# 處理 game info - 調整字體位置   

![](https://i.imgur.com/OsgVwTn.png)   

![](https://i.imgur.com/KOKtgtO.png)   


# 處理 live 外觀   

LIVE 變大寫, 字體撐大, 左右跟上下間距有差  

![](https://i.imgur.com/aRGI1IF.png)   

找 font-size 62.5% (16pt 的 62.5%)  

- Twitch 所有能做 rem 的都用 rem 去寫   
- 做 RWD  時比較方便  

字體改成微軟正黑體   

![](https://i.imgur.com/HETq1qO.png)   


![](https://i.imgur.com/YmPDG1R.png)   

![](https://i.imgur.com/BJqQyX4.png)   

# 用 position 調整 live 的位置   

![](https://i.imgur.com/oNXlAtb.png)   

記得父層調整 relative   

# game-info 字體調小   

![](https://i.imgur.com/YgMmC8x.png)   


# 看一下圖片, game-card 在一開始是分成三等份的   

![](https://i.imgur.com/dWhUT4P.png)

## 修改一下 html 結構   

用 Ctr+d 選所有的 live, alt 調整 live-block 的位置   

![](https://i.imgur.com/BHL2E4K.png)   

# 回頭調整 live 的寬度和位置   

![](https://i.imgur.com/3n7ywh0.png)   

![](https://i.imgur.com/2M4H1cL.png)

# live block 調整高度   

![](https://i.imgur.com/z6LpsJB.png)   

# 跑版的情況   
## 開著 dev tool 去微調會比較好調整   

調整 game info  

![](https://i.imgur.com/X66LNim.png)   

間距也有點問題   

把 gap 改小試試看   

![](https://i.imgur.com/UazgLA3.png)   

---

# 調整標題和描述字體的大小   

![](https://i.imgur.com/u0EUATw.png)   

對著 Twitch 調整標題和描述字體的間距   

![](https://i.imgur.com/jpJFptf.png)   

用 dev tool 去對著調整   

你做的作品跟 Twitch 越像越好, 對求職比較好   

----

# 下半部的區塊, 切版時分成左右兩塊  

如果切手機版, 左邊的會有縮放   


# 其實電腦版還有最下面的頁面, 如果有空可以切切看   
![](https://i.imgur.com/h5Jq5IB.jpg)   

# 下午的部分 - 實況中的對戰仿切   

![](https://i.imgur.com/W09PL0c.png)   

![](https://i.imgur.com/DU3eQBt.png)   

![](https://i.imgur.com/ttwuRpz.png)   


## 觀察對戰的版面構造  

分成左右兩塊, 兩塊並不會影響  

![](https://i.imgur.com/2F47IPA.png)   

![](https://i.imgur.com/AYwhV1L.png)   

這兩邊結構類似, 可以把這些區塊的 CSS 重複利用   

# 把版面劃分   

![](https://i.imgur.com/XxLn3n8.png)   

# 把 live 的 CSS 樣式重複套上   

![](https://i.imgur.com/WUa9TDr.png)   

![](https://i.imgur.com/dysAh4e.png)   

# 套上實況主名稱,標題資訊, 實況的遊戲, 語言   

![](https://i.imgur.com/lV8U1RM.png)   

![](https://i.imgur.com/ywrapqC.png)   


# 如果畫面命名很多地方, 調整一下選擇器的選擇方式, 或是 class 的命名  
![](https://i.imgur.com/wHQ36aP.png)   

![](https://i.imgur.com/Cq0R7hN.png)   

# 讓版面的區塊, 讓他跟 Twtich 一樣會縮放   

給他比例去算或是 max-width   

> 右邊版面的區塊大小   

![](https://i.imgur.com/fDZDDTe.png)

1220/4 是每塊的固定寬度, 但如果寫 25% 間距就不見了, 每個的寬度是 25px-20(padding)  

這邊採用寬度 %, 可以有 RWD 效果   

100% 分成四等分, 25%-20px

![](https://i.imgur.com/jqvYdpW.png)

因為加了第五個 row 所以第五個區塊有點掉下來   

![](https://i.imgur.com/NfKQA7y.png)   

加上 padding 去推, 讓他有拉開, 縮小的時候不會改變每格的寬度   

![](https://i.imgur.com/aIJ5T4K.png)   

---

# 如果讓他有斷點(平板版)   

![](https://i.imgur.com/gXEpYeA.png)  

![](https://i.imgur.com/aR6MRLH.png)  

先算好再用 @miedia queries 就很快  

----

# 原子習慣   

![](https://i.imgur.com/Fq8jFPr.png)  

----

# 實況中的對戰 - 套上 CSS   

![](https://i.imgur.com/DnwwheQ.png)   

左邊區塊需要比較大一點  

![](https://i.imgur.com/8vshYqE.png)   

> 左邊可以用不同的 class 包起來   

![](https://i.imgur.com/1luworr.png)   

因為不是在第一子層, 可以用後裔選擇器   

![](https://i.imgur.com/sMXMOG0.png)   

---

# 遇到不是固定寬度的狀況   

![](https://i.imgur.com/Tedpulx.png)  

不太好解決的情況可以用 position   

![](https://i.imgur.com/81BIcyX.png)   


# 把影片的位置定位和用 padding 去拉   

![](https://i.imgur.com/LjUu3R1.png)   

記得子元件 position 父元件用 relative   

# 給一點透明度, 和圓角  

![](https://i.imgur.com/KAc1s0m.png)   

# 還需要一點間距   

![](https://i.imgur.com/BJLjd6Z.png)   

# 參考 Twitch 影片寬高  

給仿製的影片上寬高   

![](https://i.imgur.com/H9A9DTH.jpg)   

# 大頭貼上顏色   

![](https://i.imgur.com/jRb7g1B.png)   

![](https://i.imgur.com/OBJMXDm.png)   

Streamer 上 flex 就會排在一起   

# 大頭貼跟實況主要有點間格   

padding 5px 左右   

![](https://i.imgur.com/0ZWQXfE.png)   

然後垂直置中   

![](https://i.imgur.com/0vT4aw1.png)   

# 更改其他影片的影片名稱大小和間距   

![](https://i.imgur.com/x7nQc71.png)   


# 怎麼讓過多的文字省略(變成 "...")   

CSS 設置文字只顯示一行, 超過的部分顯示省略符號   

![](https://i.imgur.com/xjzhIkt.png)   

#  參考資料:   

[\[CSS\]文字單行/多行的省略 – 工程師的筆記圖書館 (wordpress.com)](https://tynadesigner.wordpress.com/2021/02/02/css%e6%96%87%e5%ad%97%e7%9a%84%e7%9c%81%e7%95%a5/)   


# 之後學預處理器   

- webkit 前綴   

加前綴會用一些 CSS 無法使用的功能去支援一些版本比較舊或是跨版本的瀏覽器   

# 把 highlight 加上 padding 

發現無法對齊, 子元素 用 padding 0 10px 如果發現有空白, 可以去父層A用 margin 下 左右 -10px 把子元素推回去   

![](https://i.imgur.com/xaGluod.png)  

# 繼續處理 other 小區塊左右對齊   

![](https://i.imgur.com/HUaqczh.png)   

用 padding 去減過後, 就不用再去減 padding 了   

![](https://i.imgur.com/WRpHPSv.png)   

![](https://i.imgur.com/8u3hnxC.png)   

# 調整小區塊   

用 row gap 去推開, 才不會有 padding 留白的 副作用   

![](https://i.imgur.com/UDGGBUh.png)   

---

# 如果用 margin 去推 寬度還要再回扣 margin   

而 gap 只作用在 flex, 有瀏覽器版本支援的問題, 如果 用padding (自己撐開內間距)就比較沒這個問題; 而用 margin 會讓 div 變大(因為是外間距)   

# grid system - grid layout    

格線排版系統, 中間有間距, 這些間距常會用 padding 去推  

> 記得用 內層子元素 padding 去推的時候, 要去父層用 margin 去推   

----

# Twitch 切好後   

- 設法讓版面對上 Twitch 的版面   
> 切法, 圖片, 字體大小, 顏色, hover 效果之類的   

試著讓這些對齊看看   
