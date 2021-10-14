# 2-1、 CSS 基礎 1 : CSS selector 
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## CSS (Cascading Style Shets) 階層式樣式表
- 負責網頁樣式，用到頻率比 HTML 來得高。  

__基本款三種樣式__

```
<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
    <style>
         div {
               background:black;
    }
    </style>
  </head>
  <body>
    <div style="background:silver;">
    網頁主要呈現內容。  
    </div>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```

---
1. ``<div style="background:silver;"></div>`` :  常見顏色有支援，不過不是所有顏色支援，而且不好維護。  

2. ``<style></style>`` :  規則為 `selector {attribute: value;}` 可以選到屬性上顏色。   

3. CSS 規則變多了後難維護，而移到另外一個獨立檔案: `<link rel="stylesheet" href="./style.css" />` ， 而 ``./style.css`` 則會連到檔案位置:  
- 連到檔案位置內的寫法: `div {background: gray}` 。 
- HTML 和 CSS 檔案都獨立比較好維護，因此蠻常用這方法。   

---
# 2-2、 CSS 基礎 1 : Selector 我全都要 !
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## CSS Selector - Universal Selectors

__選到所有東西__   

開啟一個檔案 存成 HTML 格式:

```
<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
  <span>span1</span>
  <span>span2</span>
    <div>
    <span>span3 網頁主要呈現內容。</span>
    </div>
    <span>span4</span>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```

接著另外開一個檔案 style.css 格式:
```
* {
      color: red;
}
```

所有文字都會套用這個規則。

---
# 2-3、 CSS 基礎 1 : Selector 上印記 !
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## 如何去選我所要的元素 ?
- 以標籤為名稱，如: div 、 body 

開一個檔案 style.css 格式:
```
div {
      background: orange;
}

body {
      background: yellow;
}
    <!-- 
        註解 :
        去掉星號改成 div 、 body 。  
    -->
```
  [- 如果選 div 就會選到所有 div 的標籤。](https://drive.google.com/file/d/1x9laU2Bkt99xS14nmE-X4Z8SjtYKWWiE/view?usp=sharing)
- 實際開發上可能比較少用，可能選的時候只有某一、二個元素要調整。  

---

# 2-4、 CSS 基礎 1 : Selector 分門別類 !
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## id 與 class
- 較常用的兩個 Selector 。  

存成一個 html 格式的檔案:
```
<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <div id="div1">
          Hi
    </div>
    <div class="bg-yellow text-white">
          Hello
    </div>
   <div>
          是在 Hello ?
    </div>
    <div class="bg-yellow">
          是在 Yellow ?
    </div>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```

說明:  
`<div id="div1">Hi</div>` 整個網頁上只會有一個 id ， id 只能用一個。 
一個元素可以有多個 class ， 而且 class 可以被共享，也能對字體調整顏色:  ``<div class="bg-yellow text-white">Hello</div>`` 。  

---

一樣開一個檔案 style.css 格式:
```
#div1 {
      background: orange;
}

.bg-yellow {
       background: yellow;
}

.text-white {
       color: silver;
}

body {
      background: black;
}
    <!-- 
        註解 :
        無。  
    -->
```    
說明:  
- `#div1 {background: orange;}` 表示 id 的名稱。  

- ``.bg-yellow {background: yellow;}`` 套了 Selector class 後整條背景都套黃色。  

- ``.text-white {color: silver;}``  class 也可以針對字體換顏色。  

---

![](https://i.imgur.com/skRAuI4.png)

---

# 2-5、 CSS 基礎 1 : 如何選同時符合的條件
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

延續 2-4 class ， 如果只要 `div class="bg-yellow"` 有顏色，而 span 不顯色:  
```
  <body>
    <div class="bg-yellow bg-real-yellow">
          Hi
    </div>
    <div class="bg-yellow">
          Hello
    </div>
   <div>
          是在 Hello ?
    </div>
    <span class="bg-yellow">
          是在 Yellow ?
    </span>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>

```

---

則在檔案 style.css 格式中更改:
```
div.bg-yellow {
       background: yellow;
}

.text-white {
       color: silver;
}

body {
      background: black;
}
    <!-- 
        註解 :
        無。  
    -->
```    
說明:  
- 這樣改就只有 Hi 跟 Hello 有顏色。  

![](https://i.imgur.com/7RYnSZI.png)  

- class 可以一直連接，如 `div.bg-yellow.bg-real-yellow {background: yellow;}` ， 這樣就只會顯示 Hi 有顏色。  

![](https://i.imgur.com/f448ZZD.png)  

---

# 2-6、 CSS 基礎 1 : 只要底下的元素
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

先照一層一層排列的順序，有三層:  

<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <div class="Lv1">Lv1
         <div class="bg-red">Lv2
               <div class="bg-red">Lv3</div>
         </div>
    </div>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>

---

則在檔案 style.css 格式中更改:
```
.Lv1 > div {
       background: orange;
}

    <!-- 
        註解 :
        無。  
    -->
```    

說明:
- 會選到除了 Lv1 那層的其他層，並轉換顏色，因為 Lv1 的 div 區塊包了 Lv2 和 Lv3 。  

![](https://i.imgur.com/z3EKvIN.png)

- 如果要選 Lv3 就可以: `.Lv1 > div > div {background: orange;}` 。  
- 同一層和包含在內的 div 都會受這個效果影響。  
- 如果要選 Lv1 底下所有 div : `.Lv1 div {background: orange;}` 。  
- 如果 Lv1 下層沒有指定的標籤就不會被效果影響，例如 Lv1 > .bg-red ， 但 Lv2 沒有 class="bg-red" 標籤。  
- `.Lv1 > .bg-red {background: orange;}` 會除了 Lv1 以外，下層有 class="bg-red" 受影響。  
- `.Lv1  .bg-red {background: orange;}` 中間空白，會除了 Lv1 以外，底下所有 class="bg-red" 受影響。  

![](https://i.imgur.com/epCbePP.png)

---

# 2-7、 CSS 基礎 1 : 選旁邊的元素
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## 旁邊的元素: + 和 ~  
四個 div 都在同一層:  
```
<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <div class="bg-red">div1</div>
    <div>div2</div>
    <div class="bg-red">div3</div>
    <div class="bg-red">div4</div>
    
    <div>123</div>
    <span>456</span>
    <span>333</span>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```
---

則在檔案 style.css 格式中更改:
```
.bg-red + .bg-red {
       background: orange;
}

div + span {
       background: blue;
}

    <!-- 
        註解 :
        無。  
    -->
```    
- ``+`` 在同一層，上下的關係才會有作用， 如果有兩個 span 選不到最後一個 span ， 只會選到一個元素。  

- 用 ``+``  ， 如果標籤只有一個，則會自動找鄰近的有兩個以上的標籤作用。  

- 用 `+` 選 .bg-red 旁邊的 .bg-red ， 會顯示最下層的顏色:  

 ![](https://i.imgur.com/sWmrBDQ.png)  
 
 - 用 `+` 選 div 旁邊的  span ， 會顯示最下層的藍色:  

![](https://i.imgur.com/LPLZGpb.png)  

- 用 `+`  `<span>333</span>` 因為旁邊沒有 div 因此不會被選到。

## `~` 的用法
```
<!DOCTYPE HTML> 

<html>
  <head>
  網頁資訊。
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <div class="bg-red">div1</div>
    <div>div2</div>
    <div class="bg-red">div3</div>
    <div class="bg-red">div4</div>
    
    <div>123</div>
    <span>456</span>
    <span>333</span>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```
---

則在檔案 style.css 格式中更改:
```
.bg-red ~ .bg-red {
       background: orange;
}

div ~ span {
       background: blue;
}

    <!-- 
        註解 :
        無。  
    -->
```    
- "~" 在同一層，上下的關係才會有作用，但是會選到所有同標籤的元素。

- 如果將 `span + div {background: blue;}` 刪掉換成 ， `div ~ span {background: gray;}` 則是 div 右邊所有的 span 都會被上色。   

- 如果將 `.bg-red ~ .bg-red {background: orange;}` 則是 div1 後面所有的 div3 和 div4 都會被上色。  

---

## 如果有個 list ， 要有邊距，就可以用到這個效果:
```
<!DOCTYPE HTML> 

<html>
  <head>
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <span class="bg-red">span1</span>
    <span class="bg-red">span2</span>
    <span class="bg-red">span3</span>
    <span class="bg-red">span4</span>

    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```
---

則在檔案 style.css 格式中更改:

```
.bg-red + .bg-red {
       background: orange;
       margin-left: 20px;
}
    <!-- 
        註解 :
        無。  
    -->
```    

![](https://i.imgur.com/ivyoBSg.png)  

- 這樣就會造成一個清單，邊距有 20 px 。  

- ``.bg-red ~ .bg-red {background: orange;margin-left: 20px;}`` 東西都在一起的話也可以這樣。  

---

# 2-8、 CSS 基礎 1 : 假的 class ?!
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## Pseudo-Classes : hover

滑鼠移上去蓋在字(元素)上面就是 hover 。  

可以用 2-7 的 html 。  
以 style.css 為例:
```
span:hover {
       background: blue;
       margin-left: 20px;
}
```
  
  ![](https://i.imgur.com/LVN6arR.png)
  
  debug 的時候也可以用 dev tool (以 Firefox) :  
  ![](https://i.imgur.com/uhcllUr.png)

- 開啟 horver 和 focus horver within 。  
- 在滑鼠沒有移上去的狀態下就啟用 horver 。  
- 這很常用 ! 。  
  
  ---
  
  參考資料:
  
  https://www.codegrepper.com/code-examples/csharp/pseudoclasses+CSS
  
  https://developer.mozilla.org/zh-TW/docs/Web/CSS/Pseudo-classes
  
---

# 2-9、 CSS 基礎 1 : 選第五元素
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## nth-child 可以幫助選到第幾個元素

__5 個 row 的 html 格式:__  

<!DOCTYPE HTML> 

<html>
  <head>
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
        <div class="wrapper">
                  <div>row1</div>
                  <div>row2</div>
                  <div>row3</div>
                  <div>row4</div>
                  <div>row5</div>
        </div>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>

---
```
.wrapper div:first-child {
       background: orange;
       
}

.wrapper div:nth-child(3) {
       background: orange;
       
}

.wrapper div:last-child {
       background: orange;
       
}
```

- ``.wrapper div:nth-child() {background: orange;}`` nth-child() 括號內可以填 odd 、 even 。  
- ``.wrapper div:nth-child() {background: orange;}`` nth-child() 括號內填 3n ， 就會以 0、3、6、9... 順序找下去 。  
- ``.wrapper div:nth-child() {background: orange;}`` nth-child() 括號內填 3n+1 ， 就會以 1、4、7... 順序找下去 。  

- 如果在 body 內這樣寫:  
```
 <body>
        <div class="wrapper">
                   <div class="bg-red">row1</div>
                  <div>row2</div>
                  <div class="bg-red">row3</div>
                  <div>row4</div>
                  <div>row5</div>
        </div>
```
- 然後用 ``.wrapper .bg-red:nth-child(2) {background: orange;}`` 會發現甚麼也選不到。  
- 他是先以順序 nth-child(2) 第 2 個元素為準，然後再看第 2 個元素是不是 .bg-red ， 因此第2個元素是 row2 。  
- 一般用不會這麼複雜，一般都是連續的標籤和 class 會用到; 使用上是先看順序再看標籤。  

---

---

# 2-10、 CSS 基礎 1 : 偽元素
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  

## pseudo-element 偽元素

- 可選到元素的某些部份。  
- before
- after

---

```
<!DOCTYPE HTML> 

<html>
  <head>
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
        <div class="wrapper">
                  Hello
        </div>
        <div class="price">
                 1000
        </div>
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```

---

以 style.css 為例:
```
.wrapper::before {
        content: "123";
        color: silver;
}

.price::before {
        content: "$";
        color: orange;
}
```

- 看起來很像 html 的元素，但是用 CSS 產生的，會直接產生一個內容 123。  
- 好處是不用在網頁 body 內直接加符號，可以在 CSS 檔案中做更動，甚至加入圖片...等。  
- 例如  ``<div class="price">`` 用了 `::befor` 就會讓 $ 符號在價錢前面的效果。  

![](https://i.imgur.com/bveUw6r.png)  

  - ``<div class="price">`` 用了 `::after` 就會讓 $ 符號有在價錢後面的效果。  

![](https://i.imgur.com/PrufVzY.png)  

- 如果網頁 HTML 元素太多或不必要，就可以用 before(前面) 、  after(後面) 偽元素來取代。  

## content 還能放東西

- content 內一定要有東西，通常都跟 before 、 after 來一起使用。  

---

以 style.css 為例:
```
.price::after {
        content: attr();
        color: orange;
}
```

- attr() 括號內可以放 html 元素， 像是 `<div class="price">` ，CSS 檔案內 `content: attr(class)` ; 就可以把 class 的文字抽出。  

![](https://i.imgur.com/dvynrbM.png)

-  html 內自訂元素或是 attr() ， 會以 `<div class="price" data-id="Yooooooo">` ， CSS 檔案內 `content: attr(data-id)` ; 就可以把 Yooooooo 抽出。  

- 這樣會比用 ``<span class="symbol">NTD</span>`` 包起來，然後內標顏色打一長串來的簡潔。  

---
參考資料:

https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements

---

# 2-11、 CSS 基礎 1 : 一招大招就能搞定的，就不需要一堆小招
###### tags: `FE101` `HTML+CSS` `2020八月第三周` `進度筆記` `Lidemy心得` 08/20  
---

以這個 html 格式為例:
```
<!DOCTYPE HTML> 

<html>
  <head>
    <title>網頁標題</title>
    <meta charset="utf-8" /> 
   <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
        <div class="wrapper">
              <div class="list">
                    <div id="pickme" class="item">
                               pick me
                    </div>
              </div>
        </div>        
    <!-- 
        註解 
        不會顯示在網頁視覺呈現，閱讀程式碼、文字檔才會看到。  
    -->
  </body>
</html>
```

## 可以用 dev tool 看那些規則被蓋掉

- id (只有一個) 的權重 > class (很多個) > 標籤 (數不清個)，越清楚程度的贏，不論有多少個 class 都一樣。  

- CSS 的某些屬性會繼承，例如 color 。  

- 優先順序一樣的話 ， class 會以後面的為準，例如有兩個或是不同的 class ， 然後再 CSS 檔案內這樣寫 `` .item {color: blue;}`` 和 ``.item {color: orange;}`` ， 最後面的 class (橘色) 會蓋掉前一個。  

- CSS 檔案內如果寫 `div.wrapper > div.list > div.item {color:yellow;}` ， 這樣非常的詳細，但還是贏不了 id 。  

- id 如 ， ``#pickme {color: pink;}`` 會蓋掉所有的顏色，不論後來多少 class 寫到。  

## Selector 權重計算方式

按照順序會照位數比，如:  

```
             class
id >   pseudo class   >   element
             attribute
0,             0,                  0

```
                             1, 0, 0                                                                       0, 3, 0                             
- id 如 ， ``#pickme {color: pink;}``  就會比 ``div.wrapper > div.list > div.item {color:yellow;}`` 大。  
- 但都打不贏 inline style (1,0,0,0) ， 如 html 內 `<div id="pickme" class="item" style="color: orange">` ， 權重就 > id 。  
- 最終魔王: !important (1,0,0,0,0) ， 更比 inline style 和 id 猛; 用法是在 CSS 檔案內 `.wrapper {color: red !important;}` 。  
  - 第一順位的 !important 比之後的 ! important 都來得重要且優先。  
  - 而放在 id 內的 !important 又比放在其他地方的 !important 權重都來得重。  
  - 實際開發時會很少用 !important ， 因為會蓋掉一堆規則，也會很少用 inline style 。  

---

參考資料:

[強烈推薦收藏好物 – CSS Specificity (CSS 權重一覽)](http://muki.tw/tech/css-specificity-document/)


[你對 CSS 權重真的足夠了解嗎？](https://juejin.im/post/5afa98bf51882542c832e5ec)
