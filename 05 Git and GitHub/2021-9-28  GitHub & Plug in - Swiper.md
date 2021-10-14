# 9/28  GitHub & Plug in - Swiper  
###### tags: `CSS3 基礎實作` `GitHub`  `2021/09/28` `進度筆記` `前端心得`  
---

# 今日講課-上午的部分  GitHub 教學   

# GitHub 註冊  

[連猴子都能懂的Git入門指南 | 貝格樂（Backlog）](https://backlog.com/git-tutorial/tw/)   

----

# Git 和 GitHub 差別   

從 [https://git-scm.com/download/win](https://git-scm.com/download/win) 官方網站上下載，對應 OS 的 Git, 裡面會附贈 Git Bash 。   

- 一人版本控制:  
> 以前做報告會有好幾版, 都會想保存不同版的報告, 就有檔名區隔, 但小規模的時候很難看到區別  

- Git 是版本控制系統   :  
==Git 可以解決你在協作時, 如果你跟同事, 隊友同時編輯同一個地方, 檔案被覆蓋的問題==   

> 這是團隊的版本控制, 因此有版本 > 版本加新功能, 但同時 PM 跟你說有 BUG 要修>那就會在出一個 bug hotfix ↓   

![](https://i.imgur.com/mB1ZiVK.png)   


---

# 運作概念   

- 遠端數據庫和本地端數據庫   
- 本地電腦編輯的過程即是 ==Git==  
- 或你編輯完後丟上遠端數據庫   

> ==而遠端數據庫是 GitHub==   

> 有點像是 Google Drive 這種雲端硬碟   

----

# Git 工作方式 Push & Pull   

每一次你 Push 到遠端數據庫, 或是從遠端數據庫 Pull 下來的紀錄, 都會被 Git 這個系統幫你記住!  

這個紀錄就是版本差異的校訂(Revision)   

# 安裝 Git 後再安裝 GitHub Desktop   

1.   https://git-scm.com/download/win   

2. [GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)   

> GitHub Desktop 蠻簡單上手, 不過大部分工程師都用 Git   

---

# 先在 GitHub 上開一個新的 Repository   

例如上傳微軟仿切的頁面   

![](https://i.imgur.com/jv8Oo3q.png)   

- .gitignore 可以忽略你不想上傳的檔案   
- Liscense 控制你的授權, 常見的是 cc   

# main & branch   

- 主線 (main): 線上版的上線路線, 通常專案以這條為主路線(通常鎖起來, 客戶在用, 主管在看, 可能存在某些 bug, 不過修了後可能會產生更多 bug XD)   
- 分支(branch):   基本上跟線上版同樣的檔案, 不過可能會有幾個分歧路線   
    1. 修 BUG 路線: Entry level 可能常用, 不會修一次就跟線上整合一次, 會累積修到一定程度會跟 main 合併, 如果這邊修到炸掉, 還沒合併到 main 也不會出事情   
    2. 未來路線(未上線版本): 未來網站想做的東西之類的, 修到一定程度去跟線上版 main 合併   
   3. 嗯 ?   

![](https://i.imgur.com/zSN7cW7.png)   

很久以前的的主線叫 master, 現在是 main, main 有很大程度是中性用詞, 避免了 SJW XD   

==參考資料:==   

https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository   

---

# 工程師開源的道理   

Open source, 你從哪裡取用就從哪裡分享   

==參考資料:==  
[從 Redhat 到 GitHub，開源軟體為什麼開始火了？ | TechOrange 科技報橘 (buzzorange.com)](https://buzzorange.com/techorange/2019/01/16/open-sources-rule/)   


[在開源時代的興起下，如何透過License共享並保有權益 (progressbar.tw)](https://progressbar.tw/posts/61)   

---

# 搬 repository  

![](https://i.imgur.com/tb8lgM4.png)  

---

# create repository   
![](https://i.imgur.com/gPczfLg.png)   

---

# clone repo   

![](https://i.imgur.com/2D0S5rd.png)   

上 GitHub clone ↓   

![](https://i.imgur.com/yBZ8btf.png)   

---

# 測試一下 - 這邊是先 clone 後, 再 commit


開 READEME.md 檔案

![](https://i.imgur.com/RyE3gEn.png)   

他會讓你在 Vscode(或其他文字編輯器打開)  

寫幾行文字後把 Vscode 儲存後關閉, 回去看GitHub Desktop   

---

# 提交的時候是 commit  

![](https://i.imgur.com/eNG9UIh.png)   

- 記得有標題~   

每次提交(commit) 都要給個標題, 給標題才知道在做些甚麼事情~   

> 可以 describe  

提交後, 可以看到 有 undo   

![](https://i.imgur.com/qxRuTMo.png)   

---

# 結束了嗎? 還沒!  

你修改完的東西還沒上傳, 好了之後要 push origin 推上去後, 會看到 fetch origin 才算成功~     

![](https://i.imgur.com/c0wcWua.png)   

推上去後回到 GitHub, 重新整理就可以看到變化~  

![](https://i.imgur.com/bqdy2Fw.png)   

# 推微軟仿切上去到 GitHub~  

一般建議是 Clone 到一個你專門以後想放上去甚麼 Project 的資料夾   

- 因為 Git 幫你做的版本控制, 是另外開個資料夾   
- 所以~ 要把微軟仿切丟到這個資料夾內   
- ↓   
![](https://i.imgur.com/oTzNfvW.png)   

把東西丟進去↓   

![](https://i.imgur.com/sgsCSFO.png)   

好了後 commit 個標題, 例如 v1 或日期  

- 一樣 push origin, 將檔案推上去   

推上去後回到 GitHub, 重新整理就可以看到變化~  

![](https://i.imgur.com/nqMkNr0.png)  


---

# 目前先用 GitHub Desktop  

Setting → Repository  

![](https://i.imgur.com/SDux6HU.png)  

檢查 remote 有沒有到你的 GitHub   

![](https://i.imgur.com/sJsjYmV.png)   

![](https://i.imgur.com/eBJGKgW.png)   

---

# 有空試著做個人靜態頁面吧 - 例如個人履歷   

## 可以上 google, stack Overflow 去找學習資源   

==參考資料:==  

[\[架站\] GitHub Pages 也可拿來架設HTML靜態網站，與綁定網域名稱 | 梅問題．教學網 (minwt.com)](https://www.minwt.com/website/server/18522.html)  

[個人網頁模版教學 (nckuacc.github.io)](http://nckuacc.github.io/lastwork/)  

[\[Day3\] 完全免費! 一分鐘在GitHub建立個人網站! - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10259505)   


[Git 教學 - Git 書 - 為你自己學 Git | 高見龍 (gitbook.tw)](https://gitbook.tw/)  

[\[教學\] 使用 GitHub Pages + Hexo 來架設個人部落格 | 瑪利歐的部落格 (ed521.github.io)](https://ed521.github.io/2019/07/hexo-install/)  
 
 ---
 
 # 下午的部分 - GitHub Pull~  
 
 ---
 
 # 在遠端數據庫 (GitHub) 修改檔案   
 
 ![](https://i.imgur.com/ayNThQ2.png)   
 
 - 修改好後, commit change~  

![](https://i.imgur.com/zljcss7.png)   

記得下標題~   

![](https://i.imgur.com/NuDZL3d.png)   

這邊是先推到新分支, 在網頁上看 code 他是直接被修改   

---

# But  不同步 !?  

> 這邊線上版的 GitHub 檔案 跟 本機數據庫 (個人電腦的儲存空間) 是不同步的 ! 

![](https://i.imgur.com/9dYqMyT.png)   

---

# 這樣就可以按下 pull  

把遠端數據庫的檔案拉下來~  

讓遠端 (GitHub) 跟本地 (Local) 作到版本控制!  

修改紀錄都會被儲存~  

![](https://i.imgur.com/6I3VeNX.png)   

---

# 課堂練習 - 把 Twitch 仿切也放上去~  

---

# plug in - Swiper  

很受歡迎的製作輪播效果   

[https://swiperjs.com/](https://swiperjs.com/)   

![](https://i.imgur.com/MXmFyoc.png)   

---

# 題外話 -- 值得投資的技術 - 框架  
- React   
- Vue   
- Angular(職缺略少, 但猛)   
- Svelte : 第四個正在進行的框架   

![](https://i.imgur.com/Htpv0EI.png)   

權重可能不是 1 : 1 : 1, 產業別影響很大~

-----

# CDN 引入 swiper 的 library   
程式碼順序由上往下閱讀  

![](https://i.imgur.com/28J6ns3.png)   

# 自己做一次   
也可以模組化, 引入 CSS~  
![](https://i.imgur.com/TI5z6gj.png)   


---

# 加入基礎 layout   

這段是 HTML T-bone!  骨架的部分就引入一下~   
![](https://i.imgur.com/lj0rJ0U.png)   

整理一下縮排~   

- 刪除 "..." 省略號~  

# 自己玩一次   

> 記得刪除多餘的 "..." ellipsis   

![](https://i.imgur.com/prc1pHX.png)   

---

# 加入 CSS 樣式  

![](https://i.imgur.com/Tvu9JFL.png)  

外觀長這樣   

![](https://i.imgur.com/RlgFLil.png)  

---

# 來啟用一下 Swiper  

這段 CDN 是 Swiper 的核心檔案, 用 JS 製作的動畫↓  

![](https://i.imgur.com/2XEuFUN.png)   

↑ 讓他在 body 內, 置於那一堆 div 水泥隔板的下面   
>   - - -  > - - -  > - - -  > - - -  > - - 
↓ 找到這段來自 Swiper 的 js 來啟用這個輪播動畫~  
![](https://i.imgur.com/3rUX3CE.png)   

---

然後在剛才引入 CDN 核心檔案的地方~   
- 下面加入 script 後貼上這串來自啟用的 code   
![](https://i.imgur.com/4cirepE.png)   

---

# 練習讓 Swiper 動起來   

![](https://i.imgur.com/N8hPDCU.png)  

---

# 試著改 js code  

↓ 如果拿掉這行   
![](https://i.imgur.com/rXZ7ITg.png)   

就剩下這樣~  
![](https://i.imgur.com/XgIiQz3.png)   

---
---
---

# 課後任務 - 改微軟首頁的分頁輪播按鈕   

# 拿這個去改  
![](https://i.imgur.com/e426SdT.png)   

把 scroll bar, direction 去掉, 剩下的就可以用了   

引入後, 只要改 CSS 就差不多了~


把微軟弄好的東西想辦法塞進去 html ↓  
![](https://i.imgur.com/IMGRSP2.png)   

大概是從老師的範例 container 固定, 和 carousel 開始的CSS 樣式   

JS 不用去動~  

不過要改的就是把輪播圖的樣式置換成 圖片的包裝的樣式 

![](https://i.imgur.com/IZraPek.png)   


然後再把圖片推進去輪播圖~   

---

# 改變箭頭的樣式  

![](https://i.imgur.com/GeLwkeu.png)   
↓  
這個箭頭其實是個文字符號   

↓ 這個 Swiper 插劍設計的權重不會太大, 可以稍微調整一下
![](https://i.imgur.com/2K4CkVx.png)   

↓ 稍微改一下箭頭的樣式~  
![](https://i.imgur.com/meNAcZ5.png)   

↓ 然後他就被改色了   
![](https://i.imgur.com/PbZ3UvU.png)   

---

# 覆寫 CSS 的樣式, 像是點點也可以弄~   

![](https://i.imgur.com/1Rdcfju.png)  

![](https://i.imgur.com/X8QHaIn.png)  

---

# 也可以用網頁時光機去看微軟的舊設計稿   
https://web.archive.org/web/20210915223249/https://www.microsoft.com/zh-tw/   

用 Swiper 的方式去切換就好~   

---

# 之後如果做專題, 也可能會做到輪播~  

---
---
---