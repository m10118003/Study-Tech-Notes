# 5-1 、 CSS 基礎 4 : 定位 (Position)
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

__排版時要將元素放到位。__  

---

## Static

- 最基本的網頁預設排版方式，例如 ``display: block;``  。  

  - 跟你說從上排到下這樣。  

![](https://i.imgur.com/OnRQTH4.png)  

- 而 inline 或 inline-block 就會從一行開始畫，由左排到右。  

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

---

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

---
參考資料:

[關於position 屬性 - CSS](https://zh-tw.learnlayout.com/position.html)  

[CSS relative? absolute? 傻傻分不清楚 - iT 邦幫忙::一起幫忙 ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiI58zhhs7rAhU5yYsBHaVxCbsQFjABegQIBRAB&url=https%3A%2F%2Fithelp.ithome.com.tw%2Farticles%2F10212202&usg=AOvVaw2xTg7j6nC8--E94ngcdqYI)  

[MDN - position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)  

---

# 5-2 、 CSS 基礎 4 : 定位相關 z-index
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

## z-index

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
      <div class="box">Box4</div>
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
    width: 300px;
    height: 100px;
    margin: 10px;
    display: block;
    position: relative;
}

.wrapper div:nth-child(2) {
    background: red;
	top: 40px;
	z-index: 1;
}
```

- z-index 可以決定元素是否蓋過另外一個元素，數字越大越前面。  

- 如上面就會以 Box2 蓋掉 Box3 ， z-index 的值只要 > 1 就會有作用。  

- 反之也可以被蓋掉，將值調成負值。  

---

# 5-3 、 CSS 基礎 4 : 定位新成員 Sticky
###### tags: `FE101` `HTML+CSS` `2020八月第四周` `進度筆記` `Lidemy心得` 08/26
---

## `position: sticky`

- 比較新，有些舊瀏覽器不支援。  

以 5-2 的 .html 檔案，如套用 CSS 格式:  
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
    position: relative;
}

.wrapper div:nth-child(2) {
    background: red;
	top: 0px;
	position: sticky;
	z-index: 2;
}
```

- 當 Box2 這個元素還沒達到 `top: 0px ;` 的時候就跟一般 static 排版一樣。  

![](https://i.imgur.com/6hSm9yP.png)  

- 但滾動的時候 ， Box2 這個元素達到 `top: 0px;` 就會固定在 top 。  

![](https://i.imgur.com/D6UdNEP.png)  


- 手機瀏覽常見到。

---

# 5-4 、 CSS 基礎 4 : 變形金剛
###### tags: `FE101` `HTML+CSS` `2020九月第一周` `進度筆記` `Lidemy心得` 09/02
---

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
      <div id="Box1">Box1</div>
	</body>  
</html>
```

## Transform

套用 CSS 格式:
```
#Box1 {
  width: 200px;
  height: 100px;
  border-radius: 30px;
  text-align: center;
  line-height: 100px;
  color: white;
  background: orange;
  transition: all 0.5s;
  margin: 100px;
}

#Box1:hover {
  transform: scale(2);
}
```
- `transform: scale(2)` 會以中心為基準擴大 2 倍。  
- 其他還有 rotate(度數) 、 translate(移動多少 px) ...等，可以搭配 transition 使用。  
- 不會影響到其他元素，僅影響自身元素。  

## Transform 置中
```
#Box1 {
  position: fixed;
  width: 200px;
  height: 100px;
  border-radius: 30px;
  text-align: center;
  line-height: 100px;
  color: white;
  background: orange;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

圖形就置中了。  
![](https://i.imgur.com/QuEQmQF.png)  

---
參考資料:

[transform - MDN Web Docs - Mozilla](https://developer.mozilla.org/zh-TW/docs/Web/CSS/transform)


