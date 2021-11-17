# 2021-11-16 CSS -  Swiper plug in - intro  
###### tags: `CSS3 基礎實作` `2021/11/16` `進度筆記` `前端心得`  
---

# 今日講課 -- 下午的部分  

# Swiper   

> ![](https://i.imgur.com/X4XwlMz.png)   

> ![](https://i.imgur.com/MFRwU6p.png)   

----

# 運作方式  

- 所有東西都在 ↓   
> ![](https://i.imgur.com/qjQ2mBv.png)   
> 他是一堆 div 塞在這個區塊內  
> 他有設定 `overflow hidden` 去隱藏超過父層的所有東西 ↓  
> ![](https://i.imgur.com/8i2DARs.png)   

# 這樣會爆出版面的原因  
> ![](https://i.imgur.com/MO8RsFc.png) ↓   
> 思考爆出去的原因  
> 看是外框超過還是寬度  


-----

# 可以調整  

> ![](https://i.imgur.com/cr2XcGW.png)   


----

# 如果要讓他無限跑  

> ![](https://i.imgur.com/M0vfNo6.png)   
> infinite loop  
> 可以去找參數調整指令 ↓   
> ![](https://i.imgur.com/sbvgflQ.png)   

- Swiper 內的參數設定 ↓  
> ![](https://i.imgur.com/yNLZJZq.png)  

----

# 如果要讓他自動跑  

> ![](https://i.imgur.com/LfHLHVA.png)   
> ![](https://i.imgur.com/0g3zd0z.png)   
> 5000 是 5 秒, 1500 是 1.5 秒   

----

# Space between  

> ![](https://i.imgur.com/fayOf11.png)   
> 這邊是在講, between slides ↑  

- 也就是在 Slides per view 的情況下 ↓  
> ![](https://i.imgur.com/e3ROW55.png)  
> 每個 Slides 間的 between  
> 可以讓 margin auto, 寬度降低點 ↓   
> ![](https://i.imgur.com/faKWENq.png)   

- 如果再設 block ↓  
> ![](https://i.imgur.com/z0Fvuit.png)  
> 就有 Slide 和 Slide 間的空格  

----

# 如何讓圖片置中變大  

> ![](https://i.imgur.com/0qCeFwv.png) ↓   
> 分辨上下張 slide 的 active 位置  
> 那就可以去 CSS對他做調整  

- 去對他放大兩倍 ↓  
> ![](https://i.imgur.com/8LkwFN3.png)  

- 去對他放大 1.2 倍 和漸變 ↓  
> ![](https://i.imgur.com/6D0fFdJ.png)

- 或是 讓中間那張縮小 0.8 倍 ↓  
> ![](https://i.imgur.com/8BrSn9n.png)  
> ![](https://i.imgur.com/Dq3q63p.png)  

----

# 讓左右兩側照片比較小  

> ![](https://i.imgur.com/IBocJ9D.png)  
> ![](https://i.imgur.com/tMUdWJ1.png)  

- 讓左右兩邊比較近 ↓  
> ![](https://i.imgur.com/IwXFKim.png)   
> ![](https://i.imgur.com/AgCCRTf.png)   


- 做出換圖效果 ↓   
> ![](https://i.imgur.com/50c74qT.png)  
> ![](https://i.imgur.com/ywNtWmT.png)   

----

# 實際上做  

- 可以下 opacity 對左右兩側圖片做遮罩  
- 可以下 transition  
- 可以用一堆 animation 去做控制  

- 你還可以做到燈箱效果 ↓  
> ![](https://i.imgur.com/ruKajg7.png)   
> 把輪播圖的點點控制換成圖片, 有燈箱效果   

----

# 置中和心得分享   

- 父層下 flex, 子層 margin auto  

> ![](https://i.imgur.com/1Nh9NLS.png)  

````
flex, justify-content, align-items
````


- padding 快速實戰  
```
padding 下在父層去推子層  
```

- margin 快速實戰  
```
margin 下在子層去推父層
```

- margin 邊界重疊問題  
```
像是 margin 下在 子層 
margin-bottom: 13px;

父層下 margin-top: 87px

疊起來不會是 100px
```

# 參考資料 - 邊界重疊問題  
[Css系列 - 如何避免邊界重疊 ( Margin Collapsing ) · Issue #6 · marshal604/blog (github.com)](https://github.com/marshal604/blog/issues/6)   

[理解邊界重疊的原因 \- CSS | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)

---

# 可以用卡片式的方法

- 比較好做 swiper  
> ![](https://i.imgur.com/9OOuuVg.png)   
> 也可以