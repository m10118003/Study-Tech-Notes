# 零、 CMD 指令教學
###### tags: `CMD101` `進度筆記` `心得``2020六月`


## 這是甚麼 ？
Graphical User Interface, GUI 圖形化介面, 對電腦做任何事情 。
早期用 Command Line Interface (CLI)對電腦說話, 但同時是在同一個資料夾做事情, 用文字操控電腦。

## 為何要學 ？ 
因為之後很多介面都沒有GUI ， 所以要試著學 ， 最簡單的指令就是在 CLI 中 用 ping 。' 
之後用 JavaScript 、 Git 、 連到 Server 都會用到 。

## 環境設置
安裝 git-bash 執行 command line 指令, 之後都是用 git-bash , 而 Mac 則可使用 iTerm2 。

一開始輸入 `pwd` (Print Working Directory) 看User位置, ls(常用指令)列出主要資料夾下所有檔案, 指令後面可以加參數 " - " 。

`ls -al` > 詳細檔案權限、擁有者、大小, 最後修改日期, 隱藏檔案之類; -l 表示顯示列表 ， -a 可顯示檔案 。

Change Directory (CD), 在不同資料夾間跳來跳去, " .. " 在這層資料夾的上一層 /c/Users/Haku, Haku的上一層是Users 。 " ~ " 表示USER路徑, 如 /c/Users/Haku 。

 `clear` 清除畫面; " Man "(MANual), 是使用說明(windows不存在這個指令, 但有替代字串, 例如ls --help, 可以列出所有加上 " - (字串) "的說明) 。  
 
 `touch` 建立檔案與更改檔案時間, 如果檔案存在的話, 則會更改檔案現在的時間, 因為我碰了他; 但如果檔案不存在, 我則會建立一個空白檔案, 並且可以用ls -al(-all)來看這檔案所有狀態 。

 `rm` (ReMove), 清除檔案; 如要移除資料夾加上" -d ", "--dir"; 加上-f會強制刪除(包含隱藏檔案), -r 則是移除資料夾和路徑下的子檔案; 可以合併指令例如 -dr, 完整指令則是 rm -dr (資料夾名稱) 。

 `mkdir` (MakeDirectory), 建立新資料夾, 用cd 的時候打幾個字再按tab可以自動完成 。

 `mv` (Move) 移動檔案或更名, 如果 mv *(資料夾名稱)* 會更換資料夾名稱; 如果在這個資料夾底下還有個資料夾, 則可把資料夾內檔案移往該資料夾下底下的資料夾;  絕對路徑如 "~", 相對路徑如相對現在資料夾, 假設我在/test 我要移動到 deep 底下, `cd deep` 的deep前面沒有加任何東西則會從 test 資料夾去找 deep 後再移動過去; 也可以說是該位置下底下的資料夾。 如果 `cd /deep` 則會跟你說根目錄下沒有這個資料夾(根目錄為硬碟下分割的槽, 如 /C:\, /D:\, /E:\ ) 。
 
如果要移動資料夾內的資料夾, 則要比該資料夾更高的位置, 如在 "~/test/deep" 目錄下, 我要移動 deep 這個資料夾, 則必須往上移動到 test, 才能移動 deep 這個資料夾, `mv ..` 則能把檔案往上一層移動 。

`CP` CoPy 複製檔案, 用法是 `cd "檔案名稱"` "檔案名稱+數字或是字母"; 如果要複製資料夾則是 `cd -dir` 資料名稱 新資料夾名稱(或是cd -r 資料名稱 新資料夾名稱) 。

 `vim` "v" "vi"(vim_improve) 文字編輯器, 在最上行按下 i 就可以插入文字並且編輯; 按下鍵盤 Esc 則會回普通模式, 按任何鍵都無反應, 但可以複製貼上; h 往左, j往下, k往上, l往右; 按下shift+ :q+enter 關掉這個視窗; :qa!</Enter> 離開vim; :set mouse=a 啟用滑鼠, 存檔:wq 檔案名稱; :wqa! 存檔並強制離開 。

 `cat` 會列印出檔案的參數和內容, 更多內容可以參考:   http://linux.vbird.org/linux_basic/0310vi.php#vi_vim  

 `grep` 抓取檔案內關鍵字, 例如 `grep y` 就會highlight檔案內關鍵字體的那一行, 搜尋的時候很好用 。

 `wget` 指令背後有程式在執行, 可以創造自己的指令自己輸出, `wget 網址全名` 就會下載成功, 可以用open指令開檔案, 然後也可以下載網頁原始碼, 如 `wget google.com`; `cat index.html` 就會列出原始碼參數內容 。   
 
 `curl` 送出 request, 可以測試 API, 例如 `curl google.com‵ 他就會列出:
![](https://i.imgur.com/AtOEzDy.png)  

  
 `redirection` 是"重新導向"(input output), ls -al > list_result, 將結果存成檔案, 用 `vim` 看檔案內容 。
 
 `echo` 會印出東西, `echo 你輸入的東西`, 會列出你輸入的東西在下一行, ls 本來會輸出到 CLI(git blash 視窗內), 如果多了 `>` 就會導向到其他地方或是指令, 如果我在輸入一次 `echo 輸入的東西` > 檔案, 則會把輸入的東西蓋掉檔案內容。如果要新增東西則是 `echo 妳輸入的東西 >> 檔案` 。

 `pipe` 可以把 "|" 左邊的輸出, 轉到 "|"右邊的指令做輸入, 例如cat 123 | grep 4, 會把列出123 轉給grep 這個指令去抓出 4 這一行的內容; 也可以和 "redirection" `>` 一起用, `cat 123 | grep 4. > \*new_result\*` , 這樣則會把列出 123 的檔案內容, 存到 \*new_result\* 這個檔案內 。

[![](http://img.shields.io/static/v1?label=SlackMe&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=0095FF)](https://lidemy.slack.com/app_redirect?channel=U014VGFNE6S)
[![](http://img.shields.io/static/v1?label=Linkedin&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=00BFFF)](www.linkedin.com/in/jhen-yu-shih-082b29129)
[![](http://img.shields.io/static/v1?label=→@ＩＧ&message=JhenYu&?style=for-the-badge&logo=appveyor=Slack&color=FF004C)](https://www.instagram.com/haku2zas/?hl=zh-tw)



