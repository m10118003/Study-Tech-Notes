
# 0 、 PHP 前言
###### tags: `BE101` `PHP` `2020九月第四周` `進度筆記` `Lidemy心得` 09/21

==不一定當作處理 request 的腳本，可以用在後端開發。== 

- 後端在 DataBase 的運作。 
- 怎麼發 request 到後端，經過哪些地方到 DataBase ，再把 response 傳給前端。 
- 基礎實戰不一定要跟著做 ， 第九週直到 PHP 內建實戰機制。 
- 第九週 - 真正的實戰: 留言板(精華，重要的專案)。 
- 看完影片，從頭自己如何實作出來。 
- Cookie & Session 超重要。 
- 上傳作業和資料庫的地方。 

---

# 0-1 、 PHP 相關作業繳交
###### tags: `BE101` `PHP` `2020九月第四周` `進度筆記` `Lidemy心得` 09/21
- 不要把資料庫帳號密碼放上去、如何設定資料庫，以及上傳作業的方法(FTP)。 
- 第九週以後不是用 GitHub(因為 Git 只提供靜態，打開會看到 Source code) 。 
- 繳交作業是動態的， `conn.php` 會被 ignore 掉。 

---

# 0-2 、 PHP 環境建置
###### tags: `BE101` `PHP` `2020九月第四周` `進度筆記` `Lidemy心得` 09/21
Windows - XAMPP 官網：https://www.apachefriends.org/zh_tw/index.html 

- XAMPP 是 Apache + MySQL(最近被 MariaDB 取代) + PHP + Perl 縮寫。 
- MySQL 被商業公司收購，怕要付費的話，社群建置了 MariaDB 。
- 安裝好後開啟 Apache 和 MySQL 的 Modules Service ， 再點 Admin 會開啟一個位於 localhost/dashboard/ 的頁面(這頁面會位於 :/xampp/htdocs/dashboard/User 下)。 
- 安裝後更改檔案: config → <Browse> ， PHP 檔案會放在 htdocs 內

## 在 htdocs 底下建置資料夾(CLI)
有安裝 GitBash 後，直接在 htdocs 資料夾內右鍵 Git Bash here 或是用指令 move 到 htdocs ， 並 `mkdir Name` 一個資料夾，並在資料夾內創建 `touch a.php` 並添加內容 `vim a.php`。

- 在 CLI 文字編輯器底下輸入:  
```
<?php
  echo "I am Spider Man!";
?>
```

完成後，用瀏覽器開啟 `http://localhost/xampp/Name/a.php` 例如: 
```
http://localhost/xampp/User/a.php
``` 

![](https://i.imgur.com/557J8oe.png)

可以看到剛輸入的文字，代表伺服器有順利地跑起來。 
- XAMPP 這套軟體底下的 PHP 和 Apache 預設，網址路徑即是檔案的路徑。 
- 但其他語言和 Server 的軟體開法工具可能有不同的預設方式。 

---
參考資料: 
[電腦王阿達 - 架站好幫手 XAMPP](https://www.kocpc.com.tw/archives/165133) 
https://ithelp.ithome.com.tw/articles/10197921
---

# 0-3 、 PHP 基礎語法
###### tags: `BE101` `HTML+CSS` `2020九月第四周` `進度筆記` `Lidemy心得` 09/22

## php 標籤 

測試以 test.php 檔案為實際演練，如果沒有用到 php 語法，輸入程式碼或是文字就會顯示在頁面上。 

寫 php 語法必須用以下標籤，這樣區塊內的東西才會被執行輸出: 
```
<?php
  echo "123"
?>
```

或是簡寫(但這種語法有些 Server 不支援): 
```
<?
  echo "123"
?<
```
這樣可能會找不到錯誤或很難 debug 。 

---

### ==`echo`== : 可以輸出程式碼，如字串、變數，也能參入 html 。 
```
<?php
  echo "<h1>123</h1>";
?>
```
- echo 不是函式。 
- 每行結尾記得加上分號 `;` 。  

---

### ==變數 `$`== : 
```
<?php
  $a = 1;
  echo $a;
?>
```
- 會把 1 給印出來。 
- 變數前面一定要加 `$` 字號。 
- 結尾除了 `{}` 這種區塊之外，每行(敘述句)要加上 `;` 。 

---

### ==字串== :
```
<?php
  $a = "Yo Hello";
  echo $a;
?>
```

---

### ==兩變數相加== 字串串接: 
```
<?php
  $a = "aaaaaa";
  $b = "bbbbbb";
  echo $a . $b;
?>
```
- 字串拼接要用 `.` 。 

---

### ==if () else== : 
```
<?php
  $score = 60;
  if ($score >= 60) {
    echo "pass";
  } else {
    echo "fail";
  }  
?>
```
- 可以想成用變數不用宣告(var) ， 用的是 $ 開頭。 
- 也可以繼續加 `else if` 。 

### ==迴圈 Loop== : 
```
<?php
  for($i=1; $i<=10; $i++) {
    echo $i . "\n";
  }
?>
```

- 會印出 1~10 數字。 
- 換行 `. "\n"` ，但這樣做會變成空一格。 
- 但如果看原始碼其實是有換行，但在 html 解析下，多個換行會變成空白。 

![](https://i.imgur.com/kmK9wxG.png) 

- 因此空白會用 `<br>`; 。 
- 原始碼會變成這樣: 
```
1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>
```

---

### ==陣列 Array== : 
```
<?php
  $arr = array(1, 2, 3, 4, 5);
  echo "length:" . sizeof($arr) . "<br>";
  echo $arr[0];
  echo $arr[sizeof($arr)-1]
?>
```
- 會取得第 0 個元素 1 。 
- 取得長度是用 `$arr[sizeof($arr)-1]` 跟 JS 的 `.length` 很像，會得到 5 。 
- 不能用 `echo $arr;` 因必須把 array 轉成字串，不然無法輸出。 

---
### ==除了 echo 的另外選擇 `var_dump`== :
```
<?php
  $arr = array("Yo", 2, 3, 4, "YoHo");
  var_dump($arr);
?>
``` 
- 這樣會把每個變數的型態跟數值給印出來。 
- 如果要看比較複雜的資料結構，這時候可以用 `var_dump` 而不用 `echo`。 
- 或是可以用 `print_r` ， 就不會印出型態，簡潔有力的輸出。 

---
### ==Function== :
```
<?php
  function add($a, $b) {
    return $a + $b;
  }
  
  echo add(1, 3);
?>
```

---
參考資料: 
[PHP echo](https://www.wibibi.com/info.php?tid=291) 

***

# 0-4 、 Apache 與 PHP 原理
###### tags: `BE101` `HTML+CSS` `2020九月第四周` `進度筆記` `Lidemy心得` 09/22

- Request → php → Response 時 ， php 的角色沒有佔比重很重。 

如 XAMPP 的 Services 底下的服務，跟 FTP 有關的 ProFTPD ， MSQL 跟資料庫有關，最重要的服務是 Apache 。 

整體比較像是這樣: 
```
Request(test.php) → Apache(Server 端 run function(request 拿進來)) → php(Apache 將request 給 php ; php 執行 test.php 後，幫忙把 request 轉成要輸出的形式) → html out put(輸出;不是 html 也可以) → Apache(拿回 out put 後) → Apache reture Response 。 
```

- 用 dev tool 可以看到 Network 分頁底下的 Headers 會跟你說 Server 是用啥，等詳細資訊(正式環境會被隱藏)。 

![](https://i.imgur.com/jhFwD5b.png)

- 跑 Server 時，除了 php 也可以有 index.html ， index.js ， 都會由 Apache 處理。 

***

## ==php 端所處理的東西==
- 可以在 CLI 上裝套件跑 php 。 
- 可以想成 Apache 幫你 run php 的指令(下面是模擬): 
```
<?php
 $num = 1;
 echo "<br>" . $num . "<br>";
?>   
```
- 最後 Apache 幫你把 php 輸出的東西當作 response 傳回去。 
- 如果 php 掛掉，則可能傳回錯誤訊息，但 Apache 掛掉就甚麼都不能做。 

## ==網址的規則==
- 跟資料夾結構相符合，例如: 
```
localhost/User/test.php
``` 
跟 XAMPP 的路徑是相同的:
```
xampp\htdocs\User\test.php 
```
- Apache 預設規定我只能存取 htdocs 底下的檔案。 
- 大部分的網站 ， Server 端預設設定是這樣，以某個資料夾為基礎，但可以調整。 
- Server 端可以更改網址規則。
- 不會直接將原始碼給輸出，會經過處理。 
- 但中間不透過 php ， 也可直接將原始碼輸出(沒透過 Apache 處理也會直接將原始碼輸出)。 
- 如果像是常見的 `localhost/Users/123` 之類，規則會去資料夾下找有沒有123這個檔案，但可以更改設定用其他檔案回傳。 
***


