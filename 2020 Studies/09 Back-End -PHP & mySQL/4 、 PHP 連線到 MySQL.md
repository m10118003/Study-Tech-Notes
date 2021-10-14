# 4 、 PHP 連線到 MySQL
###### tags: `BE101` `PHP` `2020十月第二周` `進度筆記` `Lidemy心得` 
## PHP 與 MySQL 如何跟資料庫連線 
- 先在 phpMyAdmin 新增一個使用者帳號，主機名稱為 `localhost` 。  
- 勾選使用者帳號的資料庫以及全域權限(全選)。  

![](https://i.imgur.com/AwCY62U.png)  

- 執行後在結構的地方選剛創立的資料庫建立資料表。  
- 然後設置兩個欄位:  
1. 名稱(id) 、 類型(int) 、 AUTO_INCREMENT(PRIMARY) 。  
2. 名稱(username) 、 類型(varchar(64)) 、 編碼(utf8mb4_unicode_ci) 。 

- 如果編碼與排序沒修正的話，則在操作的地方修正成 `utf8mb4_unicode_ci` ，無修正之後可能遇到編碼問題。  

設定完成後來 conn.php 看這麼設定:  
```
<?php
  $server_name = 'localhost';
  $username = 'user';
  $password = 'secret';
  $db_name = 'user';

  $conn = new mysqli($server_name, $username, $password, $db_name);

  if (!empty($conn->connect_error)) {
    die('資料庫連線錯誤:' . $conn->connect_error);
  }

  $conn->query('SET NAMES UTF8');
  $conn->query('SET time_zone = "+8:00"');
?>
```
- `new mysqli()`新增一個 MySQL 的 instance ， 跟 database 建立連線。  
- 建立連線後的東西會回傳給 `$conn` 變數。  
- php 物件存取屬性的時候使用 `->` ， JS 則是用 `.` 。 
- `die()` 表示 `()` 內訊息輸出後，底下程式碼不會被執行，停止在這行。
	- 因為資料庫連線錯誤的時候，不希望程式繼續執行。
- 進一步簡化，去除 `!empty` ， 如果這個東西是有內容的話就 die 。  

修正成:
```
<?php
  $server_name = 'localhost';
  $username = 'user';
  $password = 'secret';
  $db_name = 'user';

  $conn = new mysqli($server_name, $username, $password, $db_name);

  if ($conn->connect_error) {
    die('資料庫連線錯誤:' . $conn->connect_error);
  }

  $conn->query('SET NAMES UTF8');
  $conn->query('SET time_zone = "+8:00"');
?>
```
- 通常會把連線分開寫，可能會有一個連線的檔案只寫連線相關資訊。  
- `require_once('conn.php')` 可能會類似這樣引入進來。  
- 所有需要用到資料庫的 php 和改設定的時候只要改這一行就好。
- 連線資料庫 `'SET NAMES UTF8'` 設定編碼，為了使用中文不出錯。  
- `'SET time_zone = "+8:00"'` 時區，確保在台灣的時區。  
- 如果 PHP 放上 GitHub 時會排除 connection.php 之設定檔案，因為會暴露帳號密碼。 
- 東西放到 Git 後很難被完整清掉(版本)，會在 `.gitignore` 檔案加上 connection.php 檔案，避免被上傳。
- 只寫連線相關資訊，在 conn.php 檔案。  

***
data.php 檔案內:
```
<?php
require_once('conn.php');

if (empty($_GET['name']) || empty($_GET['age'])) {
  echo '資料有缺，請再次填寫<br>';
  exit();
}

echo "Hello!" . $_GET['name'] . "<br>";
echo "Your age is " . $_GET['age'] . " <br> ";

print_r($_GET);

?>
```


***

# 4-1 、 PHP & MySQL : Read 
###### tags: `BE101` `PHP` `2020十月第二周` `進度筆記` `Lidemy心得`

==如何在 PHP 內把 MySQL 資料撈出。==  

## 讀取資料(Read) 
新增下行指令在 index.php 檔案中: 
```
<?php
require_once('conn.php');

  $result = $conn->query("SELECT * FROM users");
  if (!$result) {
    die($conn->error);
  } 
  // 如果 (!$result) 沒有值，則把 error 印出(在 connection 上)，並不要往下執行。 
  while ($row = $result->fetch_assoc()) {
    echo "id:" . $row['id'] . '<br>';
    echo "username:" . $row['username'] . '<br>';
  }
?>
```
- MySQL 指令 `SELECT` 可以換成 `select now()` 來選擇現在時間；這函式會是一個物件，包含 `current_field` 和 `num_rows` 等。  
- 如果第一步下的 `querry()` 的值是錯誤的(並不是函式)，則 `print_r($result)` 是空值(看有沒有拿到結果)；第二步可以用 `print_r($conn->error)` 顯示碰到的錯誤。  
- 第三部`($row = $result->fetch_assoc()` 用經過 querry 的相對應結果 `($result)` 來執行 `fetch_assoc()` 函式，然後拿到 `$row` 執行，表示根據 SELECT 的東西(Key)給你一個相對應的值(value)，是陣列；如果碰到不確的東西就先印出來。 
- `$row` 會是一個 array ； `echo 'now:' . $row['now()'];` 會是從資料庫拿出來的時間(很怪)。  
- `"select now() as n;"` 建立別名後，如果要從資料庫拿東西可以用 `$row['n'];` 。 

假設資料庫新增了三筆資料分別是: aaa 、 bbb 、 ccc 而如果
```
$row = $result->fetch_assoc(); 
print_r($row);
$row = $result->fetch_assoc(); 
print_r($row); 
$row = $result->fetch_assoc(); 
print_r($row); 
$row = $result->fetch_assoc(); 
print_r($row); 
```
跑到第四次則會出現錯誤，因為第四個 `$row` 會是空值，無法再拿取。  
- 拿取多筆資料可以用 while 迴圈。 

- `while ($row = $result->fetch_assoc())` 會像是這樣執行: 
```
先做 $row = $result->fetch_assoc();
再做 while($row) {} 並判斷 $row 是不是空值;
如果 $row 是空值則會停住;
```

***

# 4-2 、 PHP & MySQL : Create 
###### tags: `BE101` `PHP` `2020十月第三周` `進度筆記` `Lidemy心得`

使用本機的位置 `http://localhost/xampp/User/index.php` 。 

## 新增資料(Create)  
新增下行指令在 add.php 檔案中:  
```
<?php
  require_once('conn.php');

  if (empty($_POST['username'])) {
    die('請輸入 username');
  }

  $username = $_POST['username'];
  $sql = sprintf(
    "insert into users(username) values('%s')",
    $username
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  header("Location: index.php");
?>
```

***

### 如果要插入欄位:  
```
<?php
$ result = $conn->query("insert into users(username) values('apple')");
if (!$result) {
  die($conn->error);
}

print_r($result);

?>
```
- 上面這樣會自動增加 apple 字串的欄位，可以達成寫入資料功能。 
- `insert into users()` 因為設定AUTO INCREMENT, 所以 () 內填 username。   
- `values()` () 裡面填要放入的值, 因為是字串， `values('" . . "')` 要用字串拼接。  
- 如果 `query("values('apple')");` 內先用雙引號，值是字串用單引號 `('')` ， 否則可能產生錯誤。  

***

### 先加上 `$sql` 
```
<?php
require_once('conn.php');

$username = 'apple';

$sql = "insert into users(username) values('" . $username ."')");
echo $sql;
$result = $conn->query($sql);
if (!$result) {
  die($conn->error);
}

print_r($result);

?>
```
- 先把 query 獨立出來，成 `$sql = "sprintf("insert into users(username) values('"$username ."')", );` 。  
- 再印出 query 看是否正確。 

***

## `sprintf()` 函式
```
<?php
require_once('conn.php');

$username = 'apple';

$sql = sprintf(
  "insert into users(id, username) values('" . $username ."')");
echo $sql;
$result = $conn->query($sql);
if (!$result) {
  die($conn->error);
}

print_r($result);

?>
```
- 可以用這個函式讓字串拼接好理解。 
- 第一個參數內是字串，後面加上一個動態塞進去的數字和字符串 `%d` `'%s'` 成為 `values(%d, '%s')` ， 會按照順序加入值。 

***

### 請求資料(動態新增 username 的表單)
最後 add.php 檔案內如下:  
```
<?php
  require_once('conn.php');

  if (empty($_POST['username'])) {
    die('請輸入 username');
  }

  $username = $_POST['username'];
  $sql = sprintf(
    "insert into users(username) values('%s')",
    $username
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  header("Location: index.php");
?>
```
- 可以用 GET ，或是用 POST 請求資源。 
- `$username = $_POST['username'];` 這行可以不加，不過推薦先寫好。

- 透過 POST 拿 username 參數，如果沒有(顯示錯誤) 。 
- 有 username 的參數則繼續往下代給 `$username` 的變數。
- 並用動態代入的 `$username` 組成 SQL query 。 
- sql 印出來後去執行。
- 如果有錯誤就顯示錯誤(像新增同名檔案會顯示錯誤)，沒有則顯示新增成功。
- 因為要手動跳回 index.php 有點麻煩所以最後增加一個連結。
- 但比較直觀的是將連結 `<a href="index.php">return to the past</a>` 換成 header ， 會自動跳轉回 index.php。   
```
 header("Location: index.php");
```  

而新增的動態表單在 index.php 檔案中為:
```
<?php

require_once('conn.php');

  $result = $conn->query("SELECT * FROM users");
  // 可以加入 order by id asc 由小排到大;或是反序 desc。  
  if (!$result) {
    die($conn->error);
  } 
  // 如果 (!$result) 沒有值，則把 error 印出(在 connection 上)，並不要往下執行。 
  while ($row = $result->fetch_assoc()) {
    echo "id:" . $row['id'] . '<br>';
    echo "username:" . $row['username'] . '<br>';
  }
?>

<h2>新增 USER</h2>
<form method="POST" action="add.php">
  username: <input name="username" />
  age: <input name="age" />
  <input type="submit" />
</form>
```
如在 index.php 頁面中新增資料成功會顯示新增 USER 以及新增成功。  

![](https://i.imgur.com/sskXs8Y.png)  
   
![](https://i.imgur.com/QFQELXl.png)   

### `AUTO_INCREMENT`
- 每當往上加入一個 id 時，會有個變數以之前存的最高值(id)去記。  
- 因此會以最高的 id 值為主再加一，如果把連續的 id 中的值刪除。  
- 會產生 1, 2, 3, .... 9 ， 直接跳到 9(id) 的情況。  
![](https://i.imgur.com/6z3S2j3.png)  

- 也可以手動去調整資料選項。 

### dev tool
- 用瀏覽器開發人員偵錯工具下去看的時候，勾選:
	- Preserver log 和 Disable cache 。  
- 跳轉紀錄不會被記住。 
- 會看到 Status Code 302 頁面跳轉，瀏覽器接收到 header 請求。  
- 因此頁面跳轉回 index.php (代碼 200) 。 

***
參考資料: 
[PHP ： sprintf - PHP學習誌 - Google Sites](https://sites.google.com/site/phplearnmark/php/php-zhi-ling-qing-dan/zi-chuan-han-shi/php-sprintf)

https://kknews.cc/zh-tw/code/gmjky69.html

***

# 4-3 、 PHP & MySQL : Delete 
###### tags: `BE101` `PHP` `2020十月第三周` `進度筆記` `Lidemy心得`

使用本機的位置 `http://localhost/xampp/User/index.php` 。  

## 刪除資料(Delete) 

在 index.php 新增以下 code :  
   
```
<?php
  require_once('conn.php');

  if (empty($_GET['id'])) {
    die('請輸入 id');
  }

  $id = $_GET['id'];
  $sql = sprintf(
    "delete from users where id = %d",
    $id
  );
  echo $sql . '<br>';
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  if ($conn->affected_rows >= 1) {
    echo '刪除成功';
  } else {
    echo '查無資料';
  }

  // header("Location: index.php");
?>
```
### 用 GET 的方式來代  

用 GET 的方式把 id 代過去 delete.php 的檔案。  

在 index.php 中 新增: 
```
<?php

require_once('conn.php');

  $result = $conn->query("SELECT * FROM users");
  // 可以加入 order by id asc 由小排到大;或是反序 desc。  
  if (!$result) {
    die($conn->error);
  } 
  // 如果 (!$result) 沒有值，則把 error 印出(在 connection 上)，並不要往下執行。 
  while ($row = $result->fetch_assoc()) {
    echo "id:" . $row['id'];
	echo " <a href='delete.php?id=". $row['id'] ."
	  '>刪除</a>";
	echo '<br>';
    echo "username:" . $row['username'] . '<br>';
	
  }
?>

<h2>新增 USER</h2>
<form method="POST" action="add.php">
  username: <input name="username" />
  age: <input name="age" />
  <input type="submit" />
</form>
```
- 完成後點 id 後面的刪除會跳到相對應的 delete.php 檔案中的 id 位置。  
- `echo "<a href='delete.php?id=x'>刪除</a>"` ， `id` 這邊可以用 `sprintf()` 來代 id ， 或是用字串的形式 `id=" . $row['id'] . "`。  
- 如果刪除了不存在的 id 卻 query 執行成功了，而沒有出現錯誤，表示 query 沒有影響到任何東西。 
- 一般刪除不太會用 GET 來執行。  
- 用 POST 來執行刪除的動作的話，這 `echo " <a href='delete.php?id=". $row['id'] ."'>刪除</a>";` 會改成一個表單的形式。  


並新增 delete.php 檔案(用 add.php 檔案修改): 
```
<?php
  require_once('conn.php');

  if (empty($_GET['id'])) {
    die('請輸入 id');
  }

  $id = $_GET['id'];
  $sql = sprintf(
    "delete from users where id = %d",
    $id
	// $id 可以置換成 $_GET['id']
  );
  echo $sql;
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }
  // 沒有成功的話就印出錯誤。

  header("Location: index.php");

?>

```
- 可以在 PHP 抓到被 query 影響的有幾列 `echo $conn->affected_rows;` 。 
- 可以根據最後影響的列數來判斷有無刪除成功: 
```
if ($conn->affected_rows >=1) {
  echo '刪除成功';
} else {
  echo '查無資料';
}
```


***

# 4-4 、 PHP & MySQL : Update 
###### tags: `BE101` `PHP` `2020十月第三周` `進度筆記` `Lidemy心得`

使用本機的位置 `http://localhost/xampp/User/index.php` 。 
 
## 編輯資料(Update?)
在 index.php 的檔案新增: 
```
<?php
  require_once('conn.php');

  if (empty($_POST['id']) || empty($_POST['username'])) {
    die('請輸入 id 與 username');
  }

  $id = $_POST['id'];
  $username = $_POST['username'];
  $sql = sprintf(
    "update users set username='%s' where id=%d",
    $username,
    $id
  );
  echo $sql . '<br>';
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  header("Location: index.php");
?>

<h2>新增 USER</h2>
<form method="POST" action="add.php">
  username: <input name="username" />
  <input type="submit" />
</form>

<h2>編輯 USER</h2>
<form method="POST" action="update.php">
  id: <input name="id" />
  username: <input name="username" />
  <input type="submit" />
</form>
``` 

並新增一個 update.php 檔案:  
```
<?php
  require_once('conn.php');

  if (empty($_POST['id'] || empty($_POST['username'])) {
    die('請輸入 id 與 username');
  }

  $id = $_POST['id'];
  $username = $_POST['username'];
  $sql = sprintf(
    "update users set username='%s' where id=%d",
    %username,
	$id
	// 先找到 id=%d 的欄位，再設定 username 。 
    // 如果沒加 where 會編輯所有欄位。	
  );
  echo $sql;
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }
  // 沒有成功的話就印出錯誤。
 /* 
  if ($conn->affected_rows >=1) {
	echo '編輯成功';
  } else {
	echo '查無資料';
  }
*/
  header("Location: index.php");

?>
```
- CRUD 後端基本功能。 

***

## 學習心得:
- 基礎的 SQL 指令下法。  
- PHP 執行原理。  
- PHP 跟 MySQL 透過表單溝通。  
- CRUD 。 
- 留言版的專案(完整概念)。   
- 會員註冊、登入、開 API 、 資安。 
- 連線錯誤的時候不能下 Querry String (程式碼的位置)。  

*** 

## PHP 與 MySQL 指令快速查表 

```
<?php
  // 連線資料庫
  $server_name = 'localhost';
  $username = 'huli';
  $password = 'huli';
  $db_name = 'huli';

  $conn = new mysqli($server_name, $username, $password, $db_name);

  if ($conn->connect_error) {
    die('資料庫連線錯誤:' . $conn->connect_error);
  }

  $conn->query('SET NAMES UTF8');
  $conn->query('SET time_zone = "+8:00"');

  // 新增資料
  $username = $_POST['username'];
  $sql = sprintf(
    "insert into users(username) values('%s')",
    $username
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  // 讀取資料
  $result = $conn->query("SELECT * FROM users ORDER BY id ASC;");
  if (!$result) {
    die($conn->error);
  }

  while ($row = $result->fetch_assoc()) {
    echo "id:" . $row['id'];
  }

  // 修改資料
  $id = $_POST['id'];
  $username = $_POST['username'];
  $sql = sprintf(
    "update users set username='%s' where id=%d",
    $username,
    $id
  );
  echo $sql . '<br>';
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  // 刪除資料
  $id = $_GET['id'];
  $sql = sprintf(
    "delete from users where id = %d",
    $id
  );
  $result = $conn->query($sql);
  if (!$result) {
    die($conn->error);
  }

  if ($conn->affected_rows >= 1) {
    echo '刪除成功';
  } else {
    echo '查無資料';
  }
?>
```

***