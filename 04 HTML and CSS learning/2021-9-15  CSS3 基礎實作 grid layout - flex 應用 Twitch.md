# 9/15  CSS3 基礎實作 grid layout - flex 應用 Twitch   
###### tags: `CSS3 基礎實作` `2021/09/15` `進度筆記` `前端心得`  
---

# 今日講課-上午的部分  

## 預告  

- Twitch 作業, 中秋作業   

- 黃老師會帶切版到 9/30, 之後是 JS, 之後會有大型仿切微軟官方頁面    

# 排版系統演進   

1. float 使用情況會越來越少   
2. position  div 要排在特別的地方時, 會用到, 可能會超出 div 的框時也會用到   
3. display  
4. flex  
5. grid 沒有教, CSS 5 可以自己來學一下   

![](https://i.imgur.com/tJ7HFZX.png)   

- 一樣是透過父層(元件)來控制子層   
-  不過對瀏覽度的支援度不高  

# 工程師使命-向下兼容   

現在還在世代交替, IE 被放棄中, 還有大量的網頁用 CSS4 寫, 三個月內會更新一次技術資訊, 現在學到的 4 代排版系同夠應付 7-8 成, 剩下的要自己努力解決問題(善用搜尋)   

https://caniuse.com/   

![](https://i.imgur.com/5W99dMN.png)   

---

# 看 Twitch 的大版面組合   

知道 Twitch 的版面, 因為 Twitch 一直在改版, 跟現在的仿切可能不太一樣, 找一下版面切法   
![](https://i.imgur.com/u0RihVt.png)   

> 上方 bar  分三塊   
> 左邊一排的圈圈   
> 右邊中間的 卡片式切版   

## 卡片式切版(Website card design)   

- 因為很好處理 RWD   
- 資訊分成一塊塊   
- 可以讓你的視野專注在不同區塊  
- 可以增加使用者體驗   

![](https://i.imgur.com/W9DKOql.png)   

# 語意化標籤   

變成有意義的命名, 記得 div 是沒甚麼意義的   

> 善用語意化標籤可以增進 SEO  

![](https://i.imgur.com/d18jzzi.png)

![](https://i.imgur.com/jOQgrXo.png)

> 區塊頁首 - Header 
- Header 包著導覽按鈕 nav   
- nav 包著無序清單 ul li  
- 頁首這塊 bar 的特性, 切換到哪一頁面幾乎都不改變   

![](https://i.imgur.com/xR3PYIW.png)   

> main 主要大區塊   
> article 主題、文章  
> section 區塊   
> aside 側邊欄位, side bar 通常跟頁首 header 綁在一起  
> footer 頁尾, 放標語的地方   
> address 可能放資訊, 聯絡方式, 地址的位置   


參考資料:   

[快速了解HTML語意化標籤 | by Kira Yang | Medium](https://medium.com/@changru.studio/%E5%BF%AB%E9%80%9F%E4%BA%86%E8%A7%A3html%E8%AA%9E%E6%84%8F%E5%8C%96%E6%A8%99%E7%B1%A4-33dd8247d779)   

----

# 進入 Twitch 仿切   

- 可以參考 Twitch 版面, 瀏覽, 電競也放進來   

![](https://i.imgur.com/GGBQdE3.png)  


## 搜尋 bar    

![](https://i.imgur.com/EgAhh1S.png)   

- 有 hover 效果, 能加最好~   

## 登入註冊區塊   

![](https://i.imgur.com/tZQZYbG.png)   

## aside   

美化, 盡量做好作品~ 求職比較有幫助  



---

# 下午的部分 -上方導覽列和側方導覽列的 CSS    

記得先把排版區別開來   

![](https://i.imgur.com/7wmJs7x.png)

通常頁面只有一個 header,  給他點顏色~   

![](https://i.imgur.com/pizGJV9.png)   

## 給 Logo 顏色   


![](https://i.imgur.com/y11nZbl.png)   

## 對 menu 下 flex    

![](https://i.imgur.com/AwUnUNs.png)   


## 幫 header 下 flex   

![](https://i.imgur.com/1Vmvbfm.png)   

## 幫 member 下 flex   

![](https://i.imgur.com/ueWxeAD.png)   

# 登入註冊   

display 改成 flex   

如果有下 ul 記得 把 margin 和 padding 拿掉(設定0)   


# 下搜尋的按鈕  

搜尋列記得下 flex   

![](https://i.imgur.com/HzKsobk.png)   


# LOGO 通常不會放在導覽列內   

把 LOGO 脫離導覽列, 離開排版系統, 父元件要記得下 relative, 再把 LOGO 下 absolute   

# 把間距做出來   

對 logo 下 margin  

margin-left 70px 去推 logo  

# 給 aside 寬度和調整高度  

100vh-50px

![](https://i.imgur.com/nCZhyEO.png   

----

# 中間的區塊 hmtl 架構作法   

先用個容器包起來   main   

![](https://i.imgur.com/d5idhTA.png)   
  
## 注意爆版  

![](https://i.imgur.com/aWinYtC.png)   

main 貼在左上角的情況, 希望他能從左方欄位出來

下 margin 0 padding0    

![](https://i.imgur.com/93oPqky.png)   

---

## 處理大區塊的分類   

需要容器包起來, 希望排滿的時候做出來像是這樣   

![](https://i.imgur.com/TGAYQ6K.png)   

 
# 先處裡大區塊    

![](https://i.imgur.com/zlrASaR.png)   

col 是指一個一個欄位, 每個欄位裝有想要得一個東西, 

# game card html 結構   

![](https://i.imgur.com/nqGDL3Z.png)

左右貼齊, justify content space between 
把 game card 換行  wrap 

如果用 space between 有 div 掉下來,   

下多一點的空 col 他會把剩餘的空間補滿   

![](https://i.imgur.com/9e4ex2P.png)   

- 像 twitch 有多塞幾個空白的 div  
- 然後這幾個空白的 div 補一個最小的寬度, 然後沒有高度, 他會幫你乖乖橋位置  

之後複製貼上 10 個左右, 就可以拉到 10 個箱子   

![](https://i.imgur.com/ICHm00p.png)   



# CSS row 的 display 記得改 flex   

# 接著把間距做出   
用左右 padding 單位是 em   
 
 # 單位介紹  
 
 ==文字單位 px % em, rem==   
 
##  px 是所謂的絕對單位  
 
 ## em rem 是"相對"單位   
 
 > em 以父層元素為主, 適合用在限制區塊的內容   
 
 ![](https://i.imgur.com/Z9021El.png)   

- 父層 如果是 20px, 子層也會是 20px 

> rem 是相對 root 層級(例如去抓最根源的位置 html)的文字大小, 因為 html 這個文字標籤的 px 就是 16, 跟 em 不太一樣, 會 base html 去做調整(因為都被 html 包著)   

## 做 RWD 時, 每個字體級距都應該會隨著縮放   

如果用 rem 就比較會根據換算, 例如放在 padding 用 rem   

 參考資料:   
 
 [認識網頁文字單位－px、%、em、rem (webdesigns.com.tw)](https://www.webdesigns.com.tw/css-emrem.asp)   
 
 ---
 
# 基本上不會去改 row, 會去改 game card, rol    
 
 ![](https://i.imgur.com/pSUpJv5.png)   
 
## 改表格內的 123, 而不會改動表格大小   
 
 ![](https://i.imgur.com/NlhGB2e.png)   
 
## 有一點 padding   

![](https://i.imgur.com/aSPWs0V.png)   

## 調整 game card 的內容   

![](https://i.imgur.com/ELkhO2e.png)   

# 給右邊區塊一個固定寬度   

![](https://i.imgur.com/IQsCnM4.png)   

# 這會縮起來的效果是用 JS去做的  　
![](https://i.imgur.com/IgEkAGb.png)　　  　

- 先不橋   

---

# main 剩下的區塊部分   

左右兩區塊   

![](https://i.imgur.com/ruo37ml.png)   
