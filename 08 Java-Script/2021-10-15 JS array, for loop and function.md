# 10/15 JS array, for loop and function   
###### tags: `JS` `2021/10/15` `進度筆記` `前端心得`  
---

講師: 林俊生 老師   

---

# 先複習一下  

## Variables related   
-  盡量用小駝峰 myNameIs  這種命名法   
-   VS code 會幫你把保留字變色  
-  變數宣告的時候不要用中文字  

---

- Var 是在 ES 6 以前常使用的   
- Let  可以只在一段作用, 但值可以改變   
- Const 一樣可以只在一段作用, 是唯讀值   

---
---

- 有些東西 IE, 甚至 IE 11都不支援   
- 像是 ES6 (不過之後會比較能用到)  
- 例如 object-fit  (可以替換元素寬高) , 不過  ie 也不支援   

- 記得重複使用到的東西可以用變數儲存起來  
```
var car = '跑車'
console.log(car)
```

----
## array  
 
- 索引值從 0 開始 !  

## 多維陣列   

- 那如果這樣呢:  
- 想辦法拿出 6  
```
var x = ['1', '2', '3', ['4', '5', '6']]
console.log([3][2])
```

- 再急轉彎一題  
> 怎麼拿 d ?  
> ![](https://i.imgur.com/mAwF6IV.png)   

---

## for loop 複習  
- for(起始條件; 結束條件; 步進值)  
- 網頁上似乎比較少用到雙迴圈  

![](https://i.imgur.com/7NXRzqF.png)   


- for loop 應用到卡片生成  
![](https://i.imgur.com/wXTdJMV.png)   
> 可以變成這樣   
>![](https://i.imgur.com/Wd1XyTn.png)   

---

## 實作分頁標籤   
- 複習土法煉鋼   

---

# 參考資料  

[序言 · 從ES6開始的JavaScript學習生活 (gitbooks.io)](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/intro.html)   

[object-fit - CSS | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/object-fit)  

[object-fit - CSS（层叠样式表） | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit)

   [CSS object-fit Property (w3schools.com)](https://www.w3schools.com/csS/css3_object-fit.asp)   
   
   [jQuery實戰手冊 (gotop.com.tw)](http://epaper.gotop.com.tw/pdf/AEE032431.pdf)  


----

# 上午的部分 - 接續分頁按鈕作法  

- 開始回到正題  
- 如果用 `querySelectorAll()` 的話, 盡量用複數的變數名稱  

## 一開始先抓所有 dom 元素   
![](https://i.imgur.com/lT1KVg6.png)   

- 然後複習 querySelectorAll 會抓到 nodelist, 他不是 array, 
> 像這樣  
> ![](https://i.imgur.com/nU62Dmo.png)


- 點怎麼關掉其他 tab 和內容?  
![](https://i.imgur.com/Z4BUVfv.png)   
![](https://i.imgur.com/t4ZDaZB.png)   

## 換個角度, 先關其他人的, 再打開第 0 個 tab 和內容  


- 因為程式從上往下讀  
> 如果你按下去 tab 後, 所有 tab, 內容(content) 的樣式都會被加入  
> 所以在觸發後, 加入 tab 發光和 content 出來前   
> 所以先安排清除再安排觸發  
> ![](https://i.imgur.com/gwnNMF2.png)   
> 我們把所有的樣式都先關掉, 再加入  
> ![](https://i.imgur.com/3FjPue4.png)   

![](https://i.imgur.com/9EHKiSY.png)  

- 記得想辦法理解每句話, 然後再寫出來   
- But, 上面還有個問題, content 還在  
```
contents\[i\].classList.remove('act');

```
> 一樣在迴圈內加上  removclasslist  

# 參考資料  
[Document.querySelectorAll() - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)   

[HTML DOM querySelectorAll() Method (w3schools.com)](https://www.w3schools.com/jsref/met_document_queryselectorall.asp)  

[HTML DOM querySelectorAll() 方法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/jsref/met-document-queryselectorall.html)  

[NodeList - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/NodeList)  

[NodeList 與 Array 差異 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10211876)   

[JavaScript DOM Nodelist (w3schools.com)](https://www.w3schools.com/js/js_htmldom_nodelist.asp)  

[NodeList 接口，HTMLCollection 接口 - JavaScript 教程 - 网道 (wangdoc.com)](https://wangdoc.com/javascript/dom/nodelist.html)  

[將 Node List 轉換成陣列 (jstips.co)](https://www.jstips.co/zh_tw/javascript/converting-a-node-list-to-an-array/)   

[使用原生 Javascript 寫 tab 切換效果 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10228825)   

[javascript實現前端分頁功能_程式設計_程式人生 (796t.com)](https://www.796t.com/article.php?id=164919)   

[前端分頁功能（通用）\_osc\_45536bvu - MdEditor (gushiciku.cn)](https://www.gushiciku.cn/pl/pjnO/zh-tw)   


---

# 試著用不同角度來看  tabs 這件事情  
- for loop 可以控制每個東西, tab content  
- 但因為綁定的事件實在太多了, 不可能每次都寫 for loop(太過繁瑣)  

> ![](https://i.imgur.com/nWNykQL.png)   
> 所以呢˙˙˙ 我全都要 !     

---

# 用上 ==`for each`==  
- 以下都是模擬 array  
- 可以用來遍歷 array 內的內容  
![](https://i.imgur.com/lAVtSuM.png)   
> 把 array 內的所有東西(tabs)全拿出來  > 
> ![](https://i.imgur.com/gBDhpIf.png)  
> ![](https://i.imgur.com/ltd9nlS.png)  
> 會把裡面的東西分別拿出來一次  
> ![](https://i.imgur.com/kO3aJdB.png)  

- 所以外面 tab function(命名上只拿一個 tab)  
> ![](https://i.imgur.com/ey4WAjA.png)   

- 自己 try 一下~  
> ![](https://i.imgur.com/rF9XSTt.png)  
> 因為抓的是所有 tab !
> forEach 比較快, 也比較有效率~  

---

## 但其實最根本的問題來了, 我們沒有陣列  
- 原本我們用 index [] 去判斷  
- 但現在我們要怎麼知道誰是誰, 我們沒有 array  

- 丟個 e 進去看一下  
![](https://i.imgur.com/nPLW5ha.png)  
> 看到太多東西了@@ ↓   
> ![](https://i.imgur.com/wR56zD5.png)  
> 因為按下的 event(縮寫 e)  是 tab 所以拿一堆    

- 好, 那我們代個參數進去  
> ![](https://i.imgur.com/ReODgXI.png)  
> 這樣 e.target 可以直接鎖定拿到你點(`onclick() `)下去按鈕的 tab  這個事件(event)  
> target(你到底點了誰, 發生了甚麼 event)  
> ![](https://i.imgur.com/iUD66Qc.png)  
> 我點下去知道是哪個東西在做操作  

## 點亮他!  

![](https://i.imgur.com/d0kOoWz.png)  

![](https://i.imgur.com/eYrqqOj.png)   


# 參考資料  
[Array.prototype.forEach() - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)   

[JavaScript forEach() 方法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/jsref/jsref-foreach.html)   

[JavaScript Array forEach() Method (w3schools.com)](https://www.w3schools.com/jsref/jsref_forEach.asp)   

[JS 迴圈升級的陣列 Array 方法 forEach() - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10228571)   


---

# 下午的部分   

- content 比較沒有跟 tab 在對應上的關係  
- 如果內容(相對位置)對不起來怎辦  
- 這樣顯示起來比較不好用   

---

# 所以給他對應關係  
![](https://i.imgur.com/rbYNLVw.png)   
![](https://i.imgur.com/jixZg5f.png)   


- 我們來幫他自定義屬性！  
> ![](https://i.imgur.com/nvzREGj.png)   
> 多給他一個名字 ！
> 可以抓到整個元素  


- 然後再用 getAttribute  
- 這樣就可以拿到 content   
![](https://i.imgur.com/H4DGk2c.png)  
> 接著拿 element  
>![](https://i.imgur.com/EMc6zMT.png)   
```
⤒ . 表示省略 class attribute    
用 getAttribute 去抓 data-content  
```

>![](https://i.imgur.com/b9uuAQ6.png)    
> 拆開來看的話會是這樣 ↓   
> ![](https://i.imgur.com/0ybZ402.png)   

---

# 把 tab 下的 content 刪除!  
- 點完每個分頁後, 把前一個分頁的內容移除~  

- 所以多上一個 forEach   
- 來對你點完後的頁面做處理   
> ![](https://i.imgur.com/TrZIR76.png)   
> 來對 content 做處理   



# 參考資料  

[data-* - HTML：超文本標記語言 | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/HTML/Global_attributes/data-*)   

[HTML Global data-* Attributes (w3schools.com)](https://www.w3schools.com/tags/att_global_data.asp)   

[HTML data-* 属性 (w3school.com.cn)](https://www.w3school.com.cn/tags/att_global_data.asp)   


[Element.getAttribute() - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Element/getAttribute)   

---

# ==`function()`== 函式   
- `console.log` 其實就是函式~  
> ![](https://i.imgur.com/azCKtR4.png)  
> 其實我們也可以做函式  


- 像是 一加到十的作法:  
```
let result = 0 
for(let i=1; i<=10; i++) {
    result+=i
}
console.log(result);
```
- 但如果今天 有三種,　要 1 + 到 10, 2 + 到 20, 3 + 到 30 呢?  
> 可能會這樣  
> ![](https://i.imgur.com/psJfTuj.png)  
> 這樣三個功能寫三次超麻煩  

- 這樣累加的功能可以打包的！  
- **Accumulation**   
- ↑ 這函式名字是可以自己取的！
>  ![](https://i.imgur.com/0kzmqNq.png)  
- 怎麼使用函式, 用 ↓  
```
函式名字(代入你要做的事情或數值)  
function name(x)
```
>  ![](https://i.imgur.com/zSI3OZC.png)   


- 印出 45 ↓  
![](https://i.imgur.com/7DKsDkB.png)   
```
從 5+6, 5+7, 5+8 一路加到 10 
```


---
---

> 如果不想要 `console.log`   
> 我們也能把值傳出去  
> 用 return  ↓  

> ![](https://i.imgur.com/1Wq8lhN.png)  

> ![](https://i.imgur.com/a2dBcvH.png)  

---

- 也可以返回出裡面的變數 ↓    
> ![](https://i.imgur.com/pO5kyFX.png)  

---

- 也可以把 function 存起來(把它當變數一樣!)   ↓  
> ![](https://i.imgur.com/i6MooWF.png)  

---

# 課堂練習  
- 輸入數字, 印出相對應的星星數量  
- printStar 經典題   

> printStar(5)  
> > printStar(10)  
> > > printStar(20)  

- 自己 try  
```
 <script>
        function print(stars, many) {
            let result = '';
            for(let i=stars; i<=many; i++) {
                result+= '*'
            }
            // console.log(result);
            return result 
        }        
        console.log(print(1, 5));
        console.log(print(1, 10));
        console.log(print(1, 20));        
    </script>
```
![](https://i.imgur.com/GNxMQun.png)


- 你也可以弄個 div, 然後 innerHTML 塞進去  

---

# 參考資料   
[重新認識 JavaScript: Day 10 函式 Functions 的基本概念 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10191549)   

- Need charge  
[JavaScript 全攻略：克服 JS 的奇怪部分 | Udemy](https://www.udemy.com/course/javascriptjs/)   

[前端JS演算法之列印星星_其它_程式人生 (796t.com)](https://www.796t.com/article.php?id=248945)   


---

# 課後作業 - 色盲作業  
- 參考這個  
[免費色弱測試﹣暴走微遊戲 (ioxapp.com)](http://game.ioxapp.com/eye-test/game.html)  
> 做出來XD  

![](https://i.imgur.com/3ZJINuU.png)   

![](https://i.imgur.com/C16jjz3.png)   
- 切一個畫面放四個正方形(或自動生成?)  
- 把其中一個畫面換顏色  
- 點下去後換顏色

![](https://i.imgur.com/CgfhsLN.png)  
> 外面邊框沒變  
> 大小也一樣  
> 不過框內的方塊數量改變囉！

  ![](https://i.imgur.com/CSJzYgY.png)  
> 用 display flex 記得要給寬高  
> 方塊的邊距是用 border 推出來的   
![](https://i.imgur.com/y1QNzeB.png)   


> 下一步, 怎麼長不同顏色?  
> 或是觀察他, 其實他每一步有多加一個同顏色數值  
> 或是有沒有其他做法~  ?  

- 給個 opacity  
> ![](https://i.imgur.com/d73EOx8.png)  
> 降低透明度  

# 課後任務條件  

1. entry level:    
```
2*2 同顏色可以重複遊玩
按一次方塊換一次顏色
一直玩一直爽
```
2. Level 2 :   
```
2*2 不同顏色, 也可以重複遊玩
按一次方塊換一次顏色
```
3. 方塊數量隨遊玩次數增加  
4. opacity 隨遊玩次數減少  
5. 增加定時功能   

## 課程條件: 能達成 entry 就可以惹  

- 大 guy 執行方向  

1. 綁定 click  
2. 換顏色  
3. 綁定 click  
4. 重置版面把顏色換一下  
5. 換方塊 inner.HTML  

- 如果有機會體驗翻牌遊戲  

---

