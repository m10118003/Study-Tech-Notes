# Week9 6-4 、 PHP 內建 Session 機制實作
###### tags: `BE101` `PHP` `2020十一月第二周` `進度筆記` `Lidemy心得`

***

Server 建立的 Session (session_start()) ， Server 會在設定下所指定的資料夾建立 session 檔案 `sessionID` ， 並且作為 cookie 數值 response 給瀏覽器；因此瀏覽器每次訪問這個 server 就會帶著對應的 cookie ， 像是通行證一樣給 server 識別 `sessionID` ， 並查詢對應的 session 檔案。

- session 是儲存在 server 端的，安全性高，不像 cookie 有儲存長度限制。 
- session 以文字形式儲存 ， PHP 會修改其權限，只保留供系統讀取和寫入許可。

****
## 先從登入開始
handle_login.php 檔案:  
```
<?php
  session_start(); // 告知 PHP 開始使用
  require_once('conn.php');
  require_once('utils.php');

  if (
    empty($_POST['username']) ||
    empty($_POST['password']) 
  ) {
    header('Location: login.php?errCode=1');
    die();
  }

  $username = $_POST['username'];
  $password = $_POST['password'];

  $sql = sprintf(
    "select * from users where username='%s' and password='%s'",
    $username,
    $password
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  if ($result->num_rows) {
    // 登入成功，不用再建立 token 和 cookie
	/*
	    1. 產生 session id (token) 
        2. 把 username 寫入檔案  
        3. set-cookie: session-id 設定到 client 端
	*/
    $_SESSION['username'] = $username;     	
    header("Location: index.php");
  } else {
    header("Location: login.php?errCode=2");
  }

?>
```
- 用 dev tool 看 handle_login.php 檔案，可以看到產生 token ， 一串隨機的字母和數字混合。  

***

## 首頁也要更動
index.php 檔案:  
```
<?php
  session_start();
  require_once("conn.php");
  require_once("utils.php");

  /*
    $username = $_SESSION['username']; 讀取動作時，會執行以下
    1. 從 cookie 裡面讀取 PHPSESSID(token)
    2. 從檔案裡面讀取 session id 的內容
    3. 放到 $_SESSION
  */
  $username = NULL; // 先檢查有沒有 username
  if(!empty($_SESSION['username'])) {
    $username = $_SESSION['username']; // 這邊 sessionID 還在，但不影響操作
  }

  $result = $conn->query("select * from comments order by id desc");
  if (!$result) {
    die('Error:' . $conn->error);
  }
  
?>

```

***

## 登出的修改
logout.php 檔案:  
```
<?php
  session_start(); // 同樣也要先呼叫 session 才有功能
  session_destroy();
  header("Location: index.php");
?>
```
- 不用自己清除 cookie ， 用 SESSION 自動清理 token 、 cookie。 

***

## 新增留言的部分
```
<?php
  session_start(); // 先呼叫 session 
  require_once('conn.php');
  require_once('utils.php'); // 不希望 utils 有太多依賴性

  if (
    empty($_POST['content'])
  ) {
    header('Location: index.php?errCode=1');
    die('資料不齊全');
  }

  $user = getUserFromUsername($_SESSION['username']); // 從 session 內 把 username 取出，再查表
  $nickname = $user['nickname']; // 把 nickname 指定給 user

  $content = $_POST['content'];
  $sql = sprintf(
    "insert into comments(nickname, content) values('%s', '%s')",
    $nickname,
    $content
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  header("Location: index.php");
?>
```
- session 的內容會寫到檔案，並丟到 temp 暫存資料夾內。  

***

## utils 的 token 也要更改
```
 function getUserFromToken($token) {}
```
會把 token 修正成:  
```
function getUserFromUsername($username) {}
```

***

- 之前實作的 session 機制會產生一個 token (即 PHP 內建 的 PHPSESSID )。 
- PHPSESSID 是拿來辨識身分用的，有一組隨機產生的亂數(混合英文和數字)。 
- SESSION 存的東西即 SESSIONDATA ， 會存檔在亂數所對應的亂數名稱檔案內。
- 登入成功後，會用 `$_SESSION['username'] = $username;` ， 讀取動作時，背後做了三件事情: 

1. 產生 session id (token)。  
2. 把 username 寫入檔案。  
3. set-cookie: session id 設定到 client 端。  

- 接著就用到 `$username = $_SESSION['username'];` :  
1. 從 cookie 裡面讀取 PHPSESSID(token)。 
2. 從檔案裡面讀取 session id 的內容。 
3. 放到 `$_SESSION` 變數內，跟 `$_POST` 和 `$_GET` 很像。 

- 最後新增留言 ， `$user = getUserFromUsername($_SESSION['username']); // 從 session 內 把 username 取出，再查表` 。  
- 登出用 `session_destroy();` 就可以把 session 內的東西清空。  

***

參考資料:
[PHP Session機制簡介及用法](https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/223920/)  

[後端基礎：PHP 的內建 Session 機制](https://hugh-program-learning-diary-js.medium.com/%E5%BE%8C%E7%AB%AF%E5%9F%BA%E7%A4%8E-php-%E7%9A%84%E5%85%A7%E5%BB%BA-session-%E6%A9%9F%E5%88%B6-f9a19209840f)  

[ SESSION ](https://sites.google.com/site/cliffluonsoftware/php/session)  

[PHP 不得不提的 session 與 cookie](https://iter01.com/440794.html)  

[深入 Session 與 Cookie：Express、PHP 與 Rails 的實作](https://blog.techbridge.cc/2019/09/07/session-and-cookie-implementation/)  