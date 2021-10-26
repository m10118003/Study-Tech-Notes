# 2021-10-22 Bootstrap - Microsoft homepage   
###### tags: `Bootstrap` `JS` `2021/10/22` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 早上的部分 - 微軟的仿切  

# 分析版面  

- 先分析頁面  
> 先訂區塊
> 導覽列  
> > 導覽列下有 Container    


> Section  
> footer  
>  ![](https://i.imgur.com/6k76C4T.png)   

> ![](https://i.imgur.com/c6bCYFe.png)   

----

# 幫 Nav 上樣式  

> ![](https://i.imgur.com/yD9cGCy.png)  
> 剛好是 54px  

## 取代 Nav bar 的 logo  
> ![](https://i.imgur.com/uenndlp.png)  

- 給他一個 class  
```
看起來是 137 * 54
實際上 render 是 108 * 23 
```
> 複製貼上的東西要調整縮排  

> ==記得一個網頁沒有兩個 nav 互相包起來==  
> 記得格式要跟 Bootstrap 一樣才有樣式  
> 盡量重現環境  

---

## 幫他上一個 container  
- 不過這個 container 的寬是 1140  
- 微軟的實際上沒這麼擠  

- 在中間的導覽列中塞六個 li (含 a 標籤)  
> ![](https://i.imgur.com/cNpbwpl.png)   
> ![](https://i.imgur.com/3B8uxTO.png)   

# 接著用文字顏色  

- 調整預設文字顏色  
> 找 Bootstrap 的顏色  

----

# 如果文字引入  

-![](https://i.imgur.com/YonuAId.png)   
> ![](https://i.imgur.com/gF390gu.png)   
> 如果是 css 自己寫的, 記得把引入的 css  放到最下面
> ![](https://i.imgur.com/CrqRWnV.png)  
> 程式是一行一行讀的, 後面的會蓋過前面的  

---

# 修改 bootstrap 的時候要注意格式  
![](https://i.imgur.com/a4Zr5go.png)  
> 記得不要動到結構  
> 他結構不只是單純 CSS, 還有混入 JS 
> ![](https://i.imgur.com/Gozo1Kq.png)   
> 修改的時候要先知道修改哪個區域  

- 如果要給個 menu
> 可以在 class 後面再多一個 menu  
> ![](https://i.imgur.com/gK2NaeD.png)  

- 如果綁手綁腳的話就盡量不要用 bootstrap 

> 可以先上 Bootstrap 格式, 再上一個東西, 圖片, 文字  

---

# 可以試著做出微軟的變版  

---

# 微軟的卡片  

![](https://i.imgur.com/jY5Qo2R.png)  

- 4 排的時候是
```
col-3  col-3  col-3 
```
- 2 排的時候是  
```
col-6 col-6 col-6
```
- 之類的   



> ![](https://i.imgur.com/reyCWe6.png)  
> ![](https://i.imgur.com/WFq2256.png)  
> 這樣會一整排  

- 可以改成  
> ![](https://i.imgur.com/xwE7tOS.png)  

> ![](https://i.imgur.com/8lpzZoL.png)  
> 改排數編號  
> ![](https://i.imgur.com/4jJ7w0N.png)   
> ![](https://i.imgur.com/fr4ZFPP.png)  
> 給了一個 border  
> 然後再調整轉換的時機點  



> ![](https://i.imgur.com/8WGcEAd.png)  
> 可以到小於 sm 之前才變版  

- 加個 margin btn   
> ![](https://i.imgur.com/tGojezr.png)  
> ![](https://i.imgur.com/dYuGvyP.png)   
> 調整 margin  

> ![](https://i.imgur.com/xtYFERj.png)  
> margin-1 會超過大小  


- 每個方塊都有空隙就爆了, 要怎辦?  
> 在 col 裡面再放一個方塊  
> ![](https://i.imgur.com/0oWrxzP.png)   

- card 在給個顏色   
> ![](https://i.imgur.com/9AS7vBb.png)  
> 再給個高度  
> ![](https://i.imgur.com/ZGWPLTH.png)   

- 記得先用 bootstrap 的 card  
> 再把它用得跟微軟的一樣  

---

# 記得寫註解 - 這是好文明  
![](https://i.imgur.com/JJ0UIhU.png)  

- 丟微軟分頁的 icon  
> ![](https://i.imgur.com/FLP5EH5.png)  
> 也可以讓分頁自動抓  

- font awesome   
> font size 可以改變大小  
> 也可以上網找別人用好的 CDN  
> ![](https://i.imgur.com/3qDWKoB.png)  

# 有個網站有統整常用套件, CDN   

----

# Bootstrap 本身也有 icon   

- 記得先看 liscene!  
> 看他的使用規範  
> ![](https://i.imgur.com/CVaiC5d.png)  
```
Free, any way you use, open source 都是很重要的關鍵字XD  
可以包起來, 然後__業使用
```

> ![](https://i.imgur.com/gaMjOgw.png)  
> 也可以引入 CDN  
> ![](https://i.imgur.com/olpof8s.png)  

---

# 記得也有 Carousel 可以使用!  

![](https://i.imgur.com/3rPp3DA.png)  
> 淡入淡出, delay 都有~

----

# 中間三個小卡片

> ![](https://i.imgur.com/sAD224t.png)  
> ![](https://i.imgur.com/3ZLXmd2.png)  

![](https://i.imgur.com/Wh3DttN.png)  

---

# Margin 要記得調整  
> ![](https://i.imgur.com/PqAlq3g.png)  

---

# SVG 丟到 NAV 上  

- SVG 本身也是 tag !  
> ![](https://i.imgur.com/UZ2gut3.png)  
> 可以把他丟到 HTML 架構中  
> 本身需要佔有體積位置的話可以這樣丟  


- 或是  新增一個 svg 檔案  
> ![](https://i.imgur.com/WMGnxeT.png)  
> 把 svg 丟進去  
> 要怎麼下指令也會比較好下  
> ![](https://i.imgur.com/rRiPL2i.png)  

---

# 下午的部分  


# 預告課後任務  
- 切出這三個頁面  
- 主頁(首頁)  
> ![](https://i.imgur.com/LgE9GQ9.png)  
> 東西很多   
- 登入頁面  
> ![](https://i.imgur.com/EgEA0b6.png)   
- 購物車   
> ![](https://i.imgur.com/KNkqsZp.png)  

- 要有 RWD   

----

# 文字顏色的權重  

- 要找出權重的指令  
> ![](https://i.imgur.com/z39E2YN.png)  
> 再去蓋過  

---

# 調整位置  

![](https://i.imgur.com/xMTAyjs.png)   

---

# 做出 右側 nav   

> ![](https://i.imgur.com/lmoP0qF.png)   

---

# 做下拉選單   

- Via data attributes   
> 構成這個下拉選單, 有些東西是不能改的   
```
例如: dropdown-menu  
這東西一定要有
他是用 JS 去寫 data-toggle 去觸發的, 同層 class attribute 可以觸發  
他會去父層找最接近的 dropsown
```

- Via JS  
```
客製化的部分是用 JS 去寫的  
```

- 找 dropdown-menu  
> ![](https://i.imgur.com/PL0tLWH.png)   
> 1025px x 660px    

- 上個樣式   
> ![](https://i.imgur.com/IFBU9XF.png)  
> 看他現在是用甚麼方式在定位  
> ![Uploading file..._xp9t9ra5j]()   
```
記得看他剩下來的長度
再用 position 的 right 去推  
```

> 然後 dropper 下拉選單的部分再自己上樣式  
> ![](https://i.imgur.com/wNIMptM.png)   
  
- 放上 ul li 的時候要多注意   
> ![](https://i.imgur.com/cZ9oFBf.png)  
> 樣式會不一樣   

- 更改下拉按鈕的樣式  
> ![](https://i.imgur.com/YoOP06R.png)  
> 要下在 ::after   
> ![](https://i.imgur.com/Z8cMsLO.png)   
```
before & after 
如果不要有樣式, 可以 
content:"unset" 或是 "none"
```
> ![](https://i.imgur.com/DuLq2Jp.png)   

---


# icon 的部分用 img 塞入  

---

# Carousel 的部分就直接塞  

> ![](https://i.imgur.com/Q2bW6fh.png)   

# Carousel 的文字區塊  

> ![](https://i.imgur.com/BMo3SST.png)  

> 文字區塊剛好有 relative 就可以直接對齊  
> ![](https://i.imgur.com/hBAkhBW.png)   
> ![](https://i.imgur.com/jP4RtEl.png)   

```
輪播圖片的置中
#banner-1   .carousel-inner \> .carousel-item \> img {

  margin: auto;

}
```

----

# 中間三張卡片的作法  
- ![](https://i.imgur.com/pCsmWVF.png)   
> 或者是不用 col 用 card  
> ![](https://i.imgur.com/b3NwNv4.png)   

> ![](https://i.imgur.com/4UwIewn.png)   

- 置中的方法  
> ![](https://i.imgur.com/PfhKUfx.png)   
> 把 border 拿掉, 看起來就有空格了  
> ![](https://i.imgur.com/BbdtS3S.png)   

- 上了圖片後  
>![](https://i.imgur.com/btpuyC0.png)  
>記得看有沒有大小  

> ![](https://i.imgur.com/uRWi0ry.png)  
> 複寫他  
> 記得下 display flex  
> ![](https://i.imgur.com/PJFY6gc.png)   
> ![](https://i.imgur.com/nU6ZQZ6.png)
> ![](https://i.imgur.com/z1pNqIH.png)

- 給他 padding  
> 除了在 CSS 也可以在 HTML 直接下  
> ![](https://i.imgur.com/6WcRYeR.png)   
> ![](https://i.imgur.com/cKmNxRY.png)  

- 給他 RWD 變版  
> ![](https://i.imgur.com/FIyEVwp.png)   

---

# card 欄位的作法  

> ![](https://i.imgur.com/Ux2nMT4.png)   


> ![](https://i.imgur.com/j2TUoVk.png)

> ![](https://i.imgur.com/qtPWD6B.png)

> ![](https://i.imgur.com/rnOraQA.png)   

> ![](https://i.imgur.com/wHgn4fU.png)   

- Bootstrap 甚麼都沒寫(lg, sm 沒寫的時候)  
> 是用 min-height 來判斷  
> ![](https://i.imgur.com/q0s8B4L.jpg)  


---

# Footer 的作法  

- 先做外面的框框 row  
> col, 總寬度是 12的情況下就會變排
> md4 的情況下 2 2  排  
> sm 12 的時候 會 1 個 1 個排  
![](https://i.imgur.com/U6uD0u1.png)  

![](https://i.imgur.com/6K8VBVN.png)   

![](https://i.imgur.com/If8DEQH.png)  


- 新增樣式  
> 把 li 裝飾拿掉  
> ![](https://i.imgur.com/32y504E.png)   
> 拿掉 padding  
> ![](https://i.imgur.com/NAgPdS8.png)  
> 通通拿掉  
> ![](https://i.imgur.com/ZtFvpZY.png)   



![](https://i.imgur.com/H2ASdX7.png)  
> 用 col 大小會稍微無法控制  

----

# Bootstrap 漢堡條  
> ![](https://i.imgur.com/rwVjAVq.jpg)   
> 漢堡條只是觸發  
> 要把 nav -item 去調整
> 要小心展開(lg m )的位置!  
---

# JS 懶人包未來性  
> ![](https://i.imgur.com/CzaoMRa.png)   
> 例如 vue 適合中小型專案  
> Angular 適合大型  
> NUXTKS 未來也不錯  

- Vue 可以看怎麼去讀, 怎麼寫~  

[Top JavaScript Frameworks and Tech Trends for 2021 | by Eric Elliott | JavaScript Scene | Medium](https://medium.com/javascript-scene/top-javascript-frameworks-and-tech-trends-for-2021-d8cb0f7bda69)   

----

# 作業完成路線  

- 找色塊 > 天氣 API  > 
- 再來就做這個 微軟再臨-使用boosrtap   
- 最後是這個 ↓  

> ![](https://i.imgur.com/5gCaMuO.png)  

---

