# 6-1、 Zeplin 介紹
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

- week6 ~ 8 hw 會用到，因為設計稿要用到。  
- [Zeppelin](https://zeppelin.apache.org/) 是設計師與工程師溝通橋梁，變成工程師看得懂的，不用再看 Photoshop CS 。  
- 設計師設計好後 .psd 或是 illustrator 檔案，傳上去後會轉格式，工程師可以照著來切版。  
- 可以直接看懂色碼，寬高可能是寫死的 (自動排) ， 需要參考字體大小、顏色和字型，還能直接複製 content 。  
- 這設計稿比照實際工作用，也可以將設計稿圖片載好後上 [TinyPNG](https://tinypng.com/) 或 [TinyJPG](https://tinyjpg.com/) 將圖片壓縮。  
- 有時候要字型想像一下，如果出手機版就要自行想像一下。  

# 6-2、 HTML + CSS 介紹
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---
1. What this ?
2. Why learning ?
3. Where used ?

---

- HTML 標籤有語意且是骨幹，裝飾是 CSS ， 然後切版。
```
<html>
<head>
           <style>.subtitle {
                                   color: #4f6eb0;
                              }
                              
                              div {
                                   front-size: 40px;
                                   front-weight: bold;
                              }
           
           </style>
</head>
<body>
<div><h1>HTML + CSS</h1></div>
      <h2 class="subtitle">h2</h2>
      <h2>不難但也不簡單</h2>
      <p>新手教學</p>
</body>
</html>
```
- 也可以用 dev tool 暫時除錯、模仿。  
- 如果用 div 當標題， 這樣機器不知道這個是標題(也沒有 title) ， 對 SEO (Search Engine Optimization) 不友善，如果用 h1 標籤(有語意)就好很多。  
- [無障礙 (accessibility)](https://developer.mozilla.org/zh-TW/docs/Learn/Accessibility/What_is_accessibility) 且有語意的標籤對 SEO 也很有幫助。  
- CSS 選元素、基本屬性熟練...等，然後切版是最重要的。  
-  [CSS Diner](https://flukeout.github.io/) 玩到中期，不一定要全破。  
-  [Flexbox Froggy](http://flexboxfroggy.com/) 和 [Flex Pirate - 擊倒海盜，獲得網頁排版寶藏](https://hexschool.github.io/flexbox-pirate/index.html) ， 學習排版後然後怎麼應用在切版。  
-  如果不知道怎麼排，可以先宣告幾個 div 和 class 給他寬高跟底色，然後試試看各種屬性:  
```
<head>
<style>
     .A {
           background: red;
           width: 200px;
           height: 200px;
     }
     .B {
           background: blue;
           width: 150px;
           height: 150px;
     }
</style>
</head>
<body>
             <div class="A">A</div>
             <div class="B">B</div>
</body>
```
- RWD (Responsive Web Design) 對不同螢幕寬度套用不同 CSS 。  

---

# 6-3、 作業介紹
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

- hw1 
  - 主線 A: 跟著影片教學做切版，但不會全部做完，看切版的時候影片就停一下一塊一塊切，然後拼起來。  
  - 主線 B: 自己實作並加上網友評論區塊。  

1. 分成幾個區塊 ， Header 、 Navigation Bar 、 Body 、 評論和 Footer...等區塊。  
2. 找樣板: html boilerplate ， 複製 code 成樣板。  
3. `<!DOCTYPE HTML>` 大寫 ， lang 轉換 或是刪掉 ``<html lang="UTF-8">`` 。  
4. meta rwd 參考網站: [\[筆記\] 基本RWD版型設計 - PJCHENder - blogger](https://pjchender.blogspot.com/2015/05/rwd.html)  。  
5. 抓好版型:  
```
<!DOCTYPE HTML>

<html lang="UTF-8">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>中西合併餐廳官網</title>
  <style>
  
  </style>

</head>

<body>
  
</body>
</html>
```
6. 開始切版之前先安裝 [Normalize.css: Make browsers render all elements more ...](https://necolas.github.io/normalize.css/)  
- 標籤、樣式和 Body 等等幫你初始化。  
- 可以參考 [\[CSS\] 跨瀏覽器的樣式重置reset.css & normalize.css | by ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwi4t56a3NXrAhUlK6YKHSpqAlwQFjACegQIAxAB&url=https%3A%2F%2Fmedium.com%2F%40realdennis%2Fcss-%25E8%25B7%25A8%25E7%2580%258F%25E8%25A6%25BD%25E5%2599%25A8%25E7%259A%2584%25E6%25A8%25A3%25E5%25BC%258F%25E9%2587%258D%25E7%25BD%25AE-reset-css-normalize-css-40dfe53c0be9&usg=AOvVaw293yk_iPSrKw8GRQInTQBM)  

7. `transform: translate(-50%, -50%);` 將自己中心往左和往上移。  

---------------------------------------------------------------------

# - hw2 自己根據設計稿做，從零開始。  
```
<!DOCTYPE html>

<html>
<head>
  <meta charset="utf-8">

  <title>表單</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://necolas.github.io/normalize.css/8.0.1/normalize.css" />

  <style>
      body {
        background: rgba(0, 0, 0, 0.3);
      }

      .wrapper {
        max-width: 645px;
        background: white;
        margin: 10% auto;
        box-shadow: 1.8px 2.4px 5px 0 rgba(0, 0, 0, 0.3);
        border-top: solid 8px #fad312;
        padding: 64px 32px;
      }

      .apply-form__title {
        margin: 0;
        font-size: 36px;
        font-weight: bold;
      }

      .apply-form__desc {
        margin-top: 32px;
        font-size: 14px;
        line-height: 1.5em;
      }

      .apply-form__notice {
        color: #e74149;
        font-size: 16px;
        margin-top: 20px;
      }

      .input-block {
        margin-top: 55px;
      }

      .input-block__title {
        font-size: 20px;
      }

      .input-block__desc {
        font-size: 14px;
        margin-top: 8px;
      }

      .input-block__input {
        margin-top: 20px;
      }

      .input-block__input input[type=text] {
        border: solid 1px #d0d0d0;
        font-size: 16px;
        padding: 8px;
      }

      .input-block__input label {
        display: block;
        margin-top: 12px;
      }

      .required:after {
        content: '*';
        color: #e74149;
      }

      .apply-form__submit {
        background: #fad312;
        color: black;
        font-size: 15px;
        padding: 12px 32px;
        margin-top: 48px;
        border: none;
        border-radius: 4px;
      }

      footer {
        background: black;
        color: #999999;
        font-size: 13px;
        text-align: center;
        padding: 24px 12px;
      }

  </style>
</head>

<body>
  <div class="wrapper">
    <form class="apply-form">
      <h1 class="apply-form__title">新拖延運動報名表單</h1>
      <p class="apply-form__desc">
        活動日期：2020/12/10 ~ 2020/12/11<br>
        活動地點：台北市大安區新生南路二段1號
      </p>
      <p class="apply-form__notice">
        * 必填
      </p>
      <div class="input-block">
        <div class="input-block__title required">
          暱稱
        </div>
        <div class="input-block__input">
          <input name="nickname" type="text" />
        </div>
      </div>
      <div class="input-block">
        <div class="input-block__title required">
          電子郵件
        </div>
        <div class="input-block__input">
          <input name="email" type="text" />
        </div>
      </div>
      <div class="input-block">
        <div class="input-block__title required">
          手機號碼
        </div>
        <div class="input-block__input">
          <input name="phone" type="text" />
        </div>
      </div>
      <div class="input-block">
        <div class="input-block__title required">
          報名類型
        </div>
        <div class="input-block__input">
          <label>
            <input name="type" value="1" type="radio" /> 躺在床上用想像力實作
          </label>

          <label>
            <input name="type" value="2" type="radio" />
             趴在地上滑手機找現成的
          </label>
        </div>
      </div>
      <div class="input-block">
        <div class="input-block__title required">
          怎麼知道這個活動的？
        </div>
        <div class="input-block__input">
          <input name="referal" type="text" />
        </div>
      </div>
      <div class="input-block">
        <div class="input-block__title">
          其他
        </div>
        <div class="input-block__desc">
          對活動的一些建議
        </div>
        <div class="input-block__input">
          <input name="nickname" type="text" />
        </div>
      </div>
      <input class="apply-form__submit" type="submit" />
      <p class="apply-form__desc">
        請勿透過表單送出您的密碼。
      </p>
    </form>
  </div>
  <footer>© 2020 © Copyright. All rights Reserved.</footer>
  
</body>
</html>
```

-----------------------------------------------------

```
<!--  
這邊開始是自己刻的板。  
看了老師刻的跟自己切的差好多XD  

<!DOCTYPE HTML>

<html lang="UTF-8">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>新拖延運動報名表單</title>
  <style>

  	title {
			width: 305px;
			height: 32px;
			font-family: MicrosoftJhengHei;
			font-size: 36px;
			font-weight: bold;
			font-stretch: normal;
			font-style: normal;
			line-height: normal;
			letter-spacing: -1.8px;
			color: #000000;
  	}

  	body {
  		width: 645px;
  		height: 1085px;
  		box-shadow: 1.8px 2.4px 5px 0 rgba(0, 0, 0, 0.3);
  		background-color: var(--white);
  	}

  	.title {
		  font-family: MicrosoftJhengHei;
		  font-size: 36px;
		  font-weight: bold;
		  letter-spacing: -1.8px;
		  color: #000000;
		}

		.activity {
			font-family: MicrosoftJhengHei;
 		  font-size: 14px;
 		  color: #000000;
		}

		.must_fill {
			font-family: MicrosoftJhengHei;
			font-size: 16px;
			color: #e74149;
		}

		.name ::after {
      content: " *";
      font-family: MicrosoftJhengHei;
  		font-size: 20px;
  		font-weight: normal;
  		font-stretch: normal;
  		font-style: normal;
  		line-height: normal;
  		letter-spacing: normal;
  		color: #e74149;
    }

    .nickname {
		  font-family: MicrosoftJhengHei;
 		  font-size: 20px;
		  color: #000000;
    }

    input {
    	cursor:pointer;    	
    	width: 287px;
    	height: 23px;
    	border: solid 1px
    	display: inline-block;     	 
    }

    #box {
      width: 12px;
      height: 12px;
      border: solid 1px #d0d0d0;
      background-color: #bababa;
    }

    .radio {
    	font-family: MicrosoftJhengHei;
    	font-size: 14px;    	
    	color: #000000;    	
    }

    .placeholder {
    	font-family: MicrosoftJhengHei;
    	font-size: 16px;    	
    	color: #afafaf;
    }

    span input {
    	font-family: MicrosoftJhengHei;
    	text-align: center;
    	font-size: 15px;
    	width: 92px;
    	height: 40px;
    	border-radius: 3px;
    	background-color: #fad312;    	
    }

    p {
    	width: 177px;    	
    	font-family: MicrosoftJhengHei;
    	font-size: 14px;    	
    	color: #000000;

    }

  </style>

</head>

<body>
  <section class="title">
    <div><h1>新拖延運動報名表單</h1></div>
  </section>

  <section class="activity">
    <div><h2>活動日期：2020/12/10 ~ 2020/12/11</h2></div>
    <div><h2>活動地點：台北市大安區新生南路二段１號</h2></div>
  </section>
  <section class="must_fill">
    <div><h2>* 必填</h2></div>
  </section>
    <div class="name">
      <h3 class="nickname">暱稱</h3>    	
        <input type="text" placeholder="您的回答" />         
    </div>
    <br> 
    <div class="name">
      <h3 class="nickname">電子郵件</h3>    	
        <input type="email" placeholder="您的電子郵件" />         
    </div>
    <br> 
    <div class="name">
      <h3 class="nickname">手機號碼</h3>    	
        <input type="tel" placeholder="您的手機號碼" />         
    </div>
    <br>
    <div class="name">
      <h3 class="nickname">報名類型</h3> 
    </div>
  	<div>       	
      <input type="radio" id="box" name="radio" /><label for="radio">躺在床上用想像力實作</label><br>
   		<input type="radio" id="box" name="radio" /><label for="radio">趴在地上滑手機找現成的</label>         
  	</div>
    <br> 
    <div class="name">
      <h3 class="nickname">怎麼知道這個活動的</h3>    	
        <input type="text" placeholder="您的回答" />         
    </div>
    <br> 
    <div class="name">
      <h3 class="nickname">其他</h3>對活動的一些建議
         <br><br>       	
        <input type="text" placeholder="您的回答" />         
    </div>
    <br>	
     <span>
       <input type="submit" value="送出表單" />
       <br>
       <br>
       <div> 請勿透過表單送出您的密碼。 </div>
     </span>

</body>
</html>

-->

```

參考資料:

[淺談BEM CSS-CSS設計模式與架構 - iT 邦幫忙::一起幫忙解決 ...](https://ithelp.ithome.com.tw/articles/10204003)  

[BEM，CSS 設計模式~ 竹白記事本](https://chupainotebook.blogspot.com/2019/05/bemcss.html)  

[前端領域的BEM到底是什麼| 程式前沿](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwin5aTK5fHrAhUKGqYKHVV5DwEQFjAQegQICBAB&url=https%3A%2F%2Fcodertw.com%2Funcategorized%2F178852%2F&usg=AOvVaw1me_H4ThApkebFS4y-FFp0)  

---------------------------------------------------------------------

# - hw3 簡答。  

# 1. 請找出三個課程裡面沒提到的 HTML 標籤並一一說明作用。  
- 粗體字: `<b>文字</b>` 文字格式即文字，能標示粗體字。  

- `<bgsound />` ;  	src：音樂檔路徑 ; loop：重播次數 ; infinite : 重複播放，例如 : `<bgsound src="./music.mp3" loop="5" />` 表示目錄下的音樂檔案，撥放次數五次循環。  

- 文字區域: `<textarea></textarea>` ; name : 名稱(可重複) ， id : 名稱(不可重複) ; cols : 行數 ; rows : 列數，例如 : `<textarea name="text" cols="30" rows="5"></textarea>` 這是一個有著 30 行和 5 列的文字區域方塊，可拉伸。  

參考資料: [HTML標籤列表](http://web.thu.edu.tw/hzed/www/tag.htm)  

---------------------------------------------------------------------

# 2. 請問什麼是盒模型（box modal）？  

## 甚麼是盒模型 ?

HTML 的每個元素都可以看作是盒子，用 CSS 樣式來調整盒子。  

- 但要注意 padding 和 border 會往外擴張，增加 pixel ， 會影響到其他元素。  

- 例如一個 ``width: 200px;`` 和 ``height: 100px;`` 的 box 加了 ``border: 5px solid black;`` 就會變成 width 210px 和 height 110 px 。  

- 很多時候要固定寬高，而不是往外增長，所以會調整 box-sizing 。  

---------------------------------------------------------------------

## box-sizing
- ``box-sizing: content-box;`` 像是本身 content 的寬高維持不變，不考慮內邊距（padding）和邊框（border）。  

- ``box-sizing: border-box;`` 像是本身 content 的會加上內邊距（padding）和邊框（border）來維持所要的寬和高的 pixel 。  

- 如 ``width: 200 px;`` 和 ``height: 100px`` ， 使用 ``box-sizing: border-box;``  會將 content 的寬和高降成 170px 和 70px 。  
![](https://i.imgur.com/CSHWgxR.png)  

---------------------------------------------------------------------  
參考資料:  

[MDN - The box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)  

[box-sizing - MDN Web Docs - Mozilla](https://developer.mozilla.org/zh-TW/docs/Web/CSS/box-sizing)  

--------------------------------------------------------------------- 

# 3. 請問 display: inline, block 跟 inline-block 的差別是什麼？什麼時機點會用到？  

## display block element  

- 預設就是 div 、 h1 、 p 標籤，寬高、內邊距 (padding) 和邊框 (margin) 怎麼調整皆可。  

- 通常自己佔滿一整行，佔好占滿，不會將下行的 div 往上遞補。  

- ``display: block;`` 一行放一個元素。  

---------------------------------------------------------------------

## display inline element  

- 如: span 、 a 標籤，怎麼調整寬高都沒用，寬高都會根據內容來顯示。  
 
- 但調整外邊距 (margin) 則會影響左右的外邊距，但上下外邊距不影響。  
  - 外邊距調高，會造成像是跟其他元素的間距越來越大。
![](https://i.imgur.com/UO1TTfm.png)  

- 要注意的是，調整內邊距 (padding) 左右也會讓其他元素的間距變大。  
  - 但調整內邊距 (padding) 上下則是不會影響其他元素位置的變動。  
  - 但元素(背景 background 和邊框 border )高度會拉伸。  

---------------------------------------------------------------------

## display inline-block element  
- 把 inline 和 block 的優點結合起來，如: button 、 input 和 select...。  
  - 對外像 inline 可併排。  
  - 對內像 block 可調整各屬性。  

- ``display: inline-block;`` 讓元素併排。  

---------------------------------------------------------------------

# 4. 請問 position: static, relative, absolute 跟 fixed 的差別是什麼？分別各舉一個會用到的場合  

## Static  
__排版時要將元素放到位。__ 
- 最基本的網頁預設排版方式，例如 ``display: block;``  。  

  - 跟你說從上排到下這樣。  

![](https://i.imgur.com/OnRQTH4.png)  

- 而 inline 或 inline-block 就會從一行開始畫，由左排到右。  

---------------------------------------------------------------------

## Relative

- 相對定位，會改變自己的位置，而不會影響到其他元素。  

套用 .html 格式:  
```
<!DOCTYPE HTML>

<html>
　<head>  
    <meta charset="utf-8" />  
　　<title>網頁製作教學</title>  
　　<link rel="stylesheet" href="./style.css" />
　</head>  
　<body>  
　　body 間: 為主要語意所在，網頁主要顯示的部分。
    <div class="wrapper">     
      <div class="box">Box1</div>
	  <div class="box">Box2</div>
      <div class="box">Box3</div>
	</div>
　</body>  
</html>
```



如套用 CSS 格式:  
```
body {
    margin: 0;
}

.box {
    background: orange;
    width: 100px;
    height: 100px;
    margin: 10px;
}

.wrapper div:nth-child(2) {
    position: relative;
    top: 20px;
}
```

- 就會造成 Box2 往下移動，其設定的方向皆為反向移動。  

---------------------------------------------------------------------

## fixed 固定住

__相對於瀏覽器的窗口作定位，不管怎麼滾動都在同位置。__  

如套用 CSS 格式:  
```
body {
    margin: 0;
}

.box {
    background: orange;
    width: 300px;
    height: 100px;
    margin: 10px;
    display: block;
}

.wrapper div:first-child{
    position: fixed;
    width: 100px;
    background: red;
    bottom: 100px;
    right: 0px;
}
```
- viewport 根據你看得到的地方定位。  
- 所以 Box1 會被固定在你看到的右下角位置。  

---------------------------------------------------------------------

## absolute 絕對定位

__需要有參考點__  

存 .html 格式檔案:  
```
<!DOCTYPE HTML>

<html>
　<head>  
    <meta charset="utf-8" />  
　　<title>網頁製作教學</title>  
　　<link rel="stylesheet" href="./style.css" />
　</head>  
　<body>  
　　body 間: 為主要語意所在，網頁主要顯示的部分。     
    <div class="box">Box1</div>
	<div class="box">
      <div class="box-inner">
         Box2
      </div>
      <div>
         123
      </div>
    </div>
    <div class="box">Box3</div>
　</body>  
</html>
```
如套用 CSS 格式:  
```
body {
    margin: 0;
}

.box {
    background: orange;
    width: 300px;
    height: 100px;
    margin: 10px;
    display: block;
    position: relative
}

.box-inner {
    position: absolute;
	top: 10px;
    right: 10px;
}
```

- Box2 的字會對參考點定位在 body ``top: 10px; right: 10px;`` 處。  

- 因此要限制字體在 Box 內，所以需要用 `position: relative;` 。  

![](https://i.imgur.com/gYV888u.png)  

- 參考點必須用 box-inner 往上找不是 static 的地方作絕對定位。  

-  因此通常會基於不是 static 的地方，如 `<div class="box">` 作相對定位 `position: relative;` 。  

- 用了絕對定位後，第二個元素會往上遞補到第一個元素，假裝第一個元素不存在。  

- 會脫離原本的正常排版流程。  

---------------------------------------------------------------------  
參考資料:  

[關於position 屬性 - CSS](https://zh-tw.learnlayout.com/position.html)  

[CSS relative? absolute? 傻傻分不清楚 - iT 邦幫忙::一起幫忙 ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiI58zhhs7rAhU5yYsBHaVxCbsQFjABegQIBRAB&url=https%3A%2F%2Fithelp.ithome.com.tw%2Farticles%2F10212202&usg=AOvVaw2xTg7j6nC8--E94ngcdqYI)  

[MDN - position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)  

---------------------------------------------------------------------

- 挑戰題。  

---