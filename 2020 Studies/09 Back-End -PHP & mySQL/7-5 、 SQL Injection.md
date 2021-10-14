# Week11 7-5 、 SQL Injection 
###### tags: `BE101` `PHP` `2020十一月第二周` `進度筆記` `Lidemy心得`

***
## 駭客的填字遊戲 - SQL Injection  
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

***

## 不知道 user 身分也可以登入  
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

***

## 新增留言的部分也能注入
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

***
## insert into 的內容可被修改
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

***
## 預設資料庫
- information schema : INNODB_SYS_TABLE 。  
- 如果欄位的取名類似，可以被猜出來，用字串拼接(惡意字串)的方式下去撈出資料。  

***
參考資料:  
[\[Postx1\] 攻擊行為－SQL 資料隱碼攻擊SQL injection - iT 邦幫忙](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAFegQIARAC&url=https%3A%2F%2Fithelp.ithome.com.tw%2Farticles%2F10189201&usg=AOvVaw0yZ9T4kF3QGlDT_oohsfKm)  

[資安滲透攻防筆記-1\. SQL隱碼攻擊(SQL INJECTION ATTACK ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAGegQIFBAC&url=https%3A%2F%2Fmedium.com%2F%40gordonfang_85054%2F%25E8%25B3%2587%25E5%25AE%2589%25E6%25BB%25B2%25E9%2580%258F%25E6%2594%25BB%25E9%2598%25B2%25E7%25AD%2586%25E8%25A8%2598-1-c9a6b8ada5fa&usg=AOvVaw3ZLj3TGdtX5xD5sMPeVtif)  

[一次看懂SQL Injection 的攻擊原理| by Jayden Lin | 程式猿吃 ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAHegQIDhAC&url=https%3A%2F%2Fmedium.com%2F%25E7%25A8%258B%25E5%25BC%258F%25E7%258C%25BF%25E5%2590%2583%25E9%25A6%2599%25E8%2595%2589%2F%25E6%25B7%25BA%25E8%25AB%2587%25E9%25A7%25AD%25E5%25AE%25A2%25E6%2594%25BB%25E6%2593%258A-%25E7%25B6%25B2%25E7%25AB%2599%25E5%25AE%2589%25E5%2585%25A8-%25E4%25B8%2580%25E6%25AC%25A1%25E7%259C%258B%25E6%2587%2582-sql-injection-%25E7%259A%2584%25E6%2594%25BB%25E6%2593%258A%25E5%258E%259F%25E7%2590%2586-b1994fd2392a&usg=AOvVaw2r1xSjang4bH-tPVJoxX0N)  

[SQL Injection 範例(登入範例) @ 史丹利愛碎念:: 痞客邦::](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAIegQIDxAC&url=https%3A%2F%2Fnewaurora.pixnet.net%2Fblog%2Fpost%2F166231341-sql-injection-%25E7%25AF%2584%25E4%25BE%258B%2528%25E7%2599%25BB%25E5%2585%25A5%25E7%25AF%2584%25E4%25BE%258B%2529&usg=AOvVaw2XEIGuLALcyCUm2wUXuHbW)  

[SQL Injection 常見的駭客攻擊方式 - Puritys Blog](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAJegQIERAC&url=https%3A%2F%2Fwww.puritys.me%2Fdocs-blog%2Farticle-11-SQL-Injection-%25E5%25B8%25B8%25E8%25A6%258B%25E7%259A%2584%25E9%25A7%25AD%25E5%25AE%25A2%25E6%2594%25BB%25E6%2593%258A%25E6%2596%25B9%25E5%25BC%258F.html&usg=AOvVaw1dlrzUiP9-W6EySbzWHaXf)  

[何謂資料隱碼(SQL injection)攻擊？程式設計師應如何預防 ...](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAKegQIEhAC&url=https%3A%2F%2Fjob.achi.idv.tw%2F2011%2F09%2F11%2Fwhat-is-a-sql-injection-sql-injection-attacks-program-designers-should-be-how-to-prevent-it%2F&usg=AOvVaw0beac0TEPZCRq8hkciAXf4)  

[18-5 資料隱碼（SQL Injection）](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjALegQIEBAC&url=http%3A%2F%2Fmirlab.org%2Fjang%2Fbooks%2Fasp%2FsqlInjection.asp%3Ftitle%3D18-5%2520%25B8%25EA%25AE%25C6%25C1%25F4%25BDX%25A1%255DSQL%2520Injection%25A1%255E&usg=AOvVaw1iYqtIXUOGYuR4sJYovRI6)  

[SQL 注入- 術語表| MDN](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjn1Z35vrPtAhUSiZQKHb46BFYQFjAMegQIExAC&url=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-TW%2Fdocs%2FGlossary%2FSQL_Injection&usg=AOvVaw25wwRnk2h4Gu8qd-JybECM)  

***

# Week11 7-6 、 預防 SQL Injection 
###### tags: `BE101` `PHP` `2020十一月第二周` `進度筆記` `Lidemy心得`

***
