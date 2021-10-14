# 四之 6、 JS 102 ES6 更新：箭頭函式 arrow Function  
###### tags: `JS102` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/4

[箭頭函式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions) 可以省略 function 的做法，可以提高閱讀性。  

---
與一般函式相比:
```
function test(n) {
  return n
}

const test = (n) => {
  return n 
}
```

只有一個參數連 ( ) 都能省略:
```
const test = n => {
  return n 
}
```

## 好處在哪 ?
```
var arr = [1, 2, 3, 4, 5]
console.log(
  arr
    .filter(function(value) {
      return value > 1
    })
    .map(function(value) {
      return value * 2
    })
)
```
會印出 [ 4, 6, 8, 10 ] ， 過濾掉 1 ， 然後將每個值 * 2 。  

但有了箭頭函式會省很多工:  
```
var arr = [1, 2, 3, 4, 5]
console.log(
  arr
    .filter(value => {
      return value > 1
    })
    .map(value => {
      return value * 2
    })
)
```
印出 [ 4, 6, 8, 10 ]  

還可以更省略:  
```
var arr = [1, 2, 3, 4, 5]
console.log(
  arr
    .filter(value => value > 1)
    .map(value => value * 2)
)
```
印出 [ 4, 6, 8, 10 ] 。   

可讀性變得更高，連區塊都省略。  
被稱作語法糖，包裝了很多東西，如果要函式做很多事情:
```
 .filter(value => {
   ...
   .
   .
   .
   
      return value > 1
    })
```
就可能這樣做比較好，才不會太過精簡。

跟 `this` 也有關。

---
參考資料:  

[鐵人賽：箭頭函式 (Arrow functions)
](https://wcc723.github.io/javascript/2017/12/21/javascript-es6-arrow-function/)

[[筆記] JavaScript ES6 中的箭頭函數（arrow function）及對 this 的影響](https://pjchender.blogspot.com/2017/01/es6-arrow-function.html)

[箭頭函式](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/arrow_function.html)

---


# 四之 7、 JS 102 ES6 Babel 新舊相容
###### tags: `JS102` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/7

Babel 的安裝說明：https://babeljs.io/docs/en/next/babel-node.html


是重要的開發工具，如果想要用某物，但其支援度很少，開發工具將現在新的語法轉乘舊式語法，或是可以支援舊的瀏覽器，前端發展速度很快。

---

## 用法: `npx babel-node`

`npx babel-node` 的用法: 

可以執行更新的指令，用在生產上會造成記憶體大量負擔，通常會用在開發。

先在有 npm 或是 yarn 的基礎下安裝，安裝的資料夾中要含有 node_modules 資料夾，以及 package.json 檔案; 官方網站以 npm 安裝為基準，因此先以 npm 指令安裝 `npm install --save-dev @babel/core @babel/node @babel/preset-env` 。  
有 @babel/preset-env 才能執行新的含 ES6 或以上語法，把多新的語法換成多舊的語法。

好了後新增一個空白檔案 .babelrc 檔案，內容為:
```
{

 "presets": ["@babel/preset-env"]

}
```
填入內容後，是在告訴 babel 要用這個 preset ， 沒有這個檔案也會跑不了 。


最後使用 `npx babel-node index.js` 指令下去跑即可 (記得也要有模組檔案，以下範例都是以 utils.js 檔案為例)。

---

# 四之 8、 JS 102 ES6 更新：導入和導出，進出口貿易會有順差 
###### tags: `JS102` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/5

ES6 導入和導出 (import and export) 

ES6 Export 有幾種方式：

    export function add(){}，使用 import {add} 引入
    export { add }，與上面那種一樣
    export default function add()，使用 import add 引入，不需要加大括號

如果想要用其他名字，可以用 as 取別名，例如說 export { add as addFunction }

可以用 import * as utils from 'utils' 把全部都 import 進來。

---
最基本的 export 在欲導出的檔案 (以 utils.js 檔案為例) ， function 前面加 utils :  
```
export function add(a, b) {
  return a + b
}

export const PI = 3.1415
```
然後在 index.js 檔案這樣寫:
```
/*
var add = require('./utils')

console.log(add(3, 5))
*/

import {add, PI} from './utils'

console.log(add(3, 5))
```
會發現加入 import 更動了，且不用宣告。  
但這樣印不出來，需要用 Babel `npx babel-node import.js` 指令來跑的話會印出 8 。

---

## export {} 變形
```
export function add(a, b) {
  return a + b
}

const PI = 3.1415

export {
  add as addFunction,
  PI
}
```
會印出 8 3.1415 ， export { } 不是物件，要印出別的名稱;  

utils.js 檔案必須改成:

```
export function add(a, b) {
  return a + b
}

const PI = 3.1415

export {
  add as addFunction,
  PI
}
```

index.js 檔案內則是:
```
import {addFunction, PI} from './utils'

console.log(addFunction(3, 5), PI)
```

---

## import * as 

可以把所有東西導入進來:  
utils.js 修改成:
```
export function add(a, b) {
  return a + b
}

const PI = 3.1415

export {
  add as addFunction,
  PI
}
```
在 index.js 檔案內則是:
```
import * as utils from'./utils'

console.log(utils.addFunction(3, 5), utils.PI)
```
會印出 8 3.1415。
``*`` 在程式語言代表所有東西。
東西多的時候可以用 `import * as utils from'./utils'` 。

---

## export default

可以在 export 時使用預設值，例如在 utils.js 檔案內:  
utils.js 檔案必須改成:

```
export default function add(a, b) {
  return a + b
}

export const PI = 3.1415
```

一旦在模組 utils.js 檔案內加入 default 後，可以在 index.js 檔案內修改:  
```
import add from'./utils'

console.log(add(3, 5))
```
會印出 8 ; 跟在用 require 有點像，差別在不用加入 { }。

如果要用到 PI :  
```
import add, {PI} from'./utils'

console.log(add(3, 5), PI)
```
會印出 8 3.1415 。  

default 也能 as :  
```
import {default as add, PI} from'./utils'

console.log(add(3, 5), PI)
```
一樣會印出 8 3.1415 。

新專案蠻常用 ES6 的導入導出。

---

# 四之 8、 JS 102 ES6 學習仍在持續
###### tags: `JS102` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/8

ES6 之後還要學習 Map, Set< Symbol ， 有必要用的時候才會用到新語法，宣告變數會比較常用，之後會比較少用到 var 。

[更多 ES6 學習使用參考](https://github.com/DrkSephy/es6-cheatsheet)

模組化的 ES6 語法還蠻常用，所以把 function 放到另外一個檔案(模組)，出事的時候可以修一個模組就好 ， npm 在專案也很重要，在 framework 或 library 就會需要引入，jest 測試也蠻適合訓練，實際開發時單元測試也很常見，之後會學到 JS 在瀏覽器的應用。

---
