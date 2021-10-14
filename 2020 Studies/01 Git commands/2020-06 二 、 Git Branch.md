#  二 、 Git Branch
###### tags: `GIT101` `進度筆記` `Lidemy心得``2020六月第三週`

## 為何需要 Branch ?
一條線的開發模式這樣會把所有開發進程都拉在同一條線上進行 ， 這樣可能會有問題 ， 所有需要多線程開發 ， 即同時開發新功能(一條線) ， 另外做版本修復(bug fix; 另一條線) 最後再合併成一個新釋出(Release)給使用者。

## Branch 實際運作狀況像是 ？
![](https://i.imgur.com/zSN7cW7.png)

## 如何在 Git 開Branch
 `git branch -v` 就會在 master 旁開一個分支 ， 同時告訴你是從哪分出來的。  
 ![](https://i.imgur.com/W7XCN1n.png)
會告訴你從 change code.js 這個 commit 分出來 。

指令: `git branch -v name` 直接創立一個 branch 同時有名字; `git branch name` 後再用 `git branch -v` 看一下 ， 即先給 branch 名字後再建立 。
![](https://i.imgur.com/czhk6pQ.png)

## 刪除 Branch
 `git branch -d name` (d for delete).
 
## 在 Git 內切換 Branch
同樣用 `git checkout BranchName` 再用 `git branch -v` 可以看你目前在哪 。
![](https://i.imgur.com/pOjWAvO.png) ![](https://i.imgur.com/8HKbwGX.png)
 
 假如我今天修改了最新 branch 的檔案 ， 這時候一樣可以用 `git status` 看修改檔案的狀況 ， 並用 `git commit -am "name"` 把檔案加入 branch 的版本控制下。 ![](https://i.imgur.com/2SiRWf6.png)

同時再用 `git log` 看有哪些版本時 ， 會看到你在哪裡(青字 HEAD) 、 綠字表示有 branch 的 commit(2個); 同時 master(change code.js) 底下有個 branch(new-feature), 而基於 code.js 再修改後有個 branch 的 commit(new-feature2).
![](https://i.imgur.com/VM0ASir.png)

## Git Merge(合併)
當開發完成後 ， 要如何把 branch 合併到 master上 ， 則使用 `git merge name` 。
可以先用 `git checkout master` 回到 master 上 ， 接著用 `git branch -v` 看所在位置。
![](https://i.imgur.com/pBIyjAG.png)

使用 `git merge 你欲合併的 branchname` ， 接著使用 `git log` 可看到已把 branch 合併到 master 下 。
![](https://i.imgur.com/DSVioIc.png)

完成後記得 `git branch -d branchname` 把 branch 刪掉 ， 表示你已經開發完成 。
![](https://i.imgur.com/IuRIufh.png)

## Git Conflict(發生衝突怎辦)
如果同時跟同事改到同一行文字和檔案怎辦 ， Git 會不知道要相信誰的修改 ， 需要手動告訴 Git 我要留哪個檔案 ， 即兩個 branch 合併時有衝突 ， 但 Git 會告訴你問題在哪 ， 自行選擇要怎麼處理 ↓ 
![](https://i.imgur.com/CdQdANW.png)

假設開發新功能 ， 開一個新的 branch 是好習慣 ， 接著繼續開發 ， 最後切回 master 再 merge 如果有衝突就解決它 ， 沒衝突即開發完成 。

[![](http://img.shields.io/static/v1?label=SlackMe&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=0095FF)](https://lidemy.slack.com/app_redirect?channel=U014VGFNE6S)
[![](http://img.shields.io/static/v1?label=Linkedin&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=00BFFF)](www.linkedin.com/in/jhen-yu-shih-082b29129)
[![](http://img.shields.io/static/v1?label=→@ＩＧ&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=FF004C)](https://www.instagram.com/haku2zas/?hl=zh-tw)



