# 二、 JS 102 NPM
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/269 

---

## Node Package Manager (NPM)

Node.js 的套件管理，可管理抓下來的 library 、 module 和 package ... 等套件。
`npm -v` 可以看版本。


[npm 小筆記](https://hackmd.io/@b9720012/H1NPCwTew)
[NPM 官方網站](https://www.npmjs.com/)
[npm 中文文档](https://www.npmjs.cn/)
[NPM是什麼？了解Node Package Manager套件管理機制](https://tw.alphacamp.co/blog/npm-node-package-manager)

---

# 二之 1、 JS 102 NPM 安裝 left-pad
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/29 

---

[left-pad 套件模組使用](https://www.npmjs.com/package/left-pad)  

left-pad 可以在文字前面加上某些字元、或是郵遞區號，[歷史緣由](https://www.inside.com.tw/article/6041-how-one-programmer-broke-the-internet-by-deleting-a-tiny-piece-of-code)。  
選個測試用的資料夾用指令 `npm install left-pad` 安裝完後，在 CLI 用 `ls`  指令觀看，會發現多了 node_modules 的資料夾，裡面有個資料夾為 left-pad 的 module ， 點開 index.js 會發現有 `module.exports = leftpad` 這行，表示 leftpad 的模組引入。  

使用方式:
```
var leftPad = require('left-pad')
  // 有些套件如果不加引用的 ''./'' ， npm 會自動去找並 require ， 不過官方的 Usage
 預設並沒有，似乎是直接索引;
console.log(leftPad(123, 10, '0'))  

```

會印出 0000000123 。

---

## 可以提供 library 的資訊給他人用

`npm install left-pad --save`

dependencies : 開發和發布後， 仍然依賴這個程式語言之 library 其所開發的供之後使用， --save 會加入到 package.json 內的 dependencies 。  
而 --save-dev 對應到 devDependencies ，只有開發的時候會用到的 library ，正式發行後不會用到，詳細參考 [弄懂 npm install 的 –save 與 –save-dev
](https://chriskang028.wordpress.com/2017/07/05/%E5%BC%84%E6%87%82-npm-install-%E7%9A%84-dependencies-v-s-devdependencies/) 。  

可以用 `npm init` 重新下載 package.json (描述專案的檔案) ， 可以在裡面看到 dependencies ， 看到專案會依賴 left-pad ， 可以看到這專案用了哪些 library 。

如果你的 npm ， node_modules 資料夾刪除了，也可以根據 package.json 的檔案內的 dependencies (前提是有安裝過其他 library 並記錄到)，用 `npm install` 指令將所有需要的 library 或是模組抓下來。

如果要放上 gitHub 記得把 node_modules 加入 .gitignore ， 因為資料夾內 library 太多。

---

# 二之 2、 JS 102 npm scripts 
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/29

---

![](https://i.imgur.com/4ljMVfg.png)

可以在 scripts 下寫一些指令，之後 npm 會自動執行  "test" 下的一連串指令。  
專案變大後，可以先在 "main" 下說最主要的檔案為何:

![](https://i.imgur.com/eQEt1AM.png)

範例為 index.js 這個檔案。

---

![](https://i.imgur.com/61HOMyl.png)


或是在 "scripts" 下寫個指令，假如跑到 start(start 可以更名) ， 輸入 `npm run start` ， npm 就會幫你執行 `node index.js` 的動作。

---

如果要執行複數指令，則要在 "scripts" 下點功夫:

```
  "scripts": {
    
	"test1": "node index.js", 
	"test2": "node index2.js",
	"serial": "node index.js && node index2.js"
	
```
例如用串聯的方式，CLI 下執行 `npm run serial` 就會同時執行兩個模組，如果看不到上面的印出方式，需在有 node_modules 和 package.json 的檔案下，且記得先 npm init ， 然後再輸入 node 指令。

[蛋頭教室 如何使用 npm script 變成你的建立工具 重點筆記](http://jamestw.logdown.com/posts/1378697-egghead-how-to-use-npm-scripts-as-your-build-tool)

---

# 二之 3、 JS 102 除 npm 外還有其他選擇 
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/29

---

## yarn

https://yarnpkg.com/

由 FB 開發比較新的 NPM ， 用 `yarn -v` 可以看到版本，用 `npm init` 指令跟啟用 npm 類似。

而是在 CLI 介面中透過指令 `yarn` 啟用:

![](https://i.imgur.com/29LZZwd.png)

---

## 用 yarn 加入套件 

跟 `npm install 套件名稱 --save` 類似，不過是使用 `yarn add 套件名稱` ， 跟使用 npm --save 一樣，不過預設是自動更新 package.json 的 dependencies 。

## yarn　也可以使用 scripts 下的指令

跟 `npm run start` (start 可以換其他名稱) 類似，`yarn run start` 。

npm 跟 yarn 選用一個或是皆可~~~

[CLI commands comparison](https://classic.yarnpkg.com/en/docs/migrating-from-npm#toc-cli-commands-comparison)

----
