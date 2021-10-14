# 八、變數相關: 從 Object 的等號理解變數
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得` `7/4`

---

## JS 能否直接比較兩個陣列、物件

    console.log ([] === [])
    console.log ([1] === [1])
    console.log ({} === {})
    console.log ({a: 1} === {a: 1})
    
    // 全部都不相等，都為 false 。
    
    var a = 30
    console.log(a === 30)
    
    // 會是 true 相等。
    
而在變數名稱的情況:

    var obj = {
    a: 1        // a (屬性) : 1 (值); 相當於定義了一個類別，冒號相當於等號，後面的是給他們賦值;
    }
    console.log(obj === {a:1})
    
    // 會是 false 不相等，變數不相等物件。
    
![](https://i.imgur.com/sLI15fI.png)
    
__在最底層，以上其實是因為當你宣告 obj = 一個物件時，他會先把物件放在電腦的記憶體位置，也就是 obj 內存的東西其實是記憶體的位置，因此他不是直接存取 a:1 ; 但在 JS 中沒有任何方法可以知道這個記憶體位置是多少，用的時候才會給。__

__就算數值一樣，但在 JS 底層其每一個物件或陣列內的數值在記憶體的位置都是新獨立的，因此也不會沿用數值，不會指向同一個東西，所以在判斷時都會是不相等。__

參考資料: [初步理解 JavaScript 底層原理](https://iter01.com/450879.html)

---

## 如何讓其相等 ? 要有同理心，站在同等立場(型態)
    
    var obj = {
        a:1    // a (屬性) : 1 (值); 相當於定義了一個類別，冒號相當於等號，後面的是給他們賦值;
    }   
    var obj2 = obj  // 宣告讓 obj 賦予 obj 2 跟其本身同樣是變數;
    console.log(obj === obj2)

    // 會是 true 物件相等物件，如果小改:

    var obj = {
        a:1    // a (屬性) : 1 (值); 相當於定義了一個類別，冒號相當於等號，後面的是給他們賦值;
    }
    var obj2 = obj
    obj2.a = 2
    console.log(obj === obj2)    
    console.log('obj', obj)
    console.log('obj2', obj2)

    // 一樣是 true 物件相等，但如果印出來會發現裡面數值改變了。
    
__其實跟記憶體位置有關 ， `var obj = {a:1}` 後寫了 `var obj2 = obj` ，但因為新宣告物件 `obj2.a = 2` 因此會指向同一記憶體位置，並存於 0x01 中:__

![](https://i.imgur.com/pRqKADj.png)

__而最後在印出前更動了變數 `obj2.a = 2` ， 因為 `obj2` 這個物件和 `obj` 物件指向同一記憶體位置，所以會更動記憶體裡面的數值:__

![](https://i.imgur.com/o90rtTZ.png)

__而如果又讓 `obj2 = {b:1}` 變成一個物件，這時候會因為新物件的產生使其存到一個新的記憶體位置，等到要用再拿:__

![](https://i.imgur.com/2bMyYFf.png)

因此 a 和 b 會不相等，是不同物件:

    var obj = {
        a:1    // a (屬性) : 1 (值); 相當於定義了一個類別，冒號相當於等號，後面的是給他們賦值;
    }
    var obj2 = obj 
    obj2.a = 2    // 這個是針對指到 "." 的值 "a" 去進行更改記憶體的屬性;
    obj2 = {b:1}  // 如果對變數給新的物件，就會指向新的物件的記憶體位置，賦予 1 給 b 。

    console.log(obj === obj2)    
    console.log('obj', obj)
    console.log('obj2', obj2)

    // 不同 obj 印出來會是 false 。

---

## JS 中陣列 [ ] 也是物件的一種
陣列 [ ] 其實也是 object 如果對他 typeof :    

    var a = []
    var b = a
    b.push(1)

    console.log('a', a)
    console.log('b', b)
    console.log(a === b)

    // 宣告變數 a 是一個陣列，而變數 b = a ，因為是同型態所以印出來會是一樣的。
    
如果穿插一個新的陣列，就會是不同的物件，在不同的記憶體位置，所以會不一樣:


    var a = []
    var b = a
    b.push(1)

    b = [1, 2, 3]

    console.log('a', a)
    console.log('b', b)
    console.log(a === b)
    
    // 因為多了一個新的物件，會存在不同記憶體位置，所以不一樣。

對物件操作時，因為存的是記憶體的位置，所以賦值要注意，可以用 console.log( ) 來作嚴格比較 === 型態。
