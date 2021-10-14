# 4-1 、 CSS 基礎 3 : Box Model
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

## 甚麼是盒模型 ?

HTML 的每個元素都可以看作是盒子，用 CSS 樣式來調整盒子。  

- 但要注意 padding 和 border 會往外擴張，增加 pixel ， 會影響到其他元素。  

- 例如一個 ``width: 200px;`` 和 ``height: 100px;`` 的 box 加了 ``border: 5px solid black;`` 就會變成 width 210px 和 height 110 px 。  

- 很多時候要固定寬高，而不是往外增長，所以會調整 box-sizing 。  

## box-sizing
- ``box-sizing: content-box;`` 像是本身 content 的寬高維持不變，不考慮內邊距（padding）和邊框（border）。  

- ``box-sizing: border-box;`` 像是本身 content 的會加上內邊距（padding）和邊框（border）來維持所要的寬和高的 pixel 。  

- 如 ``width: 200 px;`` 和 ``height: 100px`` ， 使用 ``box-sizing: border-box;``  會將 content 的寬和高降成 170px 和 70px 。  
![](https://i.imgur.com/CSHWgxR.png)  

---
參考資料:

[MDN - The box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)  

[box-sizing - MDN Web Docs - Mozilla](https://developer.mozilla.org/zh-TW/docs/Web/CSS/box-sizing)  

---

# 4-2 、 CSS 基礎 3 : 顯示三元素 - 三位一體
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

## display block element

- 預設就是 div 、 h1 、 p 標籤，寬高、內邊距 (padding) 和邊框 (margin) 怎麼調整皆可。  

- 通常自己佔滿一整行，佔好占滿，不會將下行的 div 往上遞補。  

- ``display: block;`` 一行放一個元素。  

## display inline element

- 如: span 、 a 標籤，怎麼調整寬高都沒用，寬高都會根據內容來顯示。  
 
- 但調整外邊距 (margin) 則會影響左右的外邊距，但上下外邊距不影響。  
  - 外邊距調高，會造成像是跟其他元素的間距越來越大。
![](https://i.imgur.com/UO1TTfm.png)  

- 要注意的是，調整內邊距 (padding) 左右也會讓其他元素的間距變大。  
  - 但調整內邊距 (padding) 上下則是不會影響其他元素位置的變動。  
  - 但元素(背景 background 和邊框 border )高度會拉伸。  

## display inline-block element
- 把 inline 和 block 的優點結合起來，如: button 、 input 和 select...。  
  - 對外像 inline 可併排。  
  - 對內像 block 可調整各屬性。  

- ``display: inline-block;`` 讓元素併排。  
---
