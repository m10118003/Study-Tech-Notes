# 10/08 JS first lesson  
###### tags: `JS` `2021/10/08` `進度筆記` `前端心得`  
---

講師: 佘昌霖   

---

# JavaScript 的使用時機   
- 用在 CSS 無法作用的不同層   
- 因為 CSS 目前只能控制自己父子層   
- 比較、運算類比較等需要用到的時候   
```
1. 誰  
2. 甚麼時候   
3. 做甚麼事情   
```
可以使用 ↓  
```
document.querySelector('#boxA')
document.querySelector('#boxB')
```
> 在 JS 中可以使用 `document.querySelector()` 與 CSS selector 去選特定的元素  

---

# 用 JS 去抓元素 - 例如改變顏色這回事   

如果每次都要打一長串的字是很麻煩的, 可以把這個字用變數儲存 ↓  
```
var document.querySelector('#boxA')
var document.querySelector('#boxB')
```
> 宣告變數, 變數就像代名詞一樣  
> 方便在程式中不用每次都打很長~  
![](https://i.imgur.com/IRJuNVj.png)   

---

# 怎麼確定有沒有選到 boxA ?  

- 如果要確定有沒有選到, 可以用 log 去檢查  
```
console.log(boxA);
```
> 可以做完一個階段就使用一次去檢查~  
![](https://i.imgur.com/RmhqNU2.png)  


---

# 點擊事件   

- `onclick`   
```
boxA.onclick = function() {
    console.log(boxB);
}
// 當 A 被點擊的時候要做的事情放在這裡
```
> 點下去, 去 dev tool 看 console 就會有選到~  

![](https://i.imgur.com/ww8EO1X.png)  

# 匿名函式   
[重新認識 JavaScript: Day 10 函式 Functions 的基本概念 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10191549)  


---

----

# 改變顏色   
![](https://i.imgur.com/Wv9S1Pw.png)  
 > 改變顏色通常由 CSS 去改  
 > 試著不改變 html 的標籤情況下, 用 JS 來修改 class, 更動 boxB 的顏色  

- 自己 try   

![](https://i.imgur.com/3JenOZG.png)  

![](https://i.imgur.com/o5cAExt.png)   

![](https://i.imgur.com/J51KZeT.png)   


# 參考資料:    
[透過 JavaScript 動態修改CSS 樣式、屬性](https://ithelp.ithome.com.tw/articles/10226003)   
[javascript修改元素css样式的三种方法（代码）-js教程-PHP中文网](https://www.php.cn/js-tutorial-408825.html)  


---

# 小部分不一樣的地方  

---

```
document.getElementById() 
document.querySelector()
getElement 是類似 querySelector 的, 不過 ById 只能抓 Id
好處是不用加 '#' 字號
```

```
btn.onclick → 點擊事件(btn 按鈕), 是預設基礎事件, 可以設定值~
addEventListener → 聆聽事件用途很廣, 像是滑鼠點擊, 變動事件, 聆聽點擊, 滑鼠移動等, 很多功能, 寫法可以很複雜(常見函式)
```

# 參考資料   
[EventListener - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/EventListener)   

---

# 搜尋資源利用 - [Stack Overflow - Where Developers Learn, Share, & Build Careers](https://stackoverflow.com/)   

- 搜尋解釋  
- 解答參考  
- 教學問答   
- 全球最大工程師聊天社群   

---

# DOM 元素不是動元素  

**請問甚麼是 DOM 元素 ?**   

```
html 把這個 code, 文字等等 當作一個物件, 那你就可以利用 API 去對這些物件進行互動!
```

用 DOM 去存取屬性, 例如用 .click 去存取 html 的 class 或 Id  
```
element → <div(tag) class="boxA">內容(content)</div>
屬性(attribute) → class="boxA"

```

- DOM 操作, 例如用 `innerHTML`  
![](https://i.imgur.com/IUO2SKl.png)   

---

- 複習一下:  
![](https://mdn.mozillademos.org/files/9461/css-declaration-small.png)  
[CSS 基本 - 學習該如何開發 Web | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Learn/Getting_started_with_the_web/CSS_basics)  
[HTML 基礎 - 學習該如何開發 Web | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Learn/Getting_started_with_the_web/HTML_basics)   

---

# 複習一下屬性  
[JavaScript - 物件 與 屬性 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10193605#:~:text=%E5%B1%AC%E6%80%A7%E5%B0%B1%E6%98%AF%20key%2Fvalue%20%E7%9A%84%E7%B5%84%E5%90%88%20key%EF%BC%9A%20%E4%B9%9F%E5%B0%B1%E6%98%AF%20%E9%80%99%E5%80%8B%E5%B1%AC%E6%80%A7%E7%9A%84%E5%90%8D%E7%A8%B1%EF%BC%8C%E4%BB%BB%E4%BD%95%E5%AD%97%E4%B8%B2%E9%83%BD%E5%8F%AF%E4%BB%A5%E4%BD%9C%E7%82%BA%20key%EF%BC%8CJavaScript,%E4%B8%AD%E7%9A%84%20Array%20%28%E8%A8%BB%202%29%E5%B0%B1%E6%98%AF%E4%B8%80%E5%80%8B%E5%BE%88%E5%A5%BD%E7%9A%84%E8%AA%AA%E6%98%8E%E7%AF%84%E4%BE%8B%E3%80%82%20value%EF%BC%9A%20%E5%9C%A8%20value%20%E4%B8%AD%E5%8F%AF%E4%BB%A5%E6%94%BE%E5%85%A5%E4%BB%BB%E4%BD%95%E5%9E%8B%E5%88%A5%E7%9A%84%E5%80%BC%EF%BC%8C%E7%95%B6%E7%84%B6%E4%B9%9F%E5%8C%85%E6%8B%AC%E7%89%A9%E4%BB%B6%E3%80%82)   

# 參考 DOM 模型:  

[文件物件模型 (DOM) - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document_Object_Model)   


[什麼是DOM？ @ 學習日誌 :: 痞客邦 :: (pixnet.net)](https://chenmike.pixnet.net/blog/post/25948952)   

[W3C DOM 簡介 (openhome.cc)](https://openhome.cc/Gossip/JavaScript/W3CDOM.html)   

[JS 筆記 - 認識 DOM 文件物件模型 | TimCodingBlog (hsuchihting.github.io)](https://hsuchihting.github.io/javascript/20200615/1316819935/)   


[Day03-深入理解網頁架構：DOM - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10202689)   

[Day03-深入理解網頁架構：DOM - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10202689)


---

# 課外知識 - html5 的新增值

```
.setAttribute() → 傳統法, 會覆蓋所有值(包含原本的 CSS property & value)
現在 html5 新增可以用指定值:
.classList.add()
.classList.remove()

```

---

# 回來改顏色  

![](https://i.imgur.com/LSNA8iK.png)  

![](https://i.imgur.com/MPuqtI8.png)   

![](https://i.imgur.com/2RK9fD3.png)   

![](https://i.imgur.com/acLX1jK.png)   

不過, 這樣點 A 換 B 有點小麻煩, 要怎麼只點 B 換 B ??  

---

# 題外話 - 看到突然有東西冒出來   
- 這是 JS 在幫你做事情

- boxB 那行原本沒有 attribute  
![](https://i.imgur.com/4PatEGp.png)   
- 點一下方塊就跳出來 attribute  
![](https://i.imgur.com/9mCvglw.png)   


---

# 連續點連續換色   

- code 有各種解法, 靠著前人智慧(上網找)去找解法~  
- 希望點 boxA 會在兩種顏色間切換   
```
<style>
    .boxA {
        width: 200px;
        height: 200px;
        background-color: crimson;
    }
    .boxA.orange {
        background-color: #ED784A;
    }
</style>
<body>
    <div class="boxA"></div>
    <script>
        let boxA = document.querySelector('.boxA')
        boxA.onclick = function() {
            let orange = document.getElementsByClassName(".orange");
            boxA.classList.toggle("orange")
            console.log(boxA);
        }
        
        
    </script>
```
- 用 `toogle()`~   
- 好像是我們要的   
- 會在一個元素(class)一直切換有跟沒有的狀態   
- 除了會切換, 還會 return true / false   
-  用法很多  
   
![](https://i.imgur.com/RwNs7av.png)

- ↓ 像這種, 有兩行都是寫了 `toggle` 的都對  
![](https://i.imgur.com/FtaIO6n.png)   
-  不過程式執行是千毫秒(1/1000 s)在算, 所以螢幕和點擊切換速度也沒這麼快   

- true, 像是add 的功能, 保持在切過去的狀態   
![](https://i.imgur.com/advVi9R.png)   
![](https://i.imgur.com/PiXGPiK.png)   
- 像是, 如果寫 false, 就像是 remove 的功能  
![](https://i.imgur.com/gXZqQzh.png)   
![](https://i.imgur.com/8OdyOE4.png)   
- 不加的話就是同時是 remove 也是 add   
![](https://i.imgur.com/pFruFCZ.png)   
> 可以切換顏色   

- 自己 try  
![](https://i.imgur.com/2OFPEMa.png)  

# 參考資料:   
[Element.classList - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Element/classList)   

[HTML DOM classList Property (w3schools.com)](https://www.w3schools.com/jsref/prop_element_classlist.asp)  
[\[Day 11 - JS\] 互動吧網頁 — Javascipt的DOM 操作 / 事件 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10263778?sc=hot)  

[修改 DOM 元素樣式 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10271907)   

----

# 下午的部分 - `else(), if() / else if()`      

- 很多時候沒有判斷依據或標準的   
- 如果今天要改 class 以外的東西   

---

# if 判斷式  

- 寫 if 至少需要釐清的條件  
```
if + 判斷條件
```
> 可以用 if 去判斷條件  
> 結果是符合的(true), 符合判斷條件就執行 if 內部的 code   
> 如果結果是 false, 就會離開不執行 if 的 code   
> 大事化小, 小事化無~  

- true  
![](https://i.imgur.com/LENbOvr.png)   
- false  
![](https://i.imgur.com/87Dg6ef.png)   

- If 的條件, 除了 true / false 外, 可以輸入各種條件  
- 運算元可以是數字，字串，邏輯，或物件的值(by MDN)   
- 例如數字間的比較   
```
if(35>32) {
    console.log('又老了一歲')
}
```

- 例如比較運算子  
```
console.log(!true)
```
>會反轉 true 印出 false     

- 應用一下   
![](https://i.imgur.com/7iLd6if.png)  

# 參考資料   

[運算式與運算子 \- JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_Operators)   

---

# 拉回來, 我們用 if 變顏色   

![](https://i.imgur.com/pXNnsKP.png)   

![](https://i.imgur.com/dwYeJ0w.png)   

---

# 如果用反轉的邏輯?!  
- 加了顏色後  
- add 顏色  
- 結果 remove 刪除了顏色  
![](https://i.imgur.com/IH50VtW.png)   
> 跑不出來   

---

# 用 if...else...   

- 只用 if 可以做到簡單判斷, 但如果今天有不同狀況  
- 例如執行不同動作, 就要搭配 else 使用  
```
if (寫出判斷條件) {
    有符合就執行
} else {
    不符合就執行
}
```
> 用一個 if...else 跟很多個 if 跑起來效率差不多~  
> JS 中, 單純的 if...else...可以幫忙做到二分法  
> 但當條件很多, 就必須層層過濾, 像是漏斗  
> 缺點就是寫太多的時候, code 的閱讀性就會變差  
> 原始狀態, 例如每星期都會看不同的電視頻道   

![](https://i.imgur.com/dC5RSFD.png)   

```
else if 的可讀性會好一點~
```

![](https://i.imgur.com/4MAT9XI.png)   


---

- 用反轉 `!` 的情況去改變顏色  

![](https://i.imgur.com/0tLa0fj.png)  
> 如果他不是橘色 (因為有 `!` )   
> 加入橘色  
> 印出 boxA  
> 否則移除橘色  
> 印出 boxA  

![](https://i.imgur.com/9rXMoTQ.png)   


---

- 不用反轉 `!` 的情況去改變顏色  

![](https://i.imgur.com/PoRFiSK.png)   
> 如果它含有橘色   
> 移除橘色  
> 否則加入橘色   

![](https://i.imgur.com/DjozW9V.png)   


---

# 參考資料  
[陳述式與宣告 \- JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements)   

[HTML DOM classList Property (w3schools.com)](https://www.w3schools.com/jsref/prop_element_classlist.asp)  

[Element.classList - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Element/classList)  


---

# 課堂練習  
- 找兩張圖片, 有網址的  
![](https://i.imgur.com/58X8WGC.png)   

> html 只能有一個 img 標籤  

- 從 DOM 拿東西(html 元素)!  
```
    <script> 
        let pic1 = "https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg"
        let pic2 = "https://hololivetw.com/wp-content/uploads/2021/09/e38090e8bfb7e59ba0e5adb8e7bf92e68890e995b7e697a5e8a8982e38091e58e9fe69cace8a681e78ea9e68190e68096e9818ae688b2-e7b590e69e9ce88ab1-365x205.jpg"

        let img = document.querySelector('img')
        console.log(img)

        img.onclick = function() {
            if (img.src == pic1) {
                img.src = pic2
            } else {
                img.src = pic1
           }
       
        }        
    </script>
```

- 自己 try  
> if statement  
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    
    <img id="meme_pic" src="https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg" width="589px" height="331px"/>

    <script> 
        let noMercy = document.getElementById('meme_pic');
        let switchOn = true; // Boolean: true 1 false 0;

        noMercy.onclick = function() {
            // if(noMercy.src == "https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg") {

           
            // If here's the statement, just use it, if not → create the statement to do something;
            
            if(switchOn) {
                noMercy.src = "https://hololivetw.com/wp-content/uploads/2021/09/e38090e8bfb7e59ba0e5adb8e7bf92e68890e995b7e697a5e8a8982e38091e58e9fe69cace8a681e78ea9e68190e68096e9818ae688b2-e7b590e69e9ce88ab1-365x205.jpg";
                switchOn = false;
            } else {
                noMercy.src = "https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg";
                switchOn = true;
            }         
            
        };
    </script>

</body>
</html>
```

![](https://i.imgur.com/S10Kj8r.jpg)   
![](https://i.imgur.com/jxWU2sD.jpg)   

- Same result ↑  
- Ternary operator   
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    
    <img src="https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg" class="komame" id="meme_pic" onClick="change_pic()" width="589px" height="331px";>

    <script> 
       function change_pic() {
           let imgObj = document.getElementById("meme_pic");
           let Flag=(imgObj.getAttribute("src",2) == "https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg")
           imgObj.src = Flag ? "https://hololivetw.com/wp-content/uploads/2021/09/e38090e8bfb7e59ba0e5adb8e7bf92e68890e995b7e697a5e8a8982e38091e58e9fe69cace8a681e78ea9e68190e68096e9818ae688b2-e7b590e69e9ce88ab1-365x205.jpg":"https://i.ytimg.com/vi/8vBN47bw7zg/maxresdefault.jpg";
       }
    </script>

</body>
</html>
```


# 參考資料   
[if statement - JavaScript if判斷切換圖片 - IT閱讀 (itread01.com)](https://www.itread01.com/content/1545892144.html)   

[if statement - JS自學之if判斷小示例 | 網頁設計教學 (aiwalls.com)](https://www.aiwalls.com/javascript%E7%B7%A8%E7%A8%8B%E6%95%99%E5%AD%B8/19/38707.html)   

[Ternary operator - js對圖片的操作不改變_如何用js控制img中src圖片路徑改變_互聯網編程博客 (zymseo.com)](https://www.zymseo.com/big5/program_217320)   


---


# DOM 元素練習使用  


- img.src 使用  
![](https://i.imgur.com/jBwiGcF.png)   
> 我必須知道現在的圖片是甚麼  
> 我要知道來源   

---

# 三張圖的解法  

- 不受位置干擾的方法   
- 新增一個判斷是否換圖的變數   
![](https://i.imgur.com/c98Gg28.png)   
> 用檢查條件的方式來做   
> 多宣告一個條件來試試   

![](https://i.imgur.com/r70yPaD.png)   

- 自己 try
- 1 → 2 → 1 → 3 → 2 1 3 → 2 1 3   
```
<body>
    
    <img id="meme_pic" src="./img/01.jpg" width="589px" height="331px"/>

    <script> 
       let pic1 = "./img/01.jpg"
       let pic2 = "./img/02.jpg"
       let pic3 = "./img/03.jpg"
       let picNum = 0

       let img = document.querySelector('img')
       
       img.onclick = function() {
           console.log(img)

           if (picNum == 0) {
               img.src = pic2
               picNum = 1
           } else if (picNum == 1){
               img.src = pic1
               picNum = 2
           } else {
               img.src = pic3
               picNum = 0
           }
       }

    </script>

</body>
```
![](https://i.imgur.com/d4BCRUf.png)   

- 照順序玩法   
- 1 → 2 → 3  
```
<body>
    
    <img id="meme_pic" src="./img/01.jpg" width="589px" height="331px"/>

    <script> 
       let pic1 = "./img/01.jpg"
       let pic2 = "./img/02.jpg"
       let pic3 = "./img/03.jpg"
       let picNum = 0

       let img = document.querySelector('img')
       
       img.onclick = function() {
           console.log(img)

           if (picNum == 0) {
               img.src = pic2
               picNum = 1
           } else if (picNum == 1){
               img.src = pic3
               picNum = 2
           } else {
               img.src = pic1
               picNum = 0
           }
       }

    </script>

</body>
```
![](https://i.imgur.com/uMxI0Vp.png)   


---

# 三張圖字串 `match()` 的解法   


- 用 `match()` 檢查 img.src 是否有單引號的字串  
```
string.match('')
不過有個問題, ()內放的東西要找差距
```
> 檔案資料夾或檔案名稱不同, 是可以切換圖片的   
![](https://i.imgur.com/RUu0Jg0.png)   
![](https://i.imgur.com/IQjQYr6.png)   

> 如果檔案路徑剛相同像這樣  
![](https://i.imgur.com/Hkjhgt4.png)  
> 只能切換一次   



# 參考資料   
[JavaScript match() 方法 (w3school.com.cn)](https://www.w3school.com.cn/jsref/jsref_match.asp)  
[Day8 動手寫HTML(3) - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10219156)   

---

# JS 內有巢狀結構   

![](https://i.imgur.com/3JCEjAh.png)   

---

# 課後任務  
> 實作一個成績分級系統, 如果成績在 100, console.log 出 "Perfect"  
> 實作 90~99 console.log 出 "A+"  
> 實作 80~89 console.log 出 "A"  
> 如果成績 70~79 印出 "B"  
> 如果成績 60~69 印出 "C"  
> 如果成績在 59 以下 印出"D"   
例如用:  
![](https://i.imgur.com/HOAsZIJ.png)   
```
基本要求: 成績在這邊填入 0~100 之間的變數
進階要求: 使用 input 跟 button 將數值輸入進來
```
![](https://i.imgur.com/oJyYfKw.png)   

- 自己 try   
- switch case  
```

    <script>
        let grades = 100    

        switch(grades) {
            case (100):
                console.log("Perfect")
            break
            case (99):
            case (90):
                console.log("A+")
            break
            case (89):
            case (80):    
                console.log("A")
            break
            case (79):
            case (70):
                console.log("B")
            break
            case (69):
            case (60):
                console.log("C")
            break
            case (59):
            case (0):
                console.log("D")
            break
        }
        

    </script>
```
![](https://i.imgur.com/xl0Km26.png)   

- else if   
```

    <script>
        let grades = 100

        if (grades >= 100) {
            console.log("Perfect")
        } else if (grades >= 90 && grades < 100) {
            console.log("A+")
        } else if (grades >= 80 && grades < 90) {
            console.log("A")
        } else if (grades >= 70 && grades < 80) {
            console.log("B")
        } else if (grades >= 60 && grades < 70) {
            console.log("C")
        } else if (59 >= grades) {
            console.log("D")
        }        

    </script>
```
![](https://i.imgur.com/pQEdVWh.png)   

- w/ btn  
```

    <script>
		function grades() {
			let grades = document.getElementById("score").value
			if (grades >= 100) {
				alert('Perfect')				
			} else if (grades >= 90 && grades < 100) {
				alert('A+')
				// console.log("A+");
			} else if (grades >= 80 && grades < 90) {
				alert('A')
				// console.log("A");
			} else if (grades >= 70 && grades < 80) {
				alert('B')
				// console.log("B");
			} else if (grades >= 60 && grades < 70) {
				alert('C')
				// console.log("C");
			} else if (grades >= 59) {
				alert('D')
				// console.log("D");
			}        
		}
    </script>
```
![](https://i.imgur.com/gOz98zY.png)   


# 參考資料:   

[JavaScript 基礎知識-switch 判斷式 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10211560)    

[Javascript：将考试成绩转换为字母等级的按钮|小空笔记 (xknote.com)](https://www.xknote.com/ask/611173f72610b.html)

---

![](https://i.imgur.com/macieKe.png)   

---