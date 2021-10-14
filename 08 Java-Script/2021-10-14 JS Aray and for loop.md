# 10/14 JS Aray and for loop   
###### tags: `JS` `2021/10/14` `進度筆記` `前端心得`  
---

講師: 佘昌霖   

---

# 上午的部分 - new stuff   

- 之前介紹很單純的存一筆資料的型態   
```
Number, Boolean, string....等  
```

# 陣列(array)   
- 如果今天的東西非常多   
```
var car = '休旅車'
var car2 = '浪漫跑車'
var car = '豪華到爆的房車'
.
..
...
如果有 42 台車呢?
要怎麼方便管理呢??

```
> 東西太多不太可能一個一個宣告   
> 這時候可以用陣列來存取一堆數量的值   

- 宣告方法    
- 陣列的建立   
```
var bike = []
var bike = ['AAA-4520', 'DVD-4587', 'WWW-4841']
```
> 這樣可以放一堆資料  
> 陣列的最後一個元素不要加上逗號   

---

- 存取方法  
```
any[index]
```
- 如果要拿值的話   
- , log輸出   
```
var bike = ['AAA-4520', 'DVD-4587', 'WWW-4841']
console.log(bike[1])
```
> 會拿到 'DVD-4587'   
> 程式中索引值(index)是從 0 開始的,    

---

- 改值的方法   
- 陣列改其中一個的值  
```
var bike = ['AAA-4520', 'DVD-4587', 'WWW-4841']
機車[2] = 'WWW-4850'
console.log(bike[2])
```

- 保留字   
```
var  var = ' '
var 2car
var ca!r

會報錯
```
> 宣告有一些規定:  
> 不能有保留字, 像是 var, if, 有特定功能的字   
> 不能用數字開頭, 例如 2car   
> 不能有奇異符號! , 除了 `$`(ES6 儲存變數) 和 `_`   

- JS 宣告建議命名規則:  
```
當你的變數有兩個英文單字所組成, 可以用小駝峰的方式命名  
```
> 小駝峰與大駝峰都是用單字併在一起, 不過大駝峰是所有單字大寫, 小駝峰是第一個單字不用大寫  
```
大駝峰 MyNameIs
小駝峰 myNameIs
```

---

# 參考資料   
[JS 隨意修、刪、改的陣列 Array 方法 splice() - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10225345)   

[JavaScript保留字 (w3bai.com)](http://www.w3bai.com/zh-TW/js/js_reserved.html)   

[JavaScript 保留词 (w3school.com.cn)](https://www.w3school.com.cn/js/js_reserved.asp)   

[词法文法 \- JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Lexical_grammar)   

[ES6 深入理解` ${}`  模版_超逸の学习技术博客-CSDN博客_es6](https://blog.csdn.net/weixin_42429718/article/details/104593324)   

[浅析Js中`${}`字符串拼接 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/187577719)   

[ES6 Destructuring 陣列和物件的解構賦值 - JavaScript (JS) 教學 Tutorial (fooish.com)](https://www.fooish.com/javascript/ES6/array-and-object-destructuring.html)      

---

# 陣列應用   

- 用 JS 新增畫布   
```
div {
    width: 100px;
    height: 100px;
    background-color: 'crimson'
}


<div id="canvas"></div>

let canvas = document.querySelector('#canvas')
canvas.innerHTML = '<div></div>'
```
> 這樣可以用 JS 新增兩個紅色方塊   

==但如果今天有一大堆方塊, 100個 上千萬個方塊呢？==

---

# 迴圈(for loop)  
- 迴圈(loop)  
- 我們可以用迴圈生成一大堆方塊   
- 如果要執行很多次重複的作業時, 可以使用迴圈   
```
for(let index = 0; index < array.length; index++)
```
> for 迴圈的建立, 共有三個區塊, 區塊之間以分號(;) 區隔   
> ![](https://i.imgur.com/0GapwzF.png)   
> index 貫穿全場  
```
宣告; 判斷; 用算數運算子累加
```

![](https://i.imgur.com/vmyMEFV.png)  
> 當然不用回傳十次  


- 在 loop 內的執行動作  
```
for(let index = 0; index < array.length; index++) {
    console.log('haha')  
}

let > index > console.log > index++ > index > console.log > index++..... 直到不符合判斷式之後迴圈就會結束
```
![](https://i.imgur.com/GObDlrr.png)   
> 橘>藍>紅>綠>藍>紅>綠...   

# 參考資料   
[運算式與運算子 \- JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_operators#%E7%AE%97%E8%A1%93%E9%81%8B%E7%AE%97%E5%AD%90)   

[for - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)   

----

# 課堂練習  
- 試著印出 20~59數字序列   
```
使用 for loop, 來印出 20~59 的數字   
```
```
    <script>
        for (let i = 20; i <= 59; i++) {
            console.log(i);
        }
    </script>
```
> ![](https://i.imgur.com/BP3Jupx.png)  
> 通常 index 縮寫 i  
> 


---

# 超級挑戰  

- 挑戰
```
*
**
***
**
*
```

# 參考資料:  
[APCS-大學程式設計先修檢測 (ntnu.edu.tw)](https://apcs.csie.ntnu.edu.tw/index.php/questionstypes/previousexam/)  

---

# 好, 有了索引和陣列就能征服宇宙了(x)  
- array 可以跟 loop 結合   
> ![](https://i.imgur.com/bCSVTlC.png)   
> 可以全部印出來!  

- 如果陣列長度很長   
- 所以我們直接改變長度就好  
> ![](https://i.imgur.com/14QtQOn.png)   

> ![](https://i.imgur.com/ZUXrTkp.png)   
```
用 .length 來抓全長  
```

---

# 今天的下午目標  
> ![](https://i.imgur.com/SWYQ16F.png)  
> 實作這個分頁功能   

---

# 要怎麼把迴圈的值輸出到畫面上?  
> 用之前有套 tag(div), 和樣式   
![](https://i.imgur.com/nWVk7He.png)  
> 但這樣不會跑出來  


![](https://i.imgur.com/kptiQaS.png)   

![](https://i.imgur.com/T4h8lF8.png)  

---

# 應用到生成卡片式欄位  
- 嘗試用for迴圈去印出重複的東西   
- card  
- 做之前記得套 CSS 樣式  
![](https://i.imgur.com/rhzskrq.png)   

---
- 下 html 標籤  
![](https://i.imgur.com/4hOVUg9.png)  

---
- 用 querySelector 去抓 id   
![](https://i.imgur.com/C0psdjB.png)   
> 然後用 dom = dom+div h1 去累加  

---
- 如果在字串後加上 index  
![](https://i.imgur.com/p6zhuv8.png)  
> index 會出現在圖片外框, 變成圖片右邊有數字  

---
- 如果在 字串之間加上 index  
![](https://i.imgur.com/Bc2p7hS.png)   
> 就會出現圖片內有標題數字   
> ![](https://i.imgur.com/q24roy4.png)  

----

- 但如果這樣子只會印出 1~99 個卡片  
![](https://i.imgur.com/ysRafz6.png)  
> 可以用 index<= 100 或是 (index+1)   


# 練習一下  
- 試著印出 div於canvas上   
- 做到這樣  
![](https://i.imgur.com/HjRdGgu.png)  

- 花式XD   
![](https://i.imgur.com/NQJsby0.png)   

<!-- ![](https://i.imgur.com/SMdAOGT.png)-->

- 可以用重音符號 ``" ` "``   去標整段的 string    
```
<script>

      // let card = document.querySelector('.card');
      // for (let i = 0; i < 6; i++) {
      //     card.innerHTML = card.innerHTML + '<div><h3>我是卡片' + (i+ 1)+ '</h3><img class="meme" src="https://i.imgur.com/SMdAOGT.png"><p>覆蓋一張牌, 結束這回合 !</p></div>';

      // }  
      let   card = document.querySelector('.card');
      for (let   i = 0; i < 6; i++) {
          card.innerHTML = card.innerHTML \+ `<div><h3>我是卡片 ${(i + 1)} </h3><img class="meme" src="https://i.imgur.com/SMdAOGT.png"><p>覆蓋一張牌, 結束這回合 !</p></div>`;
        }
  </script>

```
> ↑ 這部分可以直接換圖, 因為 imgur 的 cors 問題, 所以用連圖的方式有點小問題(不過 files 可以直接開看到圖)   
- 但其實上面整體架構有點問題  
- 這是用 JS 去生成 div 和 h3, img 等  

---

# 下午的部分  
- 正確的作法 html → css → js  
- 先弄個 htnl 和 css 排版看有沒有問題  
- 最後才去弄 JS   

---

# 頁籤樣式做法 - demo   
- 基本骨架  
> ![](https://i.imgur.com/qwjqp8T.png)  

- 上個樣式  
> ![](https://i.imgur.com/1WO3MUV.png)   

- 外框樣式  
![](https://i.imgur.com/vAEJlFK.png)  

- 做出按鈕感  
> ![](https://i.imgur.com/IyPqNFu.png)   
> ![](https://i.imgur.com/SXba8PX.png)   
> now 是做給按鈕分頁用的, 按下去會發光~   

- 做出內容的範圍   
> ![](https://i.imgur.com/YbdiqnX.png)   

- 加個 act 造成 display block 效果   
![](https://i.imgur.com/9g49bdg.png)  
> 給 content 文章用的  

# 參考資料  
[中英文假字、文章產生器（Lorem Ipsum）介紹 | Allstars 網頁設計 - 星辰資訊購物車/形象網站專家 (the-allstars.com)](https://the-allstars.com/blog/website-knowledge/introduction-to-chinese-and-english-fake-characters-and-article-generators-lorem-ipsum.html)  

---

# 頁籤的 js 架構  

- 找出誰(頁籤切換)  
> ![](https://i.imgur.com/1i42BFa.png)  
> 一樣先去拿 dom 元素  

- 找出甚麼時候做甚麼事情(切換文章內容)  
- 頁籤切換 - 綁定onclick事件
>  ![](https://i.imgur.com/9xZ9iCO.png)  

- 在自己相應的地方按下去會有反應  
- 驗籤切換 -  classlist賦予/移除
> ![](https://i.imgur.com/BIuGVCf.png)   
> 如果沒有 remove 第二, 三頁的文章內容會跑出來, 像這樣↓  
> ![](https://i.imgur.com/qLDfcLY.png)  


- tab1 的作法  
> ![](https://i.imgur.com/Zs2gCVc.png)  
> 土法煉鋼法  

- tab2 的作法  
> ![](https://i.imgur.com/hl2eVds.png)  
> tab3 以此類推  


---

# 快, 還要更快 !  
- 如果今天四個還好, 但如果超過上百個呢@@!?  
> ![](https://i.imgur.com/PJXSBIl.png)   
> 這時候可以用陣列 !   

---

# 理解利用 `querySelectorAll` 去抓取元素   
- 很多一樣的時候來試試看陣列儲存變數   
> 用 `querySelectorAll`  抓到的會是一個陣列  

- 試試看用 querySelectAll  
>![](https://i.imgur.com/phDyUr3.png)   
> 如果用索引值去抓可以發現他能抓到陣列  
> ![](https://i.imgur.com/AwGJnK3.png)  

- querySelectAll 只要能抓到一筆資料, 就算只有一筆, 也是會以陣列的情況呈現   
> ![](https://i.imgur.com/olyppuI.png)   
> ![](https://i.imgur.com/JM9ioFv.png)  
> 要用陣列抓索引的方式去指向  

---

# 先抓 DOM  

![](https://i.imgur.com/Yue6f3h.png)  

---

# 用陣列呈現   

![](https://i.imgur.com/V3ieQzP.png)   

---

# 用 for loop 幫你推陣列  
- querySelectorAll 會抓你指定的屬性陣列  
- querySelector 是抓你指定的屬性   
> ![](https://i.imgur.com/2D9As7Z.png)  

```
tab[0].onclick = function() {
    console.log('按到第一個');    
}

tab[1].onclick = function() {
    console.log('按到第二個');    
}

tab[2].onclick = function() {
    console.log('按到第三個');    
}
```

---

# 用 for迴圈一口氣 - 去綁定onclick事件   

- 所以可應用 foe loop 來抓 tab 和 content  
> ![](https://i.imgur.com/zzPKPki.png)  
> 因為是選用索引值去抓  
> 所以 tab[0] 的時候會抓第一個分頁   
> tab[1] 會抓第二個分頁  


- 大概等於這三行 ↓   
> ![](https://i.imgur.com/5qiAMcz.png)   
> but, 不完全一樣   
> 因為綁了一模一樣的 function  
> 所以 用 tab[index] 的 index 去區分, 因為 for loop 的關係, 他會幫你去從 0 開始推第一個按鈕  

---

# 用 index(for loop 的 索引值)去增加  `classlist` 並綁定 content  
- 利用index(for loop的 index 值)  
- 可以將增加 `classlist` 這件事綁定在相同索引值上面的 `content`   

- 更清楚一點的看    
> ![](https://i.imgur.com/vpbjVKT.png)  
> 每個按鈕有對應的變數順序  

- 所以可以改寫成這樣 ↓  
> ![](https://i.imgur.com/uj3a5Ih.png)   
> 這樣按按鈕會讓分頁內容跳出來  
> ![](https://i.imgur.com/fkZPMHB.png)   

- 那我要怎麼按下 remove ?  
> To be continued... →   


# 參考資料  
[HTML DOM querySelectorAll() Method (w3schools.com)](https://www.w3schools.com/jsref/met_document_queryselectorall.asp)  

[HTML DOM querySelectorAll() 方法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/jsref/met-document-queryselectorall.html)   

[document.querySelector - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document/querySelector)   

[\[CSS3\]word-break 文字斷行規則 | 男丁格爾's 脫殼玩 (abgne.tw)](https://abgne.tw/css/css3-lab/css3-word-break.html)  

[CSS word-break 属性 (w3school.com.cn)](https://www.w3school.com.cn/cssref/pr_word-break.asp)   

---

# 課程規劃部分  
- 團體專題的時間  
> 要求溝通能力   


- 課程專題的時間結束後  
- 還是能做個人專題   
> 求職表現標的  
> 展示個人製作能力的結果   
> 持續製作   
> side project 可以訓練自己組織一件事情   
> 然後去達成一個目標    

- 課程表 prototype → 自己的個人專題   
- 商業實例主題(團體)製作 → 自己的個人專題   

- 團體專題的部分 → 20 天左右做完整的網站出來   
> 怎麼把自己的話表達給合作夥伴和業主聽得懂   
---

