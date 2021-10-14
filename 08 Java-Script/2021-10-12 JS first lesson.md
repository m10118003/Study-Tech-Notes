# 10/12 JS first lesson  
###### tags: `JS` `2021/10/12` `進度筆記` `前端心得`  
---

講師: 佘昌霖   

---

# 上午的部分 - 檢討成績分級系統 (if else)   
1. 分數怎麼進來？  
2. 怎麼判斷分數(條件)？  
3. 要怎麼輸出條件(`console.log`)？

![](https://i.imgur.com/BWvGVNx.png)   
```
console.log('perfect') → 字串  
console.log(perfect) → 未命名的變數
```

---

# 成績分級(基本題) - if 的特性  
- 分數, 分級判斷   
![](https://i.imgur.com/pJyT5Fq.png)   

- if 會根據條件來判斷   
```
例如區間內的這行 ↓ 
else if (grades >= 90 && grades < 100)
看完 `>=90` 以上的區間後, 就可以不用寫 100 > grades 的情況, 可以直接寫 >=90就好

以此類推 >=80, >=70......

```

- 做例外處理的部分  
![](https://i.imgur.com/FntwxRu.png)   
> 非常有增進使用者體驗的想法!  

- 一次輸出的方法  
- 把值存在變數內, 最後再印出來  
![](https://i.imgur.com/tWUZUbP.png)   
> 會少一點字數  

---

# 課外 - 如果有分享的程式碼   

![](https://i.imgur.com/dwwyVus.png)   

- 如果有公益性質的分享程式碼  
- 建議不要照抄, 做點改動  
- 至少註解拿掉~  
- 上 github 看看這段 code 授權使用方式   
- 例如 swiper 專案內可以使用, 但建議用上引用來自哪裡  

---

# 實作按鈕 - input 取值  
- 怎麼把值丟掉輸入框內?  
- 按下按鈕才計算成績  
![](https://i.imgur.com/d172g9Z.png)   
> 可以用 querySelector (深度追蹤 DOM 元素, 例如沒有 ID 的元素)去替換 getElementById(很高效的可以直接鎖定 ID)  
> querySelector 有抓到 ID  

- 用 button.oncilck 讓 button 這個變數透過儲存的值去抓 html 的 button tag  
![](https://i.imgur.com/s6D9Dop.png)   

- 要怎麼取得 input 內的值?  
![](https://i.imgur.com/HFus5za.png)  
> input 這個 tag 本身提供預設的字串或數字值 `value`  
> 所以我們要怎麼去抓這個 value?  

![](https://i.imgur.com/6IynSKW.png)   
> 這樣會是網頁一載入, 程式一跑, 就直接先讀 value  
> 而 value 的預設是 20 (數字)   
> 所以之後按按鈕也都是顯示 D (數字 20)  
```
因為沒有寫到按鈕執行時, 要讓按鈕去做的事情, 按鈕要做的事情應該是: 
0. 先有按鈕這個東西
 <button id="getResult">計算成績 >/button>
 
1. 按下去後連到哪邊去算成績 → id  
連到文字框(id score)的輸入值value

querySelector(`#score`).value
2. 讓這個值在對的地方做對的事情  
丟到 button.onclick 這個函式下面  

3. 也可以讓 value =""

```

- 讓 `querySelector(`#score`).value` 丟到對的地方  
![](https://i.imgur.com/zG6AEPR.png)   


# 參考資料:  
[HTML DOM Input Text value Property (w3schools.com)](https://www.w3schools.com/jsref/prop_text_value.asp)   

[Document.getElementById() - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)   

[document.querySelector - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document/querySelector)   

---

# 複習一下 - 變數是代名詞   
![](https://i.imgur.com/hcVcZjD.png)  
> 讓程式好看點   

---

# 用 JS 更改 html  - 輸出在網頁上   
- 怎麼改輸入的內容  
- 然後讓更改的內容輸出結果在網頁上
```
document.write(''<p>'')
```
> 只能寫在網頁最下面  
![](https://i.imgur.com/rYOOZZi.png)  

```
innerHTML
```
> 可以直接修改網頁文字  
![](https://i.imgur.com/h2HwGZl.png)  

- 拿來用用看  
> 測試一下  
![](https://i.imgur.com/nRFGWyR.png)   
> ''你的分數是100分, 你的成績是perfect!''

- 如果這樣幹的話會是物件 ↓   
![](https://i.imgur.com/nJ1LL3y.png)   

---

- 遇到個問題, 如果有人99分, 怎麼讓90分這個字替換成99  
# 字串運算子  
```
字串與字串相加
'Strings'+'Strings'
```
![](https://i.imgur.com/Vybagoq.png)   
```
'你的分數是' + score + '分, 你的成績是 "A+"'
```


# 參考資料  
[JavaScript HTML DOM - 改变 HTML (w3school.com.cn)](https://www.w3school.com.cn/js/js_htmldom_html.asp)

[運算式與運算子 \- JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_operators#%E5%AD%97%E4%B8%B2%E9%81%8B%E7%AE%97%E5%AD%90)

----

# 如果遇到靈異現象怎辦?  
- 有人輸入奇怪值怎辦?  
![](https://i.imgur.com/H3iBHiJ.png)   
> 如果是這種負值的狀況  
![](https://i.imgur.com/HACgXIk.png)   
> 可以用 scroe < 0 來判斷   

```
因為兩個 if 是分開看得, 
所以加個 else
```
![](https://i.imgur.com/BTp8xA7.png)   
> 如果執行  `if`  
> ``else if(負值)``    
> ``else if(空值)``    
> ``else if(字串)``   
> ``else if(小數)``  
> else 除此之外(執行)   
> 如果執行 `if`   

![](https://i.imgur.com/inErljo.png)   


---

# JS 宣告的型態  
- JS 宣告的時候是以他的儲存型態決定  
- 當數值運算的時候, 會嘗試將變數轉換成數字  
![](https://i.imgur.com/F3X1zUC.png)  
> score 也適用  

- 所以空白的時候也適用上面的規則, 被轉換成 0 了  
> 解決問題, 要怎麼偵測"空白"為 0 的問題  

```

```

# 參考資料  
[isNaN() - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/isNaN#%E6%8F%8F%E8%BF%B0)  

---

# 預告下午有作業  

# 在外部時是字串    
> 進來後是數字   
![](https://i.imgur.com/a0uWdj4.png)   

---

# 繼續解決輸入空白的問題  

- 可以用`parseInt()` 去解決問題   
![](https://i.imgur.com/sVBADvt.png)  
 ```
 這樣可以解決 空值, 非數字(中英文, 特殊符號), 空白
 ```
 ![](https://i.imgur.com/tAPq2d5.png)  
> `parseInt` 會將字串轉成數字   
>  人用十進位, 電腦常見的是十六進位
>   例如 RGB 是十進位, #FF0000 是十六進位   

# 參考資料   
[parseInt() - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/parseInt)   



---

# 接著解決負值   
![](https://i.imgur.com/Bwj4rMe.png)  
> -0 = 0   

---

# 剩下小數   

- 土法煉鋼   
![](https://i.imgur.com/77Ha9rg.png)   
> 或是   
```
除以一看餘數是否等於 0 
```
- 測試一下   
![](https://i.imgur.com/VZ8oZC9.png)  

- 將輸入的分數, 除以一取餘數後不等於 0   
![](https://i.imgur.com/DRZxSGO.png)   

---

# 記得還有大於 100 分的情況   
- 考慮進來後就完成了!  
![](https://i.imgur.com/rTuNjHF.png)   

---

# 課堂練習 - 做 BMI 系統   
![](https://i.imgur.com/96DTZZp.png)   

- BMI 計算   
![](https://i.imgur.com/I2z2vLu.png)  
> 需要做例外處理(提示方法不限):  
> 版面需自行製作(HTML & CSS)   
> 必須有輸入和輸出區塊   
> 開始計算沒東西的話要跳警告   
![](https://i.imgur.com/8WNd0jL.png)   
> 結果輸出方塊必須有淡入淡出效果(預設隱藏, 按下開始計算後出現)  
> 按下重新計算的按鈕會自動清空輸入框的內容(同時隱藏輸出區塊)   
> 身體狀態: 過輕 輕 正常   
![](https://i.imgur.com/UXDP2Aj.png)   
> 建議參考: 自由發揮  

# 參考資料   

[BMI值計算器 (femh.org.tw)](http://depart.femh.org.tw/dietary/3opd/bmi.htm)  

[利用 原生 的 funciotn 觀念寫一個 BMI 計算機 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10229952)   

[JS - BMI計算機 - Rita Ho (recafox.github.io)](https://recafox.github.io/2020/02/03/2020-02-03/)   


---

