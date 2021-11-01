# 2021-11-01 JS the short version - Vue initialize and import    
###### tags: `JS` `Vue` `2021/11/01` `進度筆記` `前端心得`  
---

講師: 佘昌霖 老師   

---

# 框架  

- 幫助你軟體或網頁開發時, 好用的懶人包  
- 幫你打包好一大堆功能的好用軟體, 工具  
- 照他的使用說明書去做, 就 Boom ! 完成了  

# 參考資料 - 框架  
[軟體框架 \- 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/wiki/%E8%BB%9F%E9%AB%94%E6%A1%86%E6%9E%B6)   

[Day21 - 何謂框架? - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10248882)   

[前端框架簡介 \- 學習該如何開發 Web | MDN (mozilla.org)](https://developer.mozilla.org/zh-TW/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Introduction)   

----

# 早上的部分  

# 環境建置   

# 為什麼要用 `Vue.js`  

- 華人地區很常用  
- Vue 的結構單純, 從哪裡傳到哪都幫你定義好  
- 因為都照 Vue 的規則走, 所以比較難用其他寫法進去  
- 有說法是 Vue 適合做小型專案  
- 全球有 80% 的專案適合用 A, 但總有 B 想用其他規則   
> 這時就不好用 Vue  

- 3 版不支援 IE, 但功能齊全  

# 參考資料 - Vue 3 版  

[Vue3 (vue3js.cn)](https://vue3js.cn/)   

----

# Vue 安裝方法  
1. CDN    
2. NPM   
3. Donwload  
4. CLI   
> 這次用 Node.js(包含 NPM )  
> Node.js → 底層是 JS 的程式語言   
> Vue, swiper, bootstrap 都是用 node.js 開發的  
> 16.13 LTS (Long Time Support, 官方長期維護使用 / 不會隨意更動)   

# 參考資料 - `Node.js`

[Node.js (nodejs.org)](https://nodejs.org/en/)   


----

# NPM  
- 方便管理的工具  
- 這工具可以管理 node.js 套件   
- 用到框架會用到~  
- 管理 Node.js 的工具  
- Node.js 可以拿來架 Server  
> 以 JS 為主的後端套件, 但網頁開發也會用到它的指令, library  
> 例如 Apache 伺服器可以套   
```
不過 Apache 到了現在, 會比較有以前舊時代的東西, 
執行效率還是不錯, 但比較沒那麼有效
```

- 中間會有安裝 Chocolatey, 可以勾選  
> 這會幫你安裝相容 C / Python 語言的工具 Chocolatey   
> 如果 Chocolatey 安裝不了的話就可以去把 Chocolatey 整個砍掉, 或是安裝 Visual studio, .Net framwork   
> 但其實這套件目前不會用到, 不用特別去安裝沒關係  

- 安裝好後會跳出兩個 CLI 視窗    
> ![](https://i.imgur.com/yYVpQaJ.png)   
>  Chocolatey 要三 GB 硬碟空間, 安裝好後建議 reboot  
>  ![](https://i.imgur.com/0suI4bo.png)   

安裝好後, 去 CLI 輸入:   
```
npm -v
```
- 有東西就算成功了   

> ![](https://i.imgur.com/z9V7etC.png)    

```
記得不要在 Node.js 這個視窗下執行~ 
Node.js 的視窗, 這是跟瀏覽器類似的環境, 
會去執行, 例如我們寫程式去用瀏覽器印出東西, 
瀏覽器也是 JS 的環境

要在 CLI / 命令提示字元 / Node.js command prompt 下的視窗, 去做輸入  
```

> ![](https://i.imgur.com/KZBbHvP.png)   

----

# 用 CLI 安裝 Vue  

- 在 CLI / 命令提示字元 / Node.js command prompt 下的視窗, 去做輸入    
> ![](https://i.imgur.com/XWRvkDe.png)   
```==
npm install -g @vue/cli
```

> ![](https://i.imgur.com/ECvuE3i.png)   
> ==安裝好了會像這樣==  

- 接著再輸入 `vue -V` 要大寫的 `-V`  
> ![](https://i.imgur.com/rFSBPOC.png)  
> 會出現 Vue 的版本提示訊息   

==不要在 power shell 下安裝, 可能會無法成功==   

----

# 在專案建立 vue 的資料夾  

- 找一個資料夾    
```==
根據這個資料夾的位置  
會建立你的專案位置 ! 
``` 
> 可以用這種方式開啟 CLI  
> ![](https://i.imgur.com/dU1weNg.png)     

- 找好一資料夾後  
> 在 CLI 內輸入  
```==
vue create 專案名稱
不能有大寫, 只能有底線或減號連接
```
> 好了後會像這樣  
> ![](https://i.imgur.com/dEDmBdU.png)   
> 可以按 Y(跟你說連到 NPM 會快一點)  
> ![](https://i.imgur.com/o48PRQX.png)   

- 會跟你說有 pick a preset   
> ==前面 1., 2. 兩個選項都是 Default==  
1. Vue 2  
2. Vue 3   
3. 手動選  

---

# 選擇手動設定  
- ==Manually==    
> 選好後會跟你說用到那些東西  
> ![](https://i.imgur.com/XL4cauj.png)   
> 用空白鍵選擇 / 取消  
> ![](https://i.imgur.com/NqR9NjU.png)   
```==
選這幾個  
Choose Vue version
Babel → 可以轉譯 ES6, function 等等讓舊的環境去相容執行
Router
CSS Pre-processors → SCSS / SASS
Linter / Formatter → 強迫矯正你的程式語言習慣  
```

> ![](https://i.imgur.com/1yZVhnf.png)   
> 好了後按下 Enter  

- 選 3.x    
> ![](https://i.imgur.com/ZmNecww.png)  
- 你的 Vue 要支援上一部功能嗎?    
> Y   
- 選最新的 SCSS  
> with dart-sass  
- 選 Eslint error  
> Basic  
- 選 Lint on save  
> 一直幫你存檔  
- 選 package.json  
> 幫你相容 json 模組化  
- 未來是否還要套用設定?  
> 選 n  
- 選 npm 還是 yarn ?  
> 選 npm  
> 接著就開始幫你安裝 vue 專案(下載)    

- 好了後就會有 Vue 的專案資料夾   
> ![](https://i.imgur.com/qPwGTZg.png)  
> 可以用 Vscode 開啟你的專案  

- 整體設定大概是這樣  
> ![](https://i.imgur.com/PWWDZbS.png)   

- 好了後會跟你說完成了甚麼  
> ![](https://i.imgur.com/yZOZeiD.png)  

- 完成的資料夾  
> ![](https://i.imgur.com/lMoxzYp.png)   
> ![](https://i.imgur.com/qqQlfBf.png)   

- 好一點的學習曲線   
- 學完前端(可以包很多東西) → 後端(可以模擬資料傳遞) → 框架  


# 參考資料 - Vue 教學  

[\[Vue.js\]\[筆記\]新手也適用的 Vue.js 專案從無到有. 最近才發現自己雖然會寫 Vue.js 這個 framework… | by shuuzhu | A Brighter Day | Medium](https://medium.com/a-brighter-day/vue-js-%E7%AD%86%E8%A8%98-%E6%96%B0%E6%89%8B%E4%B9%9F%E9%81%A9%E7%94%A8%E7%9A%84-vue-js-%E5%B0%88%E6%A1%88%E5%BE%9E%E7%84%A1%E5%88%B0%E6%9C%89-7acdf8f03a7a)   

[Installation — Vue.js (vuejs.org)](https://vuejs.org/v2/guide/installation.html)   

[Mac安装Vue环境 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/270608704)  

----

# 打開 Vscode  

- 我們可以先打開 README.md  
> ![](https://i.imgur.com/LTN0uaO.png)   

> ![](https://i.imgur.com/I3ZN4QD.png)   

- package.json 下會套用需要的套件   
> 載下來的套件會放在 node_modules   
> 安裝的套件會顯示版本, 套件需要用到的套件..等  
> ![](https://i.imgur.com/sueB6i6.png)   

- 專案還沒開始寫 就有 126 mb 了  
> ==大部分都是 modules 套件占掉==   


- 而 git ignore 可以選擇不要上傳到 github 的檔案  
> ![](https://i.imgur.com/tfHd7ev.png)   
> 不上傳就會有個問題, 假如沒上傳 node_modules  
> 這樣其他人下載你的專案的時候會因為沒有套件  
>  沒錯, 跑不動~  
>  可以用 重音符號 \`\  + ctrl, 或是上方列     
> 去找 terminal 去打指令   
> ![](https://i.imgur.com/WQr8qcu.png)   

-  所以要再跑一次 `npm install` 去安裝需要的套件  
>  ![](https://i.imgur.com/B7IMfsI.png)  

---

- ==source 會是你實際要寫的位置==  
---
- view 會是圖示圖  
> ![](https://i.imgur.com/eMRZjzs.png)   
> 安裝這個, 可以比較清楚的顯示資料夾  
> 安裝好後可以 Set File Icon Theme, 有 classic  或是 specific    
> 按一下 Material  
> ![](https://i.imgur.com/ip2wtlA.png)   

---
 
> ![](https://i.imgur.com/a9rDB2K.png)   

- 檢查環境, 執行 `npm run serve`   
> 開啟資料夾專案  
> 不管點到 babel, 還是 jason, 或是 `READEME.md`底下  
> 都可以直接輸入指令 `npm run serve`   
> ![](https://i.imgur.com/ifrfYuG.png)   
---
>> ![](https://i.imgur.com/bPpZMMk.png)  
---
>>> ![](https://i.imgur.com/xML4lgV.png)   
---

==如果 npm run serve 不成功, 可以重新安裝 Node.js==
> 這樣可以幫你環境重新指向, 如果再不成功  
> ↓ 參考資料  

# 參考資料 - 解決環境問題   
[關於 npm 安裝的套件任何指令都失效解決辦法 | 是 Ray 不是 Array (hsiangfeng.github.io)](https://hsiangfeng.github.io/nodejs/20190801/449913843/)   

-----

# 網頁有很多重複的元素  
- 像是 Wiki 標題, 圖案, 位置幾乎都在相同的地方  
> ![](https://i.imgur.com/rYtmaUs.png)  

- SPA, 這個網站實際只有一個頁面   
> ![](https://i.imgur.com/5RzX5Wr.png)   
> ![](https://i.imgur.com/xFFP17W.png)   
> 就算在同頁面切換  
> 也只有內容會換  

- 也就是這個 `index.html`  
> ![](https://i.imgur.com/zprhqk4.png)   

- 這一段會套用 vue  
> ![](https://i.imgur.com/1eXfrPL.png)  

- router 是根據  
> ![](https://i.imgur.com/4IywneP.png)   
> ![](https://i.imgur.com/4KnBgnM.png)   
> 一路找下去   
> 可以找到  
> ![](https://i.imgur.com/qXjaECz.png)   
> ![](https://i.imgur.com/uzJeuc3.png)   

# 也就是說 Vue 會把一個網頁拆成很多元件  

- 如果你今天只切網頁, 可能這個網頁是有整體性的  
- 但網頁上有些區塊, 按鈕, 是重複的元素  
- 所以你可以重複元素先切好, 弄成小零件  
- 然後你就可以讓這些零件, 例如你點到按鈕後會產生甚麼改變  
- 例如 A 頁面套用甚麼樣的零件, B 又有不同的零件...等   

- 也就是模組化的概念  
- Index 的網頁下有拆成一大堆元件, 這些元件 像是 router 可以導到 src 下的模組結構   
- Vue 可以幫你組這些元件 !  

> ![](https://i.imgur.com/UvkB4f0.png)   

- 像 template 就是 html 的格式  
> ![](https://i.imgur.com/TyPy4Vg.png)  

- Script 是寫 JS 的地方  
> ![](https://i.imgur.com/Xg55iuO.png)   


# 參考資料 - Vue   
![](https://i.imgur.com/3JLzUkO.png)  
  
---


# Vue 大部分解  

## assets 也就是資產  
- 大部分的圖檔, 影片檔, 音樂檔, 甚至是 jason 檔就會放在這裡  
> 例如, imgs  
> 也可以在 assets 下做分類  


## components & views  
- components 跟 views 的檔案規範是一模一樣的  
- 例如 Icons 是一種圖片, 類似的概念  
- 如果是獨立頁面, 你可能會想把它放在 views  
- 如果是小元件, 小東西, 那你可能會想放在  components   

==Views 跟 components 彼此可以互串, 沒有上下位分別==   

> ![](https://i.imgur.com/lmhutxV.png)   
> views 可以串 views, 串 components~  

----

# 好, 那這些東西要去哪?  
```==
你寫的東西, components, views 
都組成 app.vue 後
```
==這些東西經過編譯後, 就可以生成頁面==  

- 也就是這個 index.html 頁面  
> ![](https://i.imgur.com/gCH7MqF.png)  

> 發現都看不懂, 沒關係, 因為是機器幫你編譯的  
```==
你把一堆零件(compon, views)組起來後, 
做成模型的各零件(app.vue 下各位置), 
然後這個素體(組好後的 app.vue), 
去 噴漆 / 上色 後就會是編譯後的結果
當你把模型弄乾後就是成品了, 
也就是 dist, 但通常你會擺著不會去動到 dist 這個成品 
```

# 要怎麼引入 CDN, CSS?  
- 可以開 `index.html`   
> ![](https://i.imgur.com/g3sA1j9.png)   
> 在 header 的部分去放  


----

# 要怎麼知道方塊放哪?  
- 這時候就需要接線生 router  
- 它會告訴你要接去哪!  
- 就像是路標指引你  
> ![](https://i.imgur.com/sBpHntO.png)   
> 如果你的網址長這樣   
> 他會根據你的網址顯示你要去的區塊給你!  

==的確是路標==  
```
/goods/A
它會給你商品 A  
```

> ![](https://i.imgur.com/wj5aOOM.png)  
- router-view 會告訴你這個要放甚麼 view  

> ![](https://i.imgur.com/HTO6HT1.png)   
>這是第一種寫法  
>![](https://i.imgur.com/aW3rOTo.png)  

第二種寫法是省資源的  
> ![](https://i.imgur.com/NC6wYQ1.png)  

----

# 開始寫 Vue  
- 首先你要有個 vue 的 頁面  
- App.vue, 或是任何的 vue 大部分都會分成幾個部分  
> ![](https://i.imgur.com/HJjvt5V.png)  
> 分成 template, 會串到網站的部分  
> ![](https://i.imgur.com/74GXzHM.png)   

---

# 課堂練習 - 改成這個樣子  
> ![](https://i.imgur.com/a5T8KpK.png)   
> 實際上是導到這 ↓  
> ![](https://i.imgur.com/IDh2zOn.png)   
> 可以從 index.html 來找  
----

# 11/8 做到 11/24 做一個完整的網頁出來  

# 禮拜三講 SEO, 之後會Personal 訪談  

----

# 首先, 準備好頁面  
- 靜態的沒有用 JS 
> ![](https://i.imgur.com/tEoBSY2.png)  
> ![](https://i.imgur.com/Fg3MoGm.png)   

- 在 views 內放個 parallax.vue 檔案  
- 把 html 放進去 template 內  
> 在 vue 內開 style 區塊  
- 放入 CSS
>  ![](https://i.imgur.com/h7HNyEa.png)   

----

## 接著 在 App.vue 動手腳  

> ![](https://i.imgur.com/z5zAlVJ.png)  

----

# 接著打開路由  

>![](https://i.imgur.com/HWW1S5Q.png)    

- 使用你一開始開啟 npm run serve 的那個 8080 頁面, 就可以看到網頁  

---

# 如果你的圖片要放進來   

- 必須是這樣   
> ![](https://i.imgur.com/VEjzWKD.png)   

---

# 模組解釋  
- name 可以不用動, 之後有命名需求才要用  
![](https://i.imgur.com/fLCTEPY.png)  

- 這個 import 像是宣告的概念, 可以導入 Home.vue  
> ![](https://i.imgur.com/mJIKln6.png)  

- 接著去 App.vue 增加連結  
> 就有視差範例  
> ![](https://i.imgur.com/xMdpigv.png)  

> ![](https://i.imgur.com/fCerGLa.png)   
> ![](https://i.imgur.com/HmCuB2M.png)   
> 因為有後端概念, 建議用絕對路徑 `~@` 去寫  
> 這樣會從 src 開始  
> ![](https://i.imgur.com/dUFyBkM.png)   

> ![](https://i.imgur.com/BeLjBBe.png)  

> ![](https://i.imgur.com/oOTgtNZ.png)   


- 如果要放 SCSS  
> ![](https://i.imgur.com/OzUEC6i.png)   
> 要多一個 lang=scss  

----

# 幫 Vue 導入 / 編寫做個總結  

# 如果是引入    
> ![](https://i.imgur.com/cuCsIYY.png)   

# 如果是 HTML CSS 就寫在這裡  
> ![](https://i.imgur.com/CxtCrW0.png)  

# 如果是連結 就寫在這裡  
> ![](https://i.imgur.com/jMN6UtK.png)    

---

# 額外套件 - Vetur 
- 超過 8.8 M 人安裝  
> 主要是可以讓 Vue 內的 code 有顏色  
> 容易分辨  
> ![](https://i.imgur.com/OP36kb3.png)   
> 
----

# 參考資料  - Terminal 問題  
## 如果遇到 `vue -V`, 或是 `npm run serve` 無法執行  

[解決 Windows 上輸入指令出現「因為這個系統上已停用指令碼執行，所以無法載入...」的問題 | 是 Ray 不是 Array (hsiangfeng.github.io)](https://hsiangfeng.github.io/other/20200510/1067127387/)   

---

# 你可以用 GitHub 存檔  
- 做版本控制  

----

# GitHub 運作流程  
> ![](https://i.imgur.com/sBhT3FI.png)   
> commit 會先把你的專案資料夾內的檔案變更, 改動到在地資料庫  

- 如果要推上網路雲端  
> 如你下 push 指令則會從在地資料庫上到網路雲端  

- 然後如果你在網路雲端上有做更動檔案的話  
> 你就要 Fetch 到在地資料夾(下載下來)  

- 在地資料庫再合 (pull) 到專案資料夾  
> 完成  

- 如果有衝突 (conflict) 就要解決!   
> ![](https://i.imgur.com/NUSKlsN.png)   
> 看是要刪除, 或是留下來同事的專案資料  
> 溝通要溝通好~ 
> imcoming 是要修改的, upstream 是載下來的code  
> 建議 save both  
> ![](https://i.imgur.com/bRs256R.png)   


- 如果你今天連推都沒推上去, 按 fetch 就被覆蓋掉了!?  
- 如果你還沒按 fetch, 你可以先備份專案  
![](https://i.imgur.com/PkZo1mB.png)

----

# 假設你今天要多人協作  

- Manage access  
> ![](https://i.imgur.com/IsrWqbM.png)   
> 可以寄出邀請信, 7天內會過期  
> 被邀請者要在 e-mail 按 view info   
> ![](https://i.imgur.com/HYKOtq0.png)
> 接著再去參加  
> 如果出現 404, 代表你可能沒登入, 記得登入一下  
> 接著你就可以加入去寫專案  

---

# GitHub 上做成靜態頁面   
1. 要是公開的 public  
2. 或是 private(付費)  
3. 必須是 index.html  

-----