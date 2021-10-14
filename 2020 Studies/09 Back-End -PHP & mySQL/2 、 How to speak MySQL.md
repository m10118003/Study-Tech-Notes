# 2 、 How to speak MySQL
###### tags: `BE101` `PHP` `2020九月第四周` `進度筆記` `Lidemy心得` 

## SQL 指令 - 基本語法  
在資料庫 mentor.qoo 執行 SQL 查詢:  

### 查詢 `SELECT` 指令 : 找符合條件的資料。
- 可以用行內編輯來更改。 
```
SELECT * FROM `table 名稱` 

```

`*` 星號表示欄位名稱，可以找所有欄位，或是不用星號直接用數字，則會顯示數字。  
- 可以 `SELECT id, title` ， 如果沒有 `title` 的欄位則會顯示錯誤訊息。  

- `SELECT id as name` 可以讓欄位名稱改變，但資料內容不便。  
- `SELECT * FROM `table 名稱` WHERE id = 2` 可以查詢 id 為 2 的資料。 
- `SELECT * FROM `table 名稱` WHERE username = '查詢條件' and id = 2` 可以查詢符合 '查詢條件' 和 'id' 的資料。 
- `SELECT * FROM `table 名稱` WHERE username = '查詢條件' or id = 2` 可以查詢符合兩者中其中一方條件的資料。 
- WHERE 1 會把所有資料撈出來，後面常接 一兩筆資料條件。 
- 簡單字串操作，數學邏輯運算也可以運用在 SELECT 。 

***

### 新增 `INSERT` 指令 : 新增、插入資料。
- `INSERT INTO` : 
```
INSERT INTO `table 名稱`(`id`, `username`, `content`, `created_at`) VALUES ([value-1],[value-2],[value-3],[value-4])
```

- `()` 內是插入資料的欄位名稱；如果 `id` 預設是自動增加就可以拿掉， `created_at` 預設是現在時間點也可以拿掉。  
- `()` 內的反引號 `` 去掉也可以(大多情形下)；除非欄位名稱有特殊字元，像是叫做 `INSERT INTO`， 會造成混淆，會被解釋成 SQL 指令的一部分，造成出錯。 
- 很多 SQL 語法都會用大寫來表示，跟自訂的欄位名稱或是字串區別。 

```
INSERT INTO `table 名稱` (username, content) VALUES ("username01", "content01")
```
執行後，表示寫入一筆資料到 `table 名稱` ， 該筆資料的 `username` 是 "username01" ； `content` 是 "content01" 。

***

### 修改 `UPDATE` 指令 : 修改、編輯資料。 
```
UPDATE `table 名稱` SET `id`=[value-1], `username`=[value-2], `content`=[value-3], `created_at`=[value-4] WHERE id = 1
```
這是固定語法，

---

如果用:
```
UPDATE `table 名稱` SET username = "abc"
```
這樣會影響到所有資料(table) ， 但這種要改變所有資料的情況很少，因此要改變到指定的資料會設指定欄位: 如 ， `WHERE id=1` ， 這樣會改變 id 是 1 的單筆資料。

---

```
UPDATE `table 名稱` SET username = "user02", content = "content02" WHERE id = 2
```
這樣會改變欄位 id = 2 ， 並新增 username 為 "user02" 和 content 為 "content02" 的資料進去。 回 "瀏覽" 去看可以看到變動。   

![](https://i.imgur.com/DYbfdsp.png)  

***

### 刪除 `DELETE` 指令 : 刪除資料。 
- 指定條件，符合條件者均會被刪除。  
```
DELETE FROM `table 資料` WHERE 0  
```
執行後會出現確認畫面問你是否刪除。   

![](https://i.imgur.com/6lvrT94.png)  

這樣不會刪除資料，因為 WHERE 0 沒有符合任何資料。   

---

如果用:
```
DELETE FROM `table 資料` WHERE id = 2
```
這樣會直接把 id = 2 的欄位資料刪除。  

---

### 回溯時間
很多時候的系統內刪除，不是真正的刪除。  
- 有些訂單、會員等重要的資料是需要保留的資料。  
- 因此有時候會設一個 `is_deleted` 的欄位標籤。
- 而不是直接用 DELETE 刪除。      
- 缺點是對於資料庫的空間來說會一直佔據，檔案越來越多。  

刪除時可能會在結構新增一個欄位(型態可能為 BOOLEAN) 像這樣:  
```
id = 1 ; username = "user01"；content = "something"；is_deleted = "0"；created_at = now the time
```

在前台刪除資料的時候，可能會在後台把 `is_deleted` 設成 1 ，下的指令可能如下: 
```
SELECT * FROM `table 資料` WHERE is_deleted = 0
```
會把被刪除的資料顯示給 user 看，但對資料庫來說仍然存在(有標誌、保存 LOG)，因此誤刪的情況下還會救回來。

---