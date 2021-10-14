# Week11 7-3 、  發現問題：XSS  
###### tags: `BE101` `PHP` `2020十一月第二周` `進度筆記` `Lidemy心得`

***

XSS (Cross-site Scripting) ， 跨網站執行 JS ， 例如在留言板中滲入 `<script></script>` ， 使留言板被劫持。  

![](https://i.imgur.com/Oiq5uKz.png)  

- 留言內容被解析成程式碼的一部分，既然可以寫 script 就可以做更多事情。  
- 離如導到其他網站，像是釣魚網站，或是用 `alert(document.cookie)` 去抓 SESSION ID 。 
- 這樣如果把目前觀看頁面的 user cookie ， 甚至傳到有心人的 server 。  
- 知道 user cookie 就可以得知 SESSION ID ， 再來就可以偷身分、資料，非常危險。 
- 所以應該做特殊處裡，把留言的一部分作成文字，而不是可以載入的 code 。   

***
參考資料:  
[什麼是Cross-Site Scripting（XSS）攻擊| 程式前沿](https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/46727/)  

[\[IS\] Cross-Site Scripting(XSS) | PJCHENder 未整理筆記](https://pjchender.github.io/2020/06/30/is-cross-site-scripting-xss/)  

[Cross Site Scripting (XSS) Software Attack | OWASP Foundation](https://owasp.org/www-community/attacks/xss/)  

[XSS攻擊範例-Cross-site scripting(跨網站指令碼攻擊) @ 史丹利 ...](http://newaurora.pixnet.net/blog/post/187351995-xss%E6%94%BB%E6%93%8A%E7%AF%84%E4%BE%8B-cross-site-scripting%28%E8%B7%A8%E7%B6%B2%E7%AB%99%E6%8C%87%E4%BB%A4%E7%A2%BC%E6%94%BB)  

***

# Week11 7-4 、 PHP 內建修正 XSS 問題   
###### tags: `BE101` `PHP` `2020十一月第二周` `進度筆記` `Lidemy心得`

***

- 修補 XSS 漏洞。
- ==`htmlspecialchars()` 可以把特殊字元編碼==，例如 `<` 是小於的符號，透過編碼後變成 `&lt;` 這字串就會被 html 解釋成小於這個符號，而不是小於的 tag 。  

***

## 首頁修正  
index.php 的部分:  
```
<section>
        <?php
          while($row = $result->fetch_assoc()) {
        ?>
          <div class="card">
            <div class="card__avatar"></div>
            <div class="card__body">
                <div class="card__info">
                  <span class="card__author">
                    <?php echo escape($row['nickname']); ?> 
                  </span>
                  <span class="card__time">
					<?php echo escape($row['created_at']); ?>
                  </span>
                </div>
                <p class="card__content"><?php echo escape($row['content']); ?></p>
            </div>
          </div>
        <?php } ?>

      </section>
```
- 把內容跳脫後再顯示出來，就可以讓 script 被當作"文字"。 
```
<p class="card__content"><?php echo escape($row['content']); ?></p>

``` 
- 暱稱和建立時間也要跳脫，不然也會有 XSS 風險。
- 只要是使用者可以控制的地方都要注意到。    

***

## 共用檔案修正  
utils.php 檔案:  
```
<?php
  require_once("conn.php");

  function generateToken() {
    $s = '';
    for($i=1; $i<=16; $i++) {
      $s .= chr(rand(65,90));
    }
    return $s;
  }

  function getUserFromUsername($username) {
    global $conn;
    $sql = sprintf(
      "select * from users where username = '%s'",
      $username
    );
    $result = $conn->query($sql);
    $row = $result->fetch_assoc();
    return $row; // username, id, nickname
  }
  
  function escape($str) {
    return htmlspecialchars($str, ENT_QUOTES); // 跳脫(傳一個字串進來)，透過這個函式的結果傳回去，成為安全的字串
  }
?>
```
- 不是在資料庫存的內容就是跳脫 `escape()` 。  
- 推薦在顯示的時候做，因為這份資料可能不只有網頁要用，可能手機 APP 也要用。  
- 應保持使用者輸入的內容，因跳脫完後如果直接存到資料庫，iOS 和 Android 會看不懂。  

***
參考資料: 
[防止 XSS 攻擊](https://tech.meituan.com/2018/09/27/fe-security.html)  

[PHP ： htmlspecialchars - PHP學習誌 - Google Sites](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwj2we7-r7LtAhUkxosBHfgwA6QQFjAAegQIBRAC&url=https%3A%2F%2Fsites.google.com%2Fsite%2Fphplearnmark%2Fphp%2Fphp-zhi-ling-qing-dan%2Fzi-chuan-han-shi%2Fphp-htmlspecialchars&usg=AOvVaw1XblrxcteAUbc_kqZLfaES)  

[htmlspecialchars - Manual - PHP](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwj2we7-r7LtAhUkxosBHfgwA6QQFjABegQIAxAC&url=https%3A%2F%2Fwww.php.net%2Fmanual%2Fen%2Ffunction.htmlspecialchars.php&usg=AOvVaw3jpM0KWdqpgH51-E5nzOsB)  

[PHP htmlspecialchars 函數功能與用法- 網頁設計教學站](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwj2we7-r7LtAhUkxosBHfgwA6QQFjACegQIARAC&url=https%3A%2F%2Fwww.webtech.tw%2Finfo.php%3Ftid%3DPHP_htmlspecialchars_%25E5%2587%25BD%25E6%2595%25B8%25E5%258A%259F%25E8%2583%25BD%25E8%2588%2587%25E7%2594%25A8%25E6%25B3%2595&usg=AOvVaw0C7fTp2c0PKP9HZItTcF0t)  

[PHP htmlspecialchars() 函數 - HTML Tutorial](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwj2we7-r7LtAhUkxosBHfgwA6QQFjAEegQIAhAC&url=http%3A%2F%2Fwww.w3big.com%2Fzh-TW%2Fphp%2Ffunc-string-htmlspecialchars.html&usg=AOvVaw09YkhqVcCJ1AJ9SalcpZCh)  



