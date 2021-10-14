# 零、 遲來的第三周-有關 eslint
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/27`

ES6 是 JS 的新版標準使用語法，ALG 101 上到內建函式， Unit 5 和 6 ， Jest 跟測試有關。

---

## 零之 1 、  npm 簡介
###### tags: `JS102` `JavaScript` `2020七月第五週` `進度筆記` `Lidemy心得` `7/28`

重要的 Node Package Manager ， 管理 Node.js 程式套件(安裝 Node.js 就會附加安裝)，在 JS Node.js 的環境 CLI 用 `npm-v` 即可看到版本 : ![](https://i.imgur.com/TifYm8S.png)  

`npm init` :  會產生 package.json 檔案。

---

在 CLI 介面下安裝 `npm install mathjs` ， 會出現安裝完成:

![](https://i.imgur.com/11kNixn.png)

---

有許多相關數學套件，在 package-lock.json 檔案內會看到紀錄套件的內容(假如有安裝)，而 mathjs 會出現在 package.json 、 package-lock.json 以及 node_modules 檔案內，會從 node_modules (這不需要版本控制，純下載檔案)內引入到 library ， 檔案傳上 GitHub 時不會把 package-lock 也一併傳上去。

另一個 library `npm install loadash` 會自動幫你引入裝在 package.json 、 package-lock.json 以及 node_modules 有主目錄的檔案內，如果呼叫 lodash 的話會發現它是一個大物件，有一堆 function :

![](https://i.imgur.com/ew3rWtL.png)


```
var lodash = require('lodash')

console.log(lodash.merge)
```

如果第四周裝下去可能會影響到 GitHub 的 package.json 。

---

## 零之 2 、 提高 code 品質- eslint
###### tags: `JS102` `JavaScript` `2020七月第五週` `進度筆記` `Lidemy心得` `7/28`

eslint : es 是 ECMAScript 一種 JS 標準 ， lint 是檢查程式碼的工具; 可以透過其學習 ES6 語法、提高 code 品質，檢查語法。

而在這次第四期導師實驗課程已經裝好了，移到 mentor-program-4th-b9720012 (master) 下 ， 使用 `npm install` 會幫你安裝:

![](https://i.imgur.com/voynnp0.png)

可以到 mentor... 下的 package.json 或是 GitHub 的 mentor... 專案下的 package.json 看裡面加入了甚麼東西。

---

eslint 的 git hooks 是在 git 之前會幫你執行一些 function ， 確定有檢查通過才會 commit ， 在 hw 的地方會有 precommit ， 然後 Running linters 檢查檔案，有沒有宣告變數、少了括號，或是統一的 coding style ...等，如果有錯誤就看訊息更正，然後再 commit ，如果要停用 eslint 就可以在 code 前面加入: 
```
/* eslint-disable no-unused-vars */
```

以及把不想要的規則給停掉，還有這個:

```
// eslint-disable-next-line
```
__真的不行的時候再用，一開始不熟可以熟悉規則。__

---

可以從 package.json 檔案內看到檢查範圍是啥:
![](https://i.imgur.com/nIDLco7.png)

例如 hw 底下所有的 .js 檔案都會被檢查到。

warning 就不用修， error 就看錯誤訊息來修，從最後面行號修到前面，確保行號不會變，如果修到行號有改變就再 commit 一次來看錯誤訊息，例如宣告物件後加一個 , 加一個新的屬性比較容易。

修過語法後丟到 LIOJ 應該也是可以過。

---

參考資料:

[Airbnb JavaScript Style Guide() {一份彙整了在 JavasScript 中被普遍使用的風格指南。](https://github.com/jigsawye/javascript)

[[筆記] ESLint 學習筆記](https://pjchender.github.io/2017/09/26/%E7%AD%86%E8%A8%98-eslint-%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/)

[[JS] 使用 ESLint 提高程式碼品質](https://larrylu.blog/improve-code-quality-using-eslint-742cf1f384f1)

[Eslint 筆記](https://vagrantpi.github.io/2017/08/03/eslint/)

[ESlint 的使用隨手筆記](https://medium.com/@hugh_Program_learning_diary_Js/eslint-%E7%9A%84%E4%BD%BF%E7%94%A8%E9%9A%A8%E6%89%8B%E7%AD%86%E8%A8%98-73ae8938fa01)