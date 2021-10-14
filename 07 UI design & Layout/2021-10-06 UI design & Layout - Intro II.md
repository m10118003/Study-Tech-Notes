# 10/06 UI design & Layout - Intro II  
###### tags: `UI design & Layout` `網站企劃概論` `2021/10/06` `進度筆記` `前端心得`  
---

講師: 盧政憲  
視覺設計 / 介面設計

# 今日講課 -- 早上部分  
  
- 接續昨天上課內容   
- 製作 wireframe  


---

# 案例分享   

- 國家運輸安全調查委員會 ([https://www.ttsb.gov.tw/](https://www.ttsb.gov.tw/ "https://www.ttsb.gov.tw/"))   
- Matt painting ↓   
![](https://i.imgur.com/KpXXtOv.png)  
> 多頁式網站  

-   [AeonFitness (aeon-fitness.com)](https://aeon-fitness.com/)
- Parallax  
![](https://i.imgur.com/RKLaiRF.png)  
> 比較乾淨俐落  
> 詢價  
> 下載產品介紹  
> 聯繫  

- [金門縣金湖鎮開瑄國民小學 (km.edu.tw)](http://ksps.km.edu.tw/zh-tw)   
> 多頁式網站  
> ==多語系==
> 不是替換成其他語言就好, 如果文字有超出會跑版、討論  
> 可以看到背景影片播放在學生活  
> 背景有手繪圖   

---

# [Bootstrap](https://getbootstrap.com/)   
  

Bootstrap 網頁有 demo  
![](https://i.imgur.com/5vkGtBp.png)  

---

# 補充 - 格線系統  (Grid layout)  

- 編排是屬於自由意識的, 想怎麼做就怎麼做  
- 多了解其他網站怎麼做, 例如 s6, awwwards, muuuuu  

例如透過主題的標題文字, 在遠處吸引你去看   
> Logo 放在左上角是最明顯的, 右下角是最不明顯的   
![](https://i.imgur.com/B0gY1cJ.png)   
> 人偏好看圖像和符號, 比較不愛文字 
> 
> 故會將這類型放置在大多數人的身高及視線範圍 

![](https://i.imgur.com/RQs5RFp.png)   

![](https://i.imgur.com/ZOpdX4I.png)   

![](https://i.imgur.com/jKHTFq0.png)   

> 會仰賴比例尺來進行編排   
> 網站有屬於它的格線系統   

---

# 回到 Bootstrap  
[簡介 (Introduction) · Bootstrap 5 繁體中文文件 - 六角學院 v5.0 (hexschool.com)](https://bootstrap5.hexschool.com/docs/5.0/getting-started/introduction/)

- 十二欄位系統   

1. 方便切版  
2. 限制寬度   

![](https://i.imgur.com/1PeKI1w.png)  
> 其實這也是 Wireframe  
> 這些綠線可以拿來編排網頁內的內容  
> 工程師可以比較快執行 code   
> 框架(線)的問題是比較不能像手刻那麼自由   
> 比較貴的是量身打造(手刻?!)的客製化網站   
> 這是稿圖, 還沒那麼確定   

- Wireframe  
![](https://i.imgur.com/SHA21lD.png)   
> 比較確定的稿圖  

- 十二欄位系統  
![](https://i.imgur.com/c4p7Wdy.png)  
> 綠色部分是十二欄位的系統   
> 為什麼要有背景 ↓  
- 十二欄位例如 ↓  
[東京都中央卸売市場 (tokyo.lg.jp)](https://www.shijou.metro.tokyo.lg.jp/)  
> 左右兩邊的背景, 會拿來扣除某些特定螢幕寬度空間   
> 通常網頁都會注意寬度, 比較不會注意長度, 因為可以一直往下滾動  
> 扣除寬度的限制, 這樣會比較好做 RWD  
> 因此在更寬的螢幕, 像是 2K 背景就會更大   
> 十二欄位會因為視野的寬度, 去設計視野的限制範圍   
> 十二欄位常應用在 PC, 但到了平板、手機 不適用十二欄位  
```
因為十二欄位套在平板、手機蠻精細的, 所以設計師會自由發揮, 例如: 4 欄, 6 欄
```

---

# Bootstrap 框架預設  
- 例如: 1140px  這寬度  
> 台灣常以 Bootstrap 做重點  

![](https://i.imgur.com/C69ph9G.png)   
> 間距 1.5rem 在網站常用, 但設計師常用 pixel 單位  
> 所以 px 轉到網站上就會換成 rem   


![](https://i.imgur.com/uo3ME8N.png)   
- md 平板的寬度   
![](https://i.imgur.com/mubeWHj.png)   


- 960px 可以解決大部分 1024x1366 螢幕 ↓ 的問題, 省錢, 省功, 省時間   
![](https://i.imgur.com/5DcgzmY.png)  

==除了 Bootstrap 的預設, 其實也可以跳脫他的規範(寬度)限制==

---

# 跳脫框架的限制  

有使用 Bootstrap 的網站: [Best Bootstrap Websites | Web Design Inspiration (awwwards.com)](https://www.awwwards.com/websites/bootstrap/)  


- 不在預設範圍內  

- 也是使用 Bootstrap 的框架下   
- [#musiquebleue - #musiquebleue](https://www.musiquebleue.org/)   
![](https://i.imgur.com/oUT3zOs.png)   
> 跳脫了預設  

- [Cube - Digital Agency](https://cube.nl/)  
> 連 pixel 都刻到小數點   
> 一樣跳脫了預設  

----

# 介面設計工具   

![](https://i.imgur.com/eJpdvLh.png)   
- 個人專題主要使用 AI 製作  
- 團體可能用 Figma  
> 因為頁面東西少(?), 有幾個彈跳按鈕  
> 如果要走 UI/UX, Sketch 和 Figma(次世代 UI 神器) 也要學一下   
> 但你會 AI 你就會 XD 然後你就會 Figma 惹 
>  
> XD (免費版跟付費 → 才能分享到往上跟), Figma(目前免費, 可以線上協作)  
> Figma 還能做企劃(?!)
> XD 有版本, 相容 AI 但 AI 不相容 XD 的問題  

==檔案頁面多用 XD, 頁面少用 Figma==  

----

# 單位   

![](https://i.imgur.com/SNUyPtm.png)   

[PXtoEM.com: PX to EM conversion made simple.](http://pxtoem.com/)   

[Px、Em 换算工具 | 菜鸟教程 (runoob.com)](https://www.runoob.com/tags/ref-pxtoemconversion.html)  

![](https://i.imgur.com/ne1fmXs.png)   
> 記好這個, 十二欄位常用~  

---

# 課外知識 - 出血   

![](https://i.imgur.com/VTnfC9M.png)   

- 假設這是名片   
![](https://i.imgur.com/NZRZloo.png)  
> 機器印刷切割名片的時候可能有震動  
> 可能有公差產生, 容許裁切的誤差 → 出血  > 實際尺寸

# 用 Illustrator 來做 UI   

![](https://i.imgur.com/WHi3QeS.png)  

- 螢幕解析  → 72ppi  
![](https://i.imgur.com/PhuOH9Q.png)   
> 300ppi 常用在印刷  
> 螢幕裝置如果限制極限 range 高, 常用 72ppi  

---

# 頁首製作   

- 通常先做頁首再去做其他頁面   

![](https://i.imgur.com/y2kdUD2.png)  
> 高度不要比寬度大, 記得把框線拿掉  
> 記得框線 border 也有寬度   
![](https://i.imgur.com/8lke5H8.png)   
> 間距, 24px   

![](https://i.imgur.com/79HGoiO.png)   
> 留白就是一半的間距, 12 px  
![](https://i.imgur.com/HCeu7WS.png)  
記的置中↓   
![](https://i.imgur.com/48aYXLr.png)  


# 製作 十二欄位  
- 先找網格   
- 選取 1296px 的圖片後找 ↓  
![](https://i.imgur.com/WMGYa0P.png)   
↓  
![](https://i.imgur.com/cXLNVvf.png)   

![](https://i.imgur.com/tzITvc5.png)   
> 解散圖片和網格群組  
> 往下拉拉到你覺得足夠用的長度 ↓  
![](https://i.imgur.com/FrdHIev.png)  
> 打開尺標   
> 幫 1320px 圖片上尺標參考線   
![](https://i.imgur.com/DvAQ6ej.png)   

- 自己 try  
![](https://i.imgur.com/OytfYkJ.png)   

---

# 預設滿版: 970px  

![](https://i.imgur.com/aMZtWbj.png)   
> 接下來就可以做各種東西  
> 像是卡片, 四欄式  
> 三欄式  
> 這樣區塊寬度相同, 工程師也好執行   

# 意外的情況 五欄位  

![](https://i.imgur.com/d6xlxdG.png)   

- 水平均分 → 對齊選取位置 → 還能細調(均分間距)  
![](https://i.imgur.com/LYjLfy0.png)  

---

# 十二欄位可以做到的事情  
- 例如:  
![](https://i.imgur.com/cmyumKa.png)   
> 當然還有文字~  

---

# 文字排版  
- 通常給六階, h1 ~ h6   
![](https://i.imgur.com/stJxe8l.png)  
> 還有你想操作的物件   

[給客戶看的網站設計（一）字級大小對網頁樣式的影響 | CTK Pro - 竑盛科技股份有限公司](https://www.ctkpro.com/blog/webdesign-font-size/)   

- 大部分使用的 font-size  
![](https://i.imgur.com/LYn4IVF.png)  
> 中日英的文字高度稍微不同  

## 數位稿時會先定義文字大小  
- 字體多大, 線稿的字體就要多大
![](https://i.imgur.com/JZKkT80.png)   
↓  
![](https://i.imgur.com/L39PmfK.png)  

- demo:  
![](https://i.imgur.com/FU1kKcH.png)   
- 如果文字無法對齊到參考線  
> 把靠齊像素關掉  
![](https://i.imgur.com/UvNf3tr.png)   

---

# 點陣文字 vs 區域文字   

- 區域文字  
![](https://i.imgur.com/8q6hjDX.png)  
> 可以自動換行   
> 字很少的時候不用   

- 點陣文字   
>文字少的時候可以使用  
>直接縮放區塊，文字會放大

---

# 呈現物件  
> 可以點擊, 不能點擊的按鈕...等   
> 為了讓東西統一 → 多工作業時   
> 先設定好規格 → 後面的人拼拼圖  
> 得到相同程式碼  

---

# 編排 Wireframe 的時候先不要   
- 別思考圖片  
- 怎麼編排特效  
- 別想太多~~  

![](https://i.imgur.com/cjR38Yr.png)   

---

# 如果是手稿(繪)作法  
- 溝通的最快用法, 手繪  
- 紅線表示十二欄位限制範圍   
- 不用畫滿   
- 碰到圖片會打叉, 數位稿不用   

- 例如  
![](https://i.imgur.com/pGotDTT.png)  
- 左邊的做法是正確的 ↓  
![](https://i.imgur.com/hzLjBSI.png)   

- 卡片內容  
![](https://i.imgur.com/8ynlW1B.png)  
> 圖片  
> 標題  
> 日期  
> 兩行文字  
> 吧啦吧啦   

---

- Icons 的畫法  
- 這是亞馬遜的作法  
![](https://i.imgur.com/s0t9aoA.png)   

---

- 文字的畫法   
![](https://i.imgur.com/Ap2yiyz.png)   
> 靠左對齊  
> 置中對齊   

![](https://i.imgur.com/cxieAKG.png)   

---

- 彈跳視窗   
![](https://i.imgur.com/cJxaU3a.png)   
> 做出一個 pop up   
> 表示螢幕 1920x1080的大小   

---

# Wireframe 在做甚麼？   
[Wireframe.cc | The go-to free, online wireframing tool.](https://wireframe.cc/)   
[Wireframe是什麼？認識網站UI設計排版草圖與資訊架構｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/wireframe)   
[什麼是 Wireframe ? · 嫁給 RD 的 UI Designer (akanelee.me)](https://blog.akanelee.me/posts/159788-what-is-wireframe/)   
[Wireframe、Mockup與Prototype的差異？來看看完整的產品UI設計流程 - 寫點科普 Kopuchat](https://kopu.chat/2017/06/22/wireframe%E3%80%81mockup%E8%88%87prototype%E7%9A%84%E5%B7%AE%E7%95%B0%EF%BC%9F%E4%BE%86%E7%9C%8B%E7%9C%8B%E5%AE%8C%E6%95%B4%E7%9A%84%E7%94%A2%E5%93%81ui%E8%A8%AD%E8%A8%88%E6%B5%81%E7%A8%8B/)   
[設計師必懂 (一) \- Wireframe 與 Prototype 的不同 | 設計大舌頭 (designtongue.me)](https://designtongue.me/%E8%A8%AD%E8%A8%88%E5%B8%AB%E5%BF%85%E6%87%82-wireframe-prototype-%E7%9A%84%E4%B8%8D%E5%90%8C/)   
[Wireframe 誰都會畫？. Wireframe (線框圖)… | by Ted Deng | Medium](https://medium.com/@teddeng/wireframe-%E8%AA%B0%E9%83%BD%E6%9C%83%E7%95%AB-466b671d82b4)   
[Wireframe是什麼？認識網站UI設計排版草圖與資訊架構｜ALPHA Camp Blog](https://tw.alphacamp.co/blog/wireframe)   
[製作 Wireframe 設計圖的免費工具整理 - G. T. Wang (gtwang.org)](https://blog.gtwang.org/useful-tools/free-wireframe-tool/)   
[使用者介面設計｜WireFrame (mepopedia.com)](http://jinjin.mepopedia.com/~jinjin/ui/ui-05.html)   

---

# 下午的時候作手稿  
# 一樣有檢討~  
# 目前在設計工作區  

--- 

# 靜態的設計稿也可以拿來參考~   

![](https://i.imgur.com/L2Z47GH.png)   

---

# 參考線  
- 如果解除鎖定   
- 手動製作的會跟著移動到新的工作區域   
![](https://i.imgur.com/LO3URhs.png)   

---

# 記得網站是可以向下一直長的  

![](https://i.imgur.com/zVFo20o.png)  
> 不是新增工作區域~  

# 選單的位置  
- 同學的範例  
![](https://i.imgur.com/4ySEzyp.png)   
> 可以往左邊丟   

- aside 的範例  
![](https://i.imgur.com/RIfI9p4.png)   
> 增進使用者體驗, 左邊比較好用~   

- 也有做在右邊的, 不過拉開是滿版的   
![](https://i.imgur.com/6OoWZvY.png)   

- 簡單典雅暴力   
![](https://i.imgur.com/URPMhTG.png)  


> 老師示範:  
![](https://i.imgur.com/bEMZFNB.png)   
> 這家店有沒有粉絲團, 餐點, 打卡, 甚麼資訊可以提供~  

![](https://i.imgur.com/PKmAwfj.png)  
> 區塊可以有不同形狀變形  
> 不用所有東西都在 12 欄位內   

- 可以看有沒有當季商品在裡面  
![](https://i.imgur.com/cw3iOks.png)  
> 像是咖啡杯常常會做俯瞰, 看裡面有沒有東西  

- 有時候會讓東西突出去   
![](https://i.imgur.com/uLr0Bh4.png)   
> 留白的空間才能置中~   

- 也有整個主題都是米的網頁   
![](https://i.imgur.com/y9rrYCk.png)   
> 剪裁遮色片也是米的形狀  

- footer  
![](https://i.imgur.com/ExMW3cq.png)  
> 整個滿版, 大一點的   
> 也有比較扎實的 footer, 或是靠旁邊的形式   
> 不要受功能限制   

---

# 補充 - 所見即所得   
```
What You See Is What You Get
```
- 輸入的樣式, 文字, 都是由後面的人所影響   
> 怎麼輸入就怎麼影響~  
> 螢幕看到的東西與輸出成果相同~  

---

# 彈跳視窗的介紹   

- 同學的範例   
![](https://i.imgur.com/Lx2chW6.png)   
> 可能有些購物車, 選單按鈕的編排   
- 遊戲的畫面放法 ↓  
![](https://i.imgur.com/zQ8T2w6.png)  
> 介紹往上或往下放  
> 有些玩家看遊戲實際玩法, 風格, 效果, 玩家可能很少看到敘述  

![](https://i.imgur.com/gra0T8W.png)   
> 彈跳視窗往上排~   
> 可以往特效走~  

---

# 補充 - Codepen 介紹

[https://codepen.io/lynnandtonic](https://codepen.io/lynnandtonic)  
> 神人作品   

---

# 補充 - Icons 網站  
- freepik   
[Free Vectors, Stock Photos & PSD Downloads | Freepik](https://www.freepik.com/)  

- flaticon  
[Free Vector Icons and Stickers - PNG, SVG, EPS, PSD and CSS (flaticon.com)](https://www.flaticon.com/)   

- font awesome  
[Font Awesome](https://fontawesome.com/)   
> 對工程師超友善網站   
> SVG 向量檔案可以載, for ui  
> 可以把向量插圖存成程式碼~  

---

# 商圈介紹   
- 有些網站像金門國小, 在頁首可能有攝影介紹   
- 要想辦法思考一進來的話, 讓人知道這個網站的特色   
![](https://i.imgur.com/ol9Yx57.png)   
> 很多 sponsor 都會要設計稿, 但我們可以呈現設計理念給 sponsor  


---

# 課外 - 參考   

[你才糙 code !!你全家都糙 code - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10209818)

---