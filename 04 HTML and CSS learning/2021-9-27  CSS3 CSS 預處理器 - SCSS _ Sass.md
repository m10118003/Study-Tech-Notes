# 9/27  CSS3 CSS 預處理器 - SCSS / Sass    
###### tags: `CSS3 基礎實作` `2021/09/27` `進度筆記` `前端心得`  
---

# 今日講課-上午的部分  

# CSS 預處理器   

> CSS 必須先有名稱, 不能用嵌套式, 像這樣:  

![](https://i.imgur.com/Gk2thn3.png)   

# 主流的預處理器  

- Sass  - 用 Ruby 寫的動態語法 (台灣常見)   

SASS 可以當作 SCSS 的其中一種寫法，SCSS下可以寫下兼容 CSS 以及不兼容的兩種做法     
> 常見的幾個 CSS 預處理器    
```
- Sass/ScSS  
- LESS  
- Stylus  
```
- 變數:    
![](https://i.imgur.com/MSQkUUg.png)   

- Nesting:    

![](https://i.imgur.com/huAcRc5.png)   


# ==參考資料:==   

[Sass: Syntactically Awesome Style Sheets (sass-lang.com)](https://sass-lang.com/)   

[Sass/SCSS 基本語法介紹，搞懂CSS 預處理器｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/css-preprocessor-sass-scss)  

[Sass - 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/zh-tw/Sass)   

[使用VSCode外掛自動編譯SASS/SCSS. 相信有使用Sass或Scss寫網頁樣式的人都已經習慣使用相關的指令編譯。但對初次… | by An Sheng Huang | Medium](https://medium.com/@enshenghuang/%E4%BD%BF%E7%94%A8vscode%E5%A4%96%E6%8E%9B%E8%87%AA%E5%8B%95%E7%B7%A8%E8%AD%AFsass-scss-9ff768d23b48)   
  
  [DAY 03 SCSS ? SASS ? - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10266576?sc=iThelpR)   
  
  [SASS教學 ＋SCSS：CSS 再進化，掌握語法攻略！ - 犬哥網站 (frankknow.com)](https://frankknow.com/sass-tutorial/)   
  
  [Sass/SCSS 基本語法介紹，搞懂CSS 預處理器｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/css-preprocessor-sass-scss)  


  
  ----

# Live Sass Compiler - 裝 extension 來用   

![](https://i.imgur.com/I53I2HR.png)   

- 這可以幫助把 Sass 編譯成可以使用的  

## 資料夾有漂亮的圖案   

![](https://i.imgur.com/4HtoKYw.png)   


---

# Sass / SCSS 差別   

都是 Sass  

> ==Sass 沒有括號分號(被省略)==  

> ==SCSS 有括號分號==   

![](https://i.imgur.com/STNpcXg.png)   

---

# 為什麼要這個 ?  

以前端設計師為例  

![](https://i.imgur.com/8Sjk4ie.png)  

Sass 幾乎是基礎   

---

# Vscode 使用方式   

創造 scss 資料夾 > 會有個 sass 檔案格式   

![](https://i.imgur.com/tB4hu18.png)   

- 這按鈕  

![](https://i.imgur.com/6qoxKjL.png)   

==這按鈕會幫你把 CSS 編譯成 Sass/ ScSS==  

---

![](https://i.imgur.com/zsAkH2V.png)   

# 做出一個 四欄位排版     

![](https://i.imgur.com/C0GE5h7.png)  

# 引入 Scss 檔案   

![](https://i.imgur.com/hd79CjT.png)   

- 可以發現沒吃到 CSS 檔   

- html 文件看不懂 scss 檔案, 因此要把 Scss 轉成 CSS  

可以讓  html 看得懂非本身設定可以去讀的檔案, 像是 Scss   

link 那邊可以直接更改, 讓 html 直接讀 經過  LIVE SASS compiler後的 CSS   
```
link rel="stylsheet" href="../css/style.css"

指向 css 這個資料夾下的 style.css 檔案  
```

---

# Sass Vscode setting  

- 要不要加上前綴  

![](https://i.imgur.com/T0BD4ig.png)   

# ==參考資料:==    

[SASS : VSCode 套件安裝 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10203396)   

---

# 以 JSOM 的方式來修改   

![](https://i.imgur.com/IaE4Hw0.png)   

希望他編譯好後幫你丟到 css 資料夾內   

- 大概是這樣設定   
![](https://i.imgur.com/dkSvfZs.png)  

`savePath`   ==↑ 改儲存路徑的位置==   

---

# savePath - 更改儲存路徑的位置

- style.scss 編輯好後記得按一下存檔(有時候安裝完, auto save 不會自動開啟)   

![](https://i.imgur.com/ufg7Sr3.png)   

如果希望 Scss 編譯產生 css 時不要丟在 根目錄底 ↓    

![](https://i.imgur.com/j37fW5Z.png)  


> 但要注意, 這樣是說在 css 資料夾下!  

![](https://i.imgur.com/StNBOiG.png)   

- 參考老師講解後, 開 format json 格式   

![](https://i.imgur.com/jzolM5b.png)   

點進去更改 `.settings.formats`  ↓   

![](https://i.imgur.com/KfaSyYC.png)   



```
\],

 "liveSassCompile.settings.formats": \[
        {

 "format": "expanded",
                             expanded 可以直接展開 CSS檔案的格式, 比較好讀 CSS 樣式
                             compressed 則是會壓縮 CSS 格式, 上線的正式版本常用
 "extensionName": ".css",
                             展開 .css 檔案

 "savePath": "~/../css"
                                儲存路徑, 儲存在相對於每個 sass 的相對位置, 這邊的意思是 此目錄本身(~/), 的上一層中(../), 的相對位置是 css 資料夾
        }

```

---


# 正式版上線常常會壓縮 scss    

- compressed  

![](https://i.imgur.com/dVxYmzl.png)   

![](https://i.imgur.com/jX9UEYs.png)  

![](https://i.imgur.com/Nhz9cws.png)   


# style.css.map 是描述檔   

![](https://i.imgur.com/xLwNXiJ.png)   

也可以不把它弄出來(不特別造出 map 檔案)   

----

# 最後記得把 html 引入 CSS

- 不是引入 SCSS, html 真的看不懂XD  

![](https://i.imgur.com/quxFPQf.png)   

---

# CSS 基礎動畫   

![](https://i.imgur.com/cmBsj06.png)   

![](https://i.imgur.com/GRoHsEX.png)   


> 希望滑鼠移動進去, 然後 h1 先跑出來, 再來是 p 跑出來   

![](https://i.imgur.com/VCfsIxR.png)   

![](https://i.imgur.com/C6X24cs.png)  

![](https://i.imgur.com/foYkkno.png)   

![](https://i.imgur.com/YBoOuHg.png)   

![](https://i.imgur.com/CvgCh4N.png)   

---

# 做出時間差   
![](https://i.imgur.com/jSV4zzg.png)   

p 延遲 0.5 秒出現   

![](https://i.imgur.com/beEts5Y.png)   

---

# hover 的時候 before 才長出來   

![](https://i.imgur.com/BIGGErh.png)   

- 如果加上 transition 卻發現沒有效, 因為要有 hover 的時候才有 before   

![](https://i.imgur.com/quvEv5o.png)   

開 dev tool 看一下   

![](https://i.imgur.com/GGzRWyM.png)   

沒有 hover 的時候就沒有 before, before 一開始就沒有任何屬性, 要讓 before 一開始就存在   

# 先讓 before 存在   

![](https://i.imgur.com/Pab9jh1.png)   

# 然後讓他 hover 時才有 opacity  

![](https://i.imgur.com/ypEfTXM.png)   

![](https://i.imgur.com/wlZgRpH.png)   

## html 結構   

![](https://i.imgur.com/J1qDwfA.png)   

##  scss 結構   

![](https://i.imgur.com/SKmyXdp.png)   

---

# 下午的部分 - 特殊動畫~  

![](https://i.imgur.com/RUuDIDE.png)   

- 有彈跳的球, 一 變成 X X,  來做做看 X X 的效果   

---

# 拆解 X X  

> 當你 hover 的時候, 造成圖案旋轉, 看起來有三個 div   
   
![](https://i.imgur.com/xFIvmoQ.png)  
  
  
  - 推開下面方塊  

寫 XX (cross) 的時候, 把線畫出來   
![](https://i.imgur.com/NMBFGoe.png)  


劃出兩條線↓  
![](https://i.imgur.com/ij9Xdy9.png)   

然後定位 ↓   
![](https://i.imgur.com/UPSxp81.png)   

這樣就脫離排版效果, 線也重疊   

# 做出 hover 效果   


看起來要用 transform rotate  
![](https://i.imgur.com/cBOSBz6.png)   


幫他喬 45 度角   (deg)   
![](https://i.imgur.com/Z2utuDO.png)   

![](https://i.imgur.com/KWjvGw3.png)   

發現 ROTATE 被取代掉   
![](https://i.imgur.com/pHNBWSD.png)   

↓ 於是讓 transform 有多個屬性, 同時又位移又會旋轉  
![](https://i.imgur.com/NKnP2jX.png)   

↓ 順序有點影響, 會影響先位移再旋轉,   
![](https://i.imgur.com/vWWyIcD.png)  

![](https://i.imgur.com/FZxP0Km.png)   

↓ 所以讓他先選轉再位移   

![](https://i.imgur.com/UNTaSFU.png)   

----

# 老師的 codepan:  
https://codepen.io/testBP/full/LLGyZm  

---

# 課堂練習 - 實用的漢堡選單變成 X X 動畫   

CSS 動畫吃得效能超低, 可以減少資源使用量   

按下去後(做 hover 就好), 看起來有四個 div, 最上面和最下面的 bar 會旋轉, 中間的會消失   

![](https://i.imgur.com/fzpXj6u.png)   

![](https://i.imgur.com/ruGd09p.png)   

----

# 課堂練習檢討   

# 大致刻出 hmtl 結構, container & 三條線   

![](https://i.imgur.com/flwxa2q.png)   

# 做出漢堡框   

![](https://i.imgur.com/S7FNwZ3.png)   

# 給個漢堡線   

![](https://i.imgur.com/b45LGvv.png)  

![](https://i.imgur.com/9ymJ9CS.png)   
![](https://i.imgur.com/wC0eqk0.png)   

# 調整漢堡三層線位置  
 
![](https://i.imgur.com/fylpgox.png)   

> 老師的範例是用點擊的時候讓線條移動  

---

# focus 點住時改變顏色   

- 選到他的時候的狀態, 用 tab 去選的時候會有反應  

![](https://i.imgur.com/gWXkde9.png)   

# tabindex 1 2 3 4....
> 可以照順序選下去, 可以被 tab 選到     

![](https://i.imgur.com/PFqVfHt.png)   

---

因此讓   

![](https://i.imgur.com/ZJQtepH.png)   

![](https://i.imgur.com/XR4KmAe.png)   

![](https://i.imgur.com/fBwrCNQ.png)   

# transition 進階屬性   

而如果要讓漢堡上下層回到中間位置再轉   

- transition-property   

> 裡面可以寫任何 CSS 屬性, 要用逗號分隔   ![](https://i.imgur.com/PUHtJL0.png)   

↑ top 吃到 0.1s (比較快) ; transform 吃到 1s (比較慢)   
   
![](https://i.imgur.com/Hjsuszx.png)   
   
==其實 transition-property  預設是 all==   
- 所有人都能吃到, 所以可以指定一下  

![](https://i.imgur.com/u5JKwBV.png)   


# ==參考資料:==   
[CSS 轉場 - CSS | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)  

[CSS transition-property 属性 (w3school.com.cn)](https://www.w3school.com.cn/cssref/pr_transition-property.asp)   

# 調整漢堡回到中間位置, 再轉場   

給 line 顏色  

![](https://i.imgur.com/qLTbTMu.png)   


![](https://i.imgur.com/HxuOR2P.png)   

當 focus 點選的時候, 希望 top 可以快速到中間, 然後才慢慢旋轉   

![](https://i.imgur.com/QryHnrx.png)   


![](https://i.imgur.com/FrMIohr.png)   

↓ 所以這效果寫在 foceus 上　　　

而當他離開 focus, top 很慢的移動上去,  很快地變形~~~~   

---

# CSS - 進階動畫  !?   

# 做動畫的時候, 先把靜態的畫面做出來   
- 然後再去做動態的     
- 這個框放四個方塊   

![](https://i.imgur.com/l01qYK1.png)   

block 內有 四個 box   

![](https://i.imgur.com/5kuDSnN.png)   

把 block 給畫出來   
![](https://i.imgur.com/dd9dpQ7.png)   


引入 CSS   
![](https://i.imgur.com/amof4kI.png)   

把盒子弄顏色大小出來   
![](https://i.imgur.com/fcz6she.png)   

把盒子定位   
![](https://i.imgur.com/JLzPcwF.png)  

box-1 ~ 4 有間隔   350, 650, 950 之類的   


---

# @keyframes - 定義一組動畫   
```
@keyframes anime
anime → 可以自己命名, 定位到你要的 CSS 元素讓他動起來
例如: 
.box-1 {

 left: 50px;

 animation:  anime  3s infinite;

                ↑定位 ↑秒數 ↑ 無限動茲動茲               
```

==裡面用數值定義==  
- 用 0 ~ 100%, 去控制元素運動 ↓  
- 單位是秒(s)  

![](https://i.imgur.com/BNSkv5r.png)   

![](https://i.imgur.com/t4O98Lr.png)   


- `@keyframes`  這種像是逐格動畫 ↓  
 ![](https://i.imgur.com/9AlzhXk.png)   
 
 
![](https://i.imgur.com/OzGFaMr.png)  
↑ 5 秒 跑到哪~  10 秒跑到哪, 100 秒跑到哪~  
如果設定跑十秒, 就會是 2.5 秒( 25% ), 5 秒( 50% ), 10 秒 ( 100% )   

- 會有提示彈出 ↓  
![](https://i.imgur.com/XmN1WLQ.png)   

- 啟用動畫的時候, 要有標籤名, 跑十秒(只跑一次) ↓ 
![](https://i.imgur.com/qsXGjja.png)   

- 控制次數↓   
![](https://i.imgur.com/pGpTIQT.png)   
預設 1  
==infinite: 無限次==  



- [(MDN) animation-fill-mode](https://developer.mozilla.org/zh-TW/docs/Web/CSS/animation-fill-mode)
![](https://i.imgur.com/aA5Qr3m.png)  ↓    


 - [(MDN) animation-play-state:](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-play-state) ↓   
 > 預設似乎是 running  
播放 (running) 或是暫停 (paused)   
![](https://i.imgur.com/tjTSwhM.png)   


- [(MDN) animation-direction:](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-direction) ↓  
> alternative, 動畫播完後再反著撥放一次  

![](https://i.imgur.com/o50DBxr.png)   


- [(MDN) animation-delay](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-delay) (動畫延遲多久來撥放) ↓   

---

# 屬性內的值可以縮寫   

![](https://i.imgur.com/7wJsCpV.png)   

要撥放甚麼動畫, 撥放多久, 撥放幾次, 播完後再反向撥放一次   

# 範例, 有沒有往上跑  

- 讓這些方塊一起往上跑   

![](https://i.imgur.com/pMLvjSs.png)  

![](https://i.imgur.com/VBIUIFM.png)   

---

# 緩動函數(貝茲曲線公式) 
- timing function  
- 太複雜的要用 JS 寫   
現實生活不是突然動起來或停止, 也無法一直均速運動   

![](https://i.imgur.com/BmtjMvn.png)   

↓ https://easings.net/ 找貝茲曲線函數, 把這加速度拿來用一下   
![](https://i.imgur.com/oqG7Vf8.png)   

↓ 跑起來   
![](https://i.imgur.com/cWWuGZN.png)  

↓ 借用一下函數  
![](https://i.imgur.com/bBz0ULr.png)   

↓ 動起來的範例   
![](https://i.imgur.com/hsaNna5.png)     

# 自己玩的作法:

- html 結構   

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./css/style.css">
</head>
<body>
    <div class="block">
        <div class="box box-1"></div>
        <div class="box box-2"></div>
        <div class="box box-3"></div>
        <div class="box box-4"></div>
    </div>
</body>
</html>
```

- ScSS 作法  
```
.block {
    position: relative;
    width: 1400px;
    height: 700px;
    border: 1px solid black;
    
    .box {
        top: 250px;
        bottom: 250px;
        position: absolute;
        width: 100px;
        height: 100px;
        background-color: crimson;
        border: 1px solid black;
    }

    .box-1 {
        left: 50px;
        animation: anime 3s infinite;
        transition: transform 0.6s cubic-bezier(0.61, 1, 0.88, 1);
        animation-direction: alternate;
    }
    .box-2 {
        left: 350px;
        animation: anime 3s infinite;
        transition: transform 0.6s cubic-bezier(0.65, 0, 0.35, 1);
        animation-direction: alternate;
    }
    .box-3 {
        left: 650px;
        animation: anime 3s infinite;
        transition: transform 0.6s cubic-bezier(0.25, 1, 0.5, 1);
        animation-direction: alternate;
    }
    .box-4 {
        left: 950px;
        animation: anime 3s infinite;
        transition: transform 0.6s cubic-bezier(0.76, 0, 0.24, 1);
        animation-direction: alternate;
    }
}
@keyframes anime {
    25% {
        transform: translate(100px);
    }
    50% {
        transform: translate(50px);
    }
    100% {
        transform: translate(200px);
    }
}
```

# 這樣會讓方塊在中間不等速跑:
![](https://i.imgur.com/4ZCylfu.png)   


# ==參考資料:==   
https://easings.net/   

[CSS animation-timing-function 属性 (w3school.com.cn)](https://www.w3school.com.cn/cssref/pr_animation-timing-function.asp)   

[transition-timing-function - CSS | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/transition-timing-function)  

[前端新手村 細說 Timing function - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10195313)   

---

# CSS @ keyframes 應用 - 擬真   

- 讓 CSS 模仿現實生活的真實物理動作  
- 像是這顆球   
 ![](https://i.imgur.com/REnRQTT.png)   
 -@ keyframes 可以搭配 transition 來用  

# ==參考來源:==  
掉下去的時候有點減速, 彈起來有加速   
![](https://i.imgur.com/QV91Y3f.png)  

## 雖然說做動畫不是前端本業, 不過可以試著做做   

---

# 可以試試看這個球 跟按鈕漸變   

![](https://i.imgur.com/FnK0bGm.png)   

# 練習 - 漸變卡片, 打 X 方塊, 漢堡變 X, 彈跳球   

- html 結構  
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./css/style.css">
</head>
<body>
    <div class="container">
        <div class="row">
            <div class="col-4">
                <div class="prouct-card">
                    <h1>產品</h1>
                    <p>產品敘述 / What? / No? / No way!</p>
                </div>
                <div class="cross">
                    <div class="line line-1"></div>
                    <div class="line line-2"></div>
                </div>
            </div>
            <div class="col-4">
                <div class="prouct-card">
                    <h1>產品</h1>
                    <p>產品敘述 / What? / Yes? / Yes we can!</p>
                </div>
                <div class="cross-2">
                    <div class="line-x line-top"></div>
                    <div class="line-x line-mid"></div>
                    <div class="line-x line-bot"></div>
                </div>
            </div>
            <div class="col-4">
                <div class="prouct-card">
                    <h1>產品</h1>
                    <p>產品敘述 / What? / No? / No we can't!</p>
                </div>
                <div class="wrapper">
                    <div class="bounce-ball"></div>
                    <hr>
                </div>
            </div>
            <div class="col-4">
                <div class="prouct-card">
                    <h1>產品</h1>
                    <p>產品敘述 / What? / Yes! / Yes! Yes!</p>
                </div>
            </div>
        </div>
    </div>
</body>
</html>


```

- Scss 結構   
```

```


# 也可以試試看讓方塊跑四個點  
```
 ↓ ←    
→ ↑
```
