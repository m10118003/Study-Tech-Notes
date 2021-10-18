# 10/18 JS Detect color game, object, JSON, JS-API   
###### tags: `JS` `2021/10/18` `進度筆記` `前端心得`  
---

講師: 林俊生 老師  
佘昌霖 老師  

---

# 先複習一下  

## 常見三種 html 傳值方法:  
1. onclick="doit('aa')"  
2. dom 元素 抓 value  
3. dara-* attribute   

---

# 除了三種常見的資料, 還有甚麼傳資料的方法?  

> 例如, youtuber 從後端傳資料到前端頁面, 有應用生成   

![](https://i.imgur.com/TfL48Ru.jpg)   


# 樣版字串:   
```
寫了一張卡片的樣版後, 讓JS 去幫你自動生成, 內容跟資料會根據後端傳的資料去應用   
```

# 參考資料:  

[鐵人賽：JavaScript Template String 樣板字串 | 卡斯伯 Blog - 前端，沒有極限 (wcc723.github.io)](https://wcc723.github.io/javascript/2017/12/22/javascript-template-string/)   

[10\. ES6 - 樣板字面值 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10243733)   

[\[JS學徒特訓班\] JavaScript ES6 樣板字串(Template String) - 斜槓女紙 - Medium](https://medium.com/coding-girl-life/js-es6-templatestring-5eddbd29d8e9)   

[\[JS\]Template Literals(字串樣版) - HackMD](https://hackmd.io/@chrisHsiao/BykaBsBa8)   

[\[筆記\] JavaScript ES6 中的模版字符串（template literals）和標籤模版（tagged template） ~ PJCHENder<br>那些沒告訴你的小細節](https://pjchender.blogspot.com/2017/01/javascript-es6-template-literalstagged.html)   

[PJCHENder那些沒告訴你的小細節](https://pjchender.blogspot.com/)


[ES6 Template Literals 字串樣版/字符串格式化 - JavaScript (JS) 教學 Tutorial (fooish.com)](https://www.fooish.com/javascript/ES6/template-literals.html)   

[ES6 -- 字串樣板(String Template) (lucrelin.blogspot.com)](https://lucrelin.blogspot.com/2016/11/es6-template-strings.html)



---

# 複習 Key & Value   

> 在不同的地方 key & value 的寫法也不同  
> 例如:  

- 陣列中   
```
let carplate = ['aaa-1234', 'bbb-5789']
```

# 在物件中的 key & value  

- 物件 (object)   
```
let car = { // declare object
    engine: '2.0', 
    brand: 'toyota',
    size: 'big', 
    color: ['blue', 'gray'],
    wheele: 4, 
    break: {
        front: 'plate',
        real: 'drum'
    },
}
```
- 可以塞其他的資料型態 (data-type)  


- 可以存很多東西, 和用分門別類的方式下去  
![](https://i.imgur.com/mdYbntN.png)  
> 拿值的方式  
```
console.log(car)
car.engine = '5.0'  // let value on object(attribute); 物件特定屬性的賦值
console.log(car.engine)  //物件特定屬性的取用  
```

-  試一下怎麼拿灰色  
```
console.log(car.color[1])
```

- 怎麼拿物件中的物件?  
```
console.log(car.break.front)

```

![](https://i.imgur.com/Tshjd1B.png)   
> 不是陣列不能這樣取值(不過也有取 {} 的用法)

- 物件特定屬性的取用(就像 dom)  
```
console.log(car.engine)
```

- 物件特定屬性的取用(搜尋索引的方式)  
```
console.log(car['brand'])
console.log(car['color'][0])
```

- 複習一下陣列   
```
let garage = [carplate, car]
```
> 陣列裡面也可以放置其他陣列(變成多維陣列, 但這種比較少用)   
> 多維陣列可能給值印表格才會用到   
>  也可以在陣列裡面放物件  
> 例如:     
```
console.log(garage[1].break.real)
```
![](https://i.imgur.com/vKiiUjm.png)   

- 這種陣列包來包去包一大堆資料的方式  
- 從後端來的時候會很常見到這種 key & value 的形式  

# 參考資料  
[【新手大哉問】property、key、value、reference，到底是什麼啦？ | by Tweert | Medium](https://medium.com/@twee301/%E6%96%B0%E6%89%8B%E5%A4%A7%E5%93%89%E5%95%8F-property-key-value-reference-%E5%88%B0%E5%BA%95%E6%98%AF%E4%BB%80%E9%BA%BC%E5%95%A6-b3a83c7723e4)   

[\[筆記\] 談談 JavaScript 中 by reference 和 by value 的重要觀念 ~ PJCHENder<br>那些沒告訴你的小細節](https://pjchender.blogspot.com/2016/03/javascriptby-referenceby-value.html#comment-3989590007)   

[深入探討 JavaScript 中的參數傳遞：call by value 還是 reference？ (techbridge.cc)](https://blog.techbridge.cc/2018/06/23/javascript-call-by-value-or-reference/)   

[重新認識 JavaScript: Day 05 JavaScript 是「傳值」或「傳址」？ - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10191057)  

[簡單介紹JavaScript參數傳遞 (slideshare.net)](https://www.slideshare.net/YiTaiLin/java-script-63031051)  

[Value vs. Reference - Step Up Your JS: A Comprehensive Guide to Intermediate JavaScript (educative.io)](https://www.educative.io/courses/step-up-your-js-a-comprehensive-guide-to-intermediate-javascript/7nAZrnYW9rG)   

[JavaScript 初心者筆記: DOM - 如何用 JS 更改 HTML & CSS 屬性 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10218025)   

[物件屬性取值 | Summer。桑莫。夏天 (cythilya.github.io)](https://cythilya.github.io/2019/10/31/object-get-value/)   

---

# 何謂 JSON  

- 其實是一種資料交換格式  
- 內容也有 key & value  
> 其實資料型態是字串  


![](https://i.imgur.com/2uIvPlE.png)  
> 只是這種資料格式就像物件一樣  
> 例如對 json `console.log()`  
```
當你從後端抓取資料 json 的時候, 你會得到的是 JSON 格式的 ''string''
```
```
如果想要轉為 object 使用, 必須轉為 JSON.parse()  

→ 這函式會將 json 的格式, 也就是 string 轉為 
object
```

![](https://i.imgur.com/JjO7S1b.png)   
![](https://i.imgur.com/KaTLBxb.png)   

```
用 console.log(typeof userObject)
去抓 可以得到 object 的 data-type

所以也就可以衍伸利用
console.log(userObject.address.city)
 
 ```
 > 當資料使用(修改)完成後, 如有需要可以再用 JSON 的格式方式去傳到你要的地方  

- 這轉成物件的過程式可逆的
```
let carJson = JSON.stringfy(car)
console.log(typeof carJson)
console.log(carJson)
```
> ![](https://i.imgur.com/EXjSZHK.png)  
> 如果今天有上百筆資料, 慢慢取會花很多時間  
> 用 JSON 可以一口氣傳遞所有資料給後端  
> 讓後端儲存  

# 參考資料    

[JSON - 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/zh-tw/JSON)  

---

# 練習跟中央氣象局開放資料平台串接 API  

- 要先辦會員拿授權碼  
- 可以指定參數再執行(不指定會全拿)   
```
透過網址去拿 JSON 格式  
```

![](https://i.imgur.com/Bzkt6j6.jpg)   
> 今天會做這個  
> 大概三千多行

# 參考資料  
[g0v-data mirror](https://g0v-data.github.io/mirror/)  
by Dave  

---

# 檢討一下 - 找色塊遊戲  
==第一級, 重複遊玩==

![](https://i.imgur.com/PvdfGmV.png)

![](https://i.imgur.com/27K5uXj.png)  

> ![](https://i.imgur.com/JLDSFik.png)  
> 這邊 div 沒有分行跟列  

- 如果今天有變動的話  
> 這個寫法會有點危險 ↓  
> ![](https://i.imgur.com/wDSIScF.png)   

- 可以讓他變單層, 讓他一層就做完  
> ![](https://i.imgur.com/Ttb9vyo.png)   
> 這樣怎麼做 ?
> 在 display flex 加上 wrap  
> 其實沒有做出換行, 然後讓 JS 丟給 CSS 和 html, 讓他一直推方塊下去   

---

## 試著用 function 寫法  

- 做出來, 讓這邊等於 `2*2` 方塊   
> ![](https://i.imgur.com/5bBezET.png)   

- 然後用 for loop 去推  
> ![](https://i.imgur.com/CqthnrI.png)   

- 接著給他在 html 下 .onclick  
> ![](https://i.imgur.com/09nvcrx.png)   
> 就可以去推方塊, 不過會超過邊(因為沒有設邊界)~  

- 接著, 要怎麼亂數產生顏色  
> ![](https://i.imgur.com/5m9c3Iy.png)   
> 
> 把原本 0~1 的小數(不含一), 變成0~9.9999  
> 因為小數加上 match.floor 去取整數(無條件捨去)  
> 所以會變成 0~9

- 所以接下來取亂數最好的方法  
```
Math.floor(Math.random()*你需要的範圍) + 你的起始數字)

例如取: 1~12
起始值是 1  End(你需要的範圍) 是 12  就會是 

Math.floor(Math.random()*你需要的範圍) + 你的起始數字)
1~ 12                                      12                             1
3~ 100                                     98                            3
```
> ![](https://i.imgur.com/HLuVFxP.png)   

- 加進去後就有亂數了  
> ![](https://i.imgur.com/omkVrWv.png)  
> 因為是累加 所以方塊會越來越多   

- 所以在按下的時候要把上一次的方塊全部清空  
> ![](https://i.imgur.com/PgLMpZJ.png)   

- 接著做一個判斷, 讓他會出現在不同區塊  
> ![](https://i.imgur.com/BEN3txz.png)   

## 接下來想一下偵測邏輯   
- 解法有很多種  
1. 因為會產生一個 class 的 ans 所以讓他用 ans 去判斷  
2. 讓他用全域宣告 去改變  
![](https://i.imgur.com/yoiE7y3.png)   

- 如果是以 ans 的 class 做變判斷的話  
> 因為是用 JS 產生的, 所以用 querySelectorALL 去抓` # main>div` 的話會抓不到   
> ![](https://i.imgur.com/XljtVvo.png)   

- 因此用 onclick 在 html 的話, 可以把他加在 if   
> 因為要按對方塊才做, 如果沒按對就不用做  
> 因為只有綁 onclick 其他都沒有綁   
> 也就是按對方塊才做, 因為沒有按錯方塊會發生靈異事件的選項XD  

![](https://i.imgur.com/3fAuubq.png)   
> 所以可以直接累加   

- 加完分後, 在做一個方塊  
> ![](https://i.imgur.com/3Ht4fKe.png)   

# 怎麼用 JS 去改顏色和 CSS  
==`第二級, 2*2 不同顏色、重複遊玩`==  

- 因為 div 沒有 querySelector 去抓到  
- 所以可以直接加上 inline-style!  
> ![](https://i.imgur.com/wjtI5lq.png)   

- 顏色有點淡, 調整一下XD  
> ![](https://i.imgur.com/oqChKJO.png)  

- 接下來怎麼改顏色?  
1. 用 rgb 的數值  
2. 怎麼寫進去   
> 改顏色   
> ![](https://i.imgur.com/SXRokyp.png)   

- 要怎麼丟值?  
> 樣版字串!  
> 宣告 rgb  = 亂數  
> ![](https://i.imgur.com/iT94zaC.png)   
> 如果不要顏色太淡, 可以往下降  
![](https://i.imgur.com/xUCiiEV.png)   


- 因為 html 不會算空白, 所以怎麼按空白都可以(除非字串內)  
> ![](https://i.imgur.com/8nybFkK.png)  


## 帶進樣版字串

> 用字串去串的寫法
> ![](https://i.imgur.com/f2zTXXC.png)   
> 這種寫法可能有 bug   
> 如果不是完整 html, 一次累加再帶出來可能會爆掉  
> 因為用字串畫面會很亂, 所以帶上用 ES6 的新寫法   

- 接著做出樣版字串  
> ![](https://i.imgur.com/gY8uVvr.png)   
> 做出樣版字串, `${} `

> ![](https://i.imgur.com/HSn5fAj.png)  
> 這樣就做完等級二了  

---

# 第三級  
==`三級: 方塊數量隨遊玩次數增加`==

- 接下來要判斷方塊增加的方法  
> ![](https://i.imgur.com/8PpSpwS.png)   
> 這樣變成 2*4+1, 因為是用父層去換行  
> 所以就爆了XD  

1. 讓父層的框框變大, 配合子層    
2. 讓裡面的框框變小, 配合父層框框

## 如果是選一的作法  
- 所以父層就會變成是做方塊的時候由父層決定  
> ![](https://i.imgur.com/rNHNxKW.png)   
> 但因為這樣不能用 px, 所以用樣版字串  
> 讓寬高都一起改變  
> ![](https://i.imgur.com/0HXlR5u.png)   
> ![](https://i.imgur.com/5srLKUr.png)   

![](https://i.imgur.com/P9hRZfk.png)


![](https://i.imgur.com/mZC1uVD.png)  

![](https://i.imgur.com/jFlHdXv.png)   


# 第四級  
==`四級: 透明度差異隨遊玩次數減少`==

- 可以加個 opacity  
> 但是顏色會隨著遊玩次數變淡   

- 如果第十題變淡, 分數就會是九分  
> 做出樣版字串去拿值, 因為改變了顏色變淡(下個困難度)  
> ![](https://i.imgur.com/8uaoAyJ.png)   


- 根據答題數來改變方塊透明度  
> 來判斷分數到時麼時候, 去改變 difficulty (opacity)  
> ![](https://i.imgur.com/a4rXmvm.png)   
> 要怎麼讓遊戲平衡不錯, 這跟 UX 有關係~  

# 第五級  
==`五級: 增加定時、成績功能`==

- 如果做懲罰機制, 可以在 onclick 下一些機制來做處理  
> 例如, 做錯會更新題目    
> ![](https://i.imgur.com/V4Im7py.png)   

- 接著要怎麼做 "定時" 這件事情  

##  ==setTimeout==  
> 多久時間執行一次   
```
(x, y)
x → 可以是指令(字串), 或函式

y 如果是 200 → 表示毫秒, 0.2 秒 

```
## ==setInterval==  
> 會一直持續執行  
> 而倒數計時, 應該是會一直執行的(時間一直倒扣)  
```
用法跟 setTimeout 大同小異~
```
- ES6 之前的匿名函式呼叫  
> ![](https://i.imgur.com/W1mRfUq.png)   

- ES6  
=>  

- 傳參數的方法  
> ![](https://i.imgur.com/UnSPQNj.png)   
> ![](https://i.imgur.com/vcoGAgU.png)  
> 不能給括符   


- 使用上會有誤差累積, 誤差會逐漸擴大  
- 精準度也需要微調  

---

## 造成時間差異寫法  
- 比較正式的寫法  
> 按下按鈕後, 應該會倒數計時, 再跑 makeBlock  > ![](https://i.imgur.com/GBx7EvW.png)   
> 按下去後變 60秒  

- 接著要扣秒數  
> 做一個可以執行扣秒的函式  
> 把 timeleft 轉換成數字
> ![](https://i.imgur.com/WTzLY01.png)  
> 按下後不只會給方塊, 還會扣秒數   

- 但是這樣會造方塊後, 又把時間給重置了  
![](https://i.imgur.com/riEpGM4.png)  

- 讓他開始遊戲的時候再去叫 makeBlock  
> ![](https://i.imgur.com/5SRust8.png)
> ![](https://i.imgur.com/5jvR594.png)   

- 這樣就不會重複了  
> ![](https://i.imgur.com/NX7ozFh.png)  
> 不過有個問題, 時間會一直扣下去扣成負值  

- 因此設定一下 timeleft = 0, 讓時間到了遊戲結束   
> ![](https://i.imgur.com/Kw9Vxmw.png)    
> 如何時間到了讓玩家不能再點?  

- Za wa ru do!  
- 讓時間停住  
- 給個 ID 後  
![](https://i.imgur.com/nxGKRbj.png)   

- 時間到了不給玩XD  
> ![](https://i.imgur.com/bJuLj9b.png)  
> 直接清空框框 XDDDDD   
> 創意發想, 給個 alert 遊戲結束, 或是有其他做法? 不要清空框框~  
> ![](https://i.imgur.com/Ykativx.png)   
> 其實也可以不用轉數字直接印出來!  

- 遊戲結束  
> ![](https://i.imgur.com/sDNgGhQ.png)   
> 不過發現遊戲可以累計  

- 所以按開始的時候分數要重計算  
> ![](https://i.imgur.com/i2conyX.png)   

```
讓參數返回(return)
```

==一個好的 code 應該把功能分開==  
> 增加功能的耦合性  
> 比較可以維護  

> 專案化公司, 耦合性稍高, 因為是客製化  
> 如果是, 耦合性比較低, 比較會有重複貼上, 也比較好維護  

# ==第六級==  
- 如果是 click 事件的話  
- 要怎麼按下才確定  
![](https://i.imgur.com/F8161GD.png)  
> 也沒辦法用 class 判斷(可以把 class 刪除看看~)  
> 不能用外再去判斷的時候要怎麼用 code 去判斷 ?  
> 依照 index 去做做看  
> ![](https://i.imgur.com/QfoB5nf.png)  
> 看 index 傳過來的數值對不對?  
> 不過要怎麼用 index 去傳?  
> 因為沒辦法用 queryselectorALL 去抓  

- 所以在造方塊的時候, 直接檢查索引值  
> ![](https://i.imgur.com/oglXuee.png)  
> 並做個判斷  
![](https://i.imgur.com/JxwsrbA.png)  
> 這樣會報錯,  因為 guess 的 ans 沒有定義  
因為, ans 寫在 function 裡面  
![](https://i.imgur.com/Cc4JrDn.png)  
> 所以把 ans 拿出來  
> ![](https://i.imgur.com/8Lg3cNK.png)   

# POC - 開發的時候要從小的地方開始   
- Proof of concept, POC  
- 確認規劃的想法, 概念, 流程是否可行~  
- 設定完整體後, 做個小規模的測試   
```
一個一個的測試, 如果業主一開始給得很大的東西, 也要有辦法做出從小地方開始測試  
```

---

# 參考資料:  

[\[筆記\]\[JavaScript\]用Math.random()取得亂數的技巧 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10197904)   


https://segmentfault.com/a/1190000016444812  

https://www.jb51.net/article/118860.htm   

[談談 JavaScript 的 setTimeout 與 setInterval | Kuro's Blog](https://kuro.tw/posts/2019/02/23/%E8%AB%87%E8%AB%87-JavaScript-%E7%9A%84-setTimeout-%E8%88%87-setInterval/)   

[setInterval() - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/setInterval)   

[JavaScript Day22 - setTimeout、setInterval - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10279012?sc=hot)   

[利用setTimeout(setInterval)做簡易倒數計時器 (victsao.com)](http://victsao.com/blog/81-javascript/78-settimeout-timer)   

[\[javascript\] 深入了解 setTimeout() 與 setInterval() 的不同之處 – camel 's blog (camel2243.com)](https://blog.camel2243.com/2016/08/06/javascript-%e6%b7%b1%e5%85%a5%e4%ba%86%e8%a7%a3-settimeout-%e8%88%87-setinterval-%e7%9a%84%e4%b8%8d%e5%90%8c%e4%b9%8b%e8%99%95/)  

[HTML DOM setInterval() 方法 (w3school.com.cn)](https://www.w3school.com.cn/jsref/met_win_setinterval.asp)

[\[Python 常用\] 實現 setInterval 定時器圈呼叫函式功能 — 1010Code (andy6804tw.github.io)](https://andy6804tw.github.io/2021/01/21/time-interval/)

[Window setInterval() 方法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/jsref/met-win-setinterval.html)

----

# 做一個類似倉儲(分類)系統   

- 結合跟 JSON 的練習使用, 來做一個頁面~  

# 練習導入 JSON 的格式   

# 做出這個畫面  

![](https://i.imgur.com/k7BMa8p.png)  
- sunyehfy good to eat  
- 刻一個版面  
- 進入網頁版全部商品列出來
- 按下飲料的時候只有飲料, 點主食的時候只有主食的菜單  
- 有 filter, 可以去選飲料   - 
- 甜點跟飲料裡面都有珍奶  

> ![](https://i.imgur.com/BNyuTEK.png)   


- 去串 JSON    
> ![](https://i.imgur.com/FJ0dZxZ.png)  

> ![](https://i.imgur.com/p4KCPNN.png)   

---

# 建立一個 上益好好吃的版面   

1. 先做卡片  
```
1. canvas 或 display 區塊
2. nav
3. div 
```
2. 需要導覽列區塊  

- nav   
> ![](https://i.imgur.com/8tBLh11.png)  
> ![](https://i.imgur.com/sDvJtAY.png)   
> ![](https://i.imgur.com/bllq7RL.png)   

- main   
![](https://i.imgur.com/U40kgME.png)

- 請 JS 幫忙之前, 自己先做一個 demo  
> ![](https://i.imgur.com/qB2TS5N.png)   
> tag 不用印, 拿來做分類    
> ![](https://i.imgur.com/C1wd2jf.png)   

- card 的 css  
> ![](https://i.imgur.com/IK79zux.png)   


- card 的 html  
> ![](https://i.imgur.com/Kc4pTN5.png)   
> ![](https://i.imgur.com/JBhhtw5.png)  


- car img, div, name 樣式  
> ![](https://i.imgur.com/pf73oFX.png)   
> ![](https://i.imgur.com/Cu1bMkX.png)  
> ![](https://i.imgur.com/sYkyBMI.png)   


- 為了確保沒有問題, 再複製一張 來看看有沒有問題  

- ![](https://i.imgur.com/LV0IdJU.png)   


- 用 margin  
> ![](https://i.imgur.com/vnorvus.png)   
> 10px 還好  
> 如果大 px 去推可能會偏掉  

- 如果螢幕 4:3   
> ![](https://i.imgur.com/wr1vBOT.png)   
> 再多讓兩個 div 出現在 html 上 去補足 evently   
> 有個小問題 rwd 4 變 2 的時候, 就要修改數值   

- html 請自由發揮  
> ![](https://i.imgur.com/GcadLRa.png)  

---

# 利用 for loop 將設計好的版面印出(相應數量)   

# 印出資料到圖片上  

- 這樣可以印出每筆資料  
> ![](https://i.imgur.com/bU5hFxg.png)   
> ![](https://i.imgur.com/5ptFnOp.png)   


![](https://i.imgur.com/Ns2k18t.png)   

![](https://i.imgur.com/AyLhoQE.png)

---

# 將卡片中的資訊 換成樣板字串   

- 用 `=` 的話, 會一直被洗掉   
> ![](https://i.imgur.com/GmNvpjl.png)   
- 可以用 ``+ =`` 去製造重複推的效果   
> ![](https://i.imgur.com/U5A9wm5.png)   


- 加個 ↓   
- ![](https://i.imgur.com/mXQQ3pe.png)  
![](https://i.imgur.com/WOLb1NA.png)   

- html 和 CSS 會影響到 JS 寫的方法!!!   

---

# for loop 往上移會有個問題  

![](https://i.imgur.com/XaPsrI8.png)   

> 會報錯  
> ![](https://i.imgur.com/fvI9Uzo.png)   
> 因為程式是一行一行讀的   
> 所以移到宣告前面就出是惹  

---

# JS 把卡片推出來   
- 像是這樣    
![](https://i.imgur.com/fWTrctK.png)   

----

# 將卡片中的資訊印出來   
- 把圖片用樣版字串去接   
> 把資料換上去  
> ![](https://i.imgur.com/XJNVNYu.png)   
> 會看到爆版  
> 調整一下圖片 CSS   
> ![](https://i.imgur.com/O7KdSGG.png)   

---

# 綁 onclick 參數  
- 在NAV上綁上onclick 事件, 並且可以使傳送條件方便判斷   
> ![](https://i.imgur.com/91Kg63V.png)   
> ![](https://i.imgur.com/CqBqAE3.png)   
> ![](https://i.imgur.com/kXQzsrP.png)   


---

# 將 for loop 寫成 function   

- 將 for loop 寫成 function 
- 這樣可以方便 nav 上面的按鈕去做呼叫的動作   
![](https://i.imgur.com/DmaH0rs.png)   
> 寫成 function, 用 show 去執行  
> ![](https://i.imgur.com/IKT1sRr.png)    

# 按下按鈕要清空一次  
> ![](https://i.imgur.com/ho04e9P.png)  
> 每個分類可以有對應的過濾條件  
> 但按下 all 甚麼都沒有  


# 讓按下 all 有東西出來   
- 在 innerHTML 執行前
```
使用if判斷 → "條件"是否符合 → 我們的 tag
```
- if 會加在 innerHTML 印出去之前   
- 如果傳過來的值是 all   
> ![](https://i.imgur.com/iBdrdrA.png)   

# 但飲料有, 甜點沒有珍奶  

> ![](https://i.imgur.com/9JfwTQE.png)   
```
為了解決珍珠奶茶有兩個 tag, 
因此用 or(||) 去判斷 tag1 跟 tag2
```
> ![](https://i.imgur.com/gu5ZsK6.png)  
> 要符合其中一個條件就印出來   
> 讓 if 判斷用 || 去製造兩邊中只要一邊的值成立就印出  
> ![](https://i.imgur.com/i01JK9d.png)  
> ![](https://i.imgur.com/HRLiKGu.png)   


---

# 可以再更精簡一點  
![](https://i.imgur.com/dsDSAlp.png)  
> 不過應該很吃效能 (Maximum call stack size exceeded)   
> 再改成單行敘述  
> 甚至可以去除 else   

>![](https://i.imgur.com/hIkhBRG.jpg)   
> 最後可以試試看, 看卡片能不能對齊   

> 如果要降低效能使用可以改成這樣 ↓ (不知道為啥, 可能是 i 的判斷條件多跑一行 =, 如果純粹用 < SY\_gooodToEat\_Product.length, 有卡死的情況   
> ![](https://i.imgur.com/G8CrE87.png)  



---

# 明天是設計課  - prototype?  

# 預告下次有天氣的卡片  
## 會用到 fetch  
- 因為資料量很大  
- 所以可能要點很多層按鈕, 才去點到資料!  
- 天氣 API  