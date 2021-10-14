# 一、 JS 102 start - Module
###### tags: `JS102` `JavaScript續` `2020七月第五週` `進度筆記` `Lidemy心得` `7/26` `7/27`

---

## 模組(Module) / 中國稱呼模塊

如果一個系統一長串，動了某個部位可能全部的部位都要改動，因此要模組化:

![](https://i.imgur.com/aZxMqZf.png)

例如這樣，再用一個主程式套連，與一長串的系統相比在於，有沒有把功能切獨立分開來。

而 Node.js 也有一個模組像是 [OS module ](https://nodejs.org/api/os.html) 

---

使用方式:
```
var os = require('os');
```

require 表示引入 os 這個 module 。

---

`os.platform()`  :  
```
var os = require('os')

console.log(os.platform())
```
![](https://i.imgur.com/TzlA4FE.png)


會回傳作業系統核心名稱 wins : win32 ; mac : darwin 。
每個小部分都是 module 。

---

## export
啟用任何模組之前，需在有 node_modules 和 package.json 的資料夾和檔案下，且記得先 `npm init` 。
做出的 module 讓他人使用，例如:

![](https://i.imgur.com/2fWYAon.png)

首先必須把你的東西給輸出出去，先創造一個名為 myModule 的模組，在函式的區塊後加上這個，以函式名 printLayer 為例:
```
module.exports = printLayer
```

之後如果宣告，或是呼叫時需要的話，就可以引入 (require) 你自創的模組進來，有 `./模組名` 表示自創的模組路徑，如:

`var something = require('./myModule.js')`

透過這個規範，就可以在其他檔案呼叫自創模組。

省略掉檔案的 .js 也可以，這 module 會自動去找:

`var something = require('./myModule')`

變數名稱可以依函式所需的性質去改名比較好。

---

## 很多場合會不只輸出一個 function
啟用任何模組之前，需在有 node_modules 和 package.json 的資料夾和檔案下，且記得先 `npm init` 。

創造一個 index.js 檔案，內容為印出模組的狀況:

```
var myModule = require('./myModule')

console.log(myModule)
```


如果輸出物件 (obj):

```
function printLayer(n) {
  return n * 2
}

var obj = {
  printLayer: Layer
  printAdobe: function(n) {
    return n *3
  }
}

module.exports = obj

```

![](https://i.imgur.com/0YWSGh9.png)


輸出一個 obj 的時候，這個 module 就會是一個 obj 。
如果看不到上面的印出方式，需在有 node_modules 和 package.json 的資料夾和檔案下，且記得先 `npm init` ， 然後再輸入 node 指令。

---

可以多種混用:

```
var myModule = require('./myModule')

console.log(myModule.double(2), myModule.triple(10))
```
![](https://i.imgur.com/LgtchOd.png)

module.exports = 可以接陣列、數字或是成為函式...等都行。

實務上可能會有很多 module 混用，可以把東西集結在一起，改的時候比較好改。

![](https://i.imgur.com/sAppE2h.png)


---

## 除了 module.exports 之外的方法

有點像是內建函式 expoerts.() :  
```
function double(n) {
  return n * 2
}

var obj = {
  double: double,
  triple: function(n) {
    return n *3
  }
}

exports.double = double
```

然後也創造一個 index2.js 來看 objModule.js 的狀態:
```
var exports = require('./objModule')

console.log(exports)
```

輸出一樣也會是個有函式的物件:

![](https://i.imgur.com/3QgA1AU.png)

exports.接的東西比較是物件一類，蠻少用。
如果看不到上面的印出方式，需在有 node_modules 和 package.json 的資料夾和檔案下，且記得先 `npm init` ， 然後再輸入 node 指令。

---
