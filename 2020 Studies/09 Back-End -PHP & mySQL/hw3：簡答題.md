# Week11 hw3：簡答題
###### tags: `BE101` `PHP` `2020十一月第三周` `進度筆記` `Lidemy心得`

***
## ==1. 請說明雜湊跟加密的差別在哪裡，為什麼密碼要雜湊過後才存入資料庫:==  

### 編碼（Encoding）  
- 一開始的發展是編碼，把一團資料各自表述，使用不同方法來解釋，不用金鑰就能解碼的不安全方式。  

### 加密（Encryption）  
- 後來發展出加密，是一對一的方式。  
- 用金鑰來保護重要資料的安全方法，且加密和解密過程都需要用到金鑰。 
- 但其實沒那麼保險，如果被知道加密演算法，和金鑰，那被存在資料庫的密碼都會被解開。
```
明文(ex. aaa) → 加密 → 密文(ex. bbb)
密文(ex. bbb) → 解密 → 明文(ex. aaa)
```   

### 雜湊（Hash） 
- 因此發展出多對一的方式，會有很多種字串對應到有限的結果。  
- 把一堆欄位的資料丟進某種 function (Hash function)進行運算，且得到的結果無法用來反推回原來的資料，也就是更難以取得使用者訊息。  
```
明文(ex. aaa) → Hash → 文字(ex. j1o1h7n)
```
- 如果有兩不同東西產生同樣 Hash 的結果時被稱之為"碰撞"。 
- 知名的演算法發生碰撞機率超級低，幾乎不太可能。 

### 例如，取餘數
```
n%999

1 => hash =>1
2 => hash =>2

但 1001 => hash => 2
2000 => hash => 2
```
知道結果是 2 ， 但是無法知道 hash 前輸入的值是多少，因此是單向的。  

- sha256 > MD5(不安全) 。  
- https://emn178.github.io/online-tools/sha256.html  
- 使用者在註冊的時候，把其密碼經過 hash 後存到資料庫。  
- 其 user 在登入時輸入的密碼一樣也透過 hash 後，與資料庫經 hash 的 user 密碼做比對，如果出來的結果一樣，代表輸入的值一樣，因此可以應用。  

***

## ==2. include、require、include_once、require_once 的差別:==  

### `include()` 函數  
- 會將指定的文件訊息讀取後並執行裡面的code 。  
### `require()` 函數  
- 會將目標文件資料內容讀去後，並把自己本身換成這些讀取後的內容。  
### `include_once()` 函數  
- 在 code 執行時抓取並運行指定資料；此方法和 `include()` 語句類似，差別在於如果該文件中已經被抓取過，則不會再次抓取。而且只會抓取一次。  
### `require_once()` 函數  
- 和 `require()` 語句幾乎一樣，差別在於是由於 PHP 特性會檢查該資料是否已經被抓取過，如果有則不會再次被抓取。  

***

## ==3. 請說明 SQL Injection 的攻擊原理以及防範方法:==  

- User 登入網頁時，之前我們有透過 hash 的方式讓密碼被 hash 並存在 server 。   
- 之前我們撈 username 的時候 ， SQL 上的語法 `sql = sprintf("SELECT * from users where username='%s' and password='%s'", $username)` 是用字串拼接的方式。   

- 而用 hash 的形式在 phpMyAdmin 上執行:  
```
SELECT * from users where username='aa'#' and password='bbb'
相同於以下這段
SELECT * from users where username='aa'

```
'#' 之後的字都變黃色，代表註解；如果 username 用 '#' 字串傳入，這樣就會成立 query ， 而且會以 aa 的身分登入網頁。  

- 這樣會有個問題，知道 username 就可以任何人的身分登入。

### 不知道 user 身分也可以登入  
```
SELECT * from users where username='%s' and password='%s'
如果改用這段
SELECT * from users where username='' or 1=1#
```
1=1 是 true ， 會把資料庫所有的 users 都 select 出來。  

- 也因此帳號填入 `' or 1=1#` ， 而密碼隨便填:  
```
username: ' or 1=1#
password:123
整段 query 變成
SELECT * from users where username='' or 1=1# and password='123'
```
這樣也會把所有資料都 select 出來。  

- 也因此填入惡意構造的字串，注入到 SQL 後就會變成不同的意思，掌握了 query 。  

### 新增留言的部分也能注入
```
INSERT INTO comments(nickname, content)
values('%s', '%s')
        ↓
nickname: a, content: b
        ↓
INSERT INTO comments(nickname, content)
values('a', 'b')
```
==INSERT INTO 的指令可以同時塞入多個指令。==  

- 一個 INSERT INTO 可以塞入多筆資料。  
- 這樣可以試著把原本的 query 改成，這樣塞入多筆資料的形式。  
- 這樣就能控制 `content` 的 `%s` 例如:
```
content: '), ('admin', 'test')
        ↓
INSERT INTO comments(nickname, content)
values('%s', ''), ('admin', 'test')
```
Query 就會變成 insert into comments 然後塞入兩個 values 。 

- 將這個 `'), ('admin', 'test')` 貼在沒有防止 SQL Injection 的留言板上會新增兩個 comments 。  
- 應用字串拼接的方式來拼湊改造，達到想要的入侵目的。  

### insert into 的內容可被修改
`insert into` 的內容可以是 `select` 的內容，例如:    
```
insert into comments(nickname, content)
values('aaa', (select password from users limit1))
```
sub-query 的概念，一個 query 內可以有其他的 query 。  

- 這樣就有被偷取密碼的風險，甚至可以更改、選定特定用戶的資料出來。  
```
'), ((select username from users where id=40), (select password from users where id=40))#
```
這樣會把 `id=40` 的 user 的帳號和密碼給撈出來。  

### 預設資料庫
- information schema : INNODB_SYS_TABLE 。  
- 如果欄位的取名類似，可以被猜出來，用字串拼接(惡意字串)的方式下去撈出資料。  

### 防範SQL injection方法

- Escape Parameters ， 透過正規表達式對 user 輸入參數進行檢查，如有關鍵字符合 SQL 語法，則將它替換成合法字元。  
```
缺點在於 SQL 的關鍵字一旦新增，檢查規則整個都要大改，因此總有漏洞，無法全面防範。  
```

- Query Parameterization ， 參數化查詢，大部分情況使用這防範方式相當安全，幾乎是安全解法；原理是資料庫語法中的佔位符號，丟進去的參數不會被執行。  
```
SELECT * FROM person WHERE name = $1 AND password = $2
``` 

- White List (白名單)，在特殊的情況下使用的，在 Query Parameterization 可能會失效的情況下用；常是使用 `Order By` 這樣可以根據條件選擇欄位排序，檢查並限制 user 的輸入欄位必須是固定數值。  
```
SELECT * FROM users ORDER BY (CASE WHEN (TRUE) THEN lastname ELSE firstname)
```

***

## ==4. 請說明 XSS 的攻擊原理以及防範方法:==  

### XSS (Cross-site Scripting)  
- 跨網站執行 JS ， 例如在留言板中滲入 `<script></script>` ， 使留言板被劫持。  

![](https://i.imgur.com/Oiq5uKz.png)  

- 留言內容被解析成程式碼的一部分，既然可以寫 script 就可以做更多事情。  
- 離如導到其他網站，像是釣魚網站，或是用 `alert(document.cookie)` 去抓 SESSION ID 。 
- 這樣如果把目前觀看頁面的 user cookie ， 甚至傳到有心人的 server 。  
- 知道 user cookie 就可以得知 SESSION ID ， 再來就可以偷身分、資料，非常危險。 
- 所以應該做特殊處裡，把留言的一部分作成文字，而不是可以載入的 code 。   

### 修補 XSS 漏洞  
- ==`htmlspecialchars()` 可以把特殊字元編碼==，例如 `<` 是小於的符號，透過編碼後變成 `&lt;` 這字串就會被 html 解釋成小於這個符號，而不是小於的 tag 。  

- 把內容跳脫後再顯示出來，就可以讓 script 被當作"文字"。 
```
<p class="card__content"><?php echo escape($row['content']); ?></p>

``` 
- 暱稱和建立時間也要跳脫，不然也會有 XSS 風險。
- 只要是使用者可以控制的地方都要注意到。    

***

## ==5. 請說明 CSRF 的攻擊原理以及防範方法:==  

- CSRF 是一種 Web 上的攻擊手法，全稱是 Cross Site Request Forgery，跨站請求偽造。  
- 是點擊按鈕之後瀏覽器就會發送一個 GET 的請求給某個網址，如 `網址後接/delete?id=3` ，但因為瀏覽器的運行機制，會一併把該網址本身的 cookie 都帶上去。
- 而因 Server 端收到後檢查 session，發現是 user 的 request ， 且這輸入訊息是 user 發的，於是就將訊息刪除。  

### 防範方法

- user 每次瀏覽完後，登出所有輸入資料訊息，並且刪除 cookie 。   
- Server 主動防禦，透過 request 的 header 內有欄位叫做 referer，代表這個 request 是從需求方要求並傳送，可檢查這欄位是不是合法的 domain，不是的話直接 reject 。

- 要注意，有些瀏覽器可能不帶 referer ； 有些 user 可能會關閉自動帶 referer 功能，這時 server 就會 reject 由真正 user 發出的 request ； 如果要檢查 domain 是否合法，則 code 必須要想辦法保證沒 bug 產生。  

***