#  JS 補充 、 function 額外補充 - 1
###### tags: `JS102` `JavaScript續` `2020八月第二周` `進度筆記` `Lidemy心得` 08/22

---

# 1. 定義一個 function
後面傳進去並定義一個 function:  
```
function a() {

}
console.log(a)
```

- 有一個變數是 a 而它是 function :  
```
function a() {

}

var a = function() {

}
console.log(a)
```
- 會印出 [Function: a] 。  
- 這個 function 的名稱即是 a ， 但印出函式並沒有甚麼用，並沒有執行結果。  

---

# 2. 呼叫 function   
結尾的值會回傳到開頭的函式，一定要加 () :  
```
function a() {
  console.log('呼叫 A')
  return 'A'
}

a()
```
---

# 3. 值會自動補位  
如果結尾傳數字到開頭，然後 console.log 也有印數字:
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}
a(123)
```
- 會印出: 呼叫 A 123 。 

---

# 4. function 接收參數是按照順序
如果你傳兩個值，會優先以第一個值:  
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}
a(123, 124)
```
傳數字進去，第一個數字會對應到 number ; 但如果有 number 2 在第一行函式內，第二個參數就會被傳進去。  
- 類似自己定義變數名稱，因此傳陣列、字串也行，但只會接受第一個傳進去的值，只照順序。  

---

# 5. 不同 function 間還是要設定回傳值
例如:
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main () {
  a()
}

```
- 沒有分別傳值到分別的函式開頭，所以不會印出東西。  

但如果傳值到第二個函式內的 a() ， 它會幫你傳到第一個函式的 a() :  
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main() {
  a(123)
}

main()
```
- 如果第二個函式的 a(123) ， 沒有傳值則是 undefined 。  

# 6. 呼叫完後可以再回傳值
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main() {
  var result = a(123)
  console.log(result)
}

main()
```
- 把回傳值印出來會發現印出 A 。  
- 執行順序為先執行最尾的 main() ， 然後再回傳到第二個函式的開頭 main() 。  
- 接著往下執行 `var result = a(123)` 把值往上傳到第一個函式 a() ， 然後印出。  
- 接著第一個函式內 'A' 被回傳到 a(123) ， 因此第二個函式的 result 印出 A 。  

---

# 7. 也可以把宣告省略:
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main() {
  console.log(a(123))
}

main()
```
結果跟上式一樣，會印出:  
呼叫 A 123
A

---

# 8. function 可以被傳遞:
```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main(arg) {
  console.log(arg)  // console.log(arg === a) 
}

main(a)
```
- 印出 [Function: a] 。  
- fumction 像是變數一樣可以被傳遞。  

完全等於 a() :  

```
function a(number) {
  console.log('呼叫 A', number)
  return 'A'
}

function main(arg) {
  arg(123) // a()
}

main(a)
```
- 印出: 呼叫 A 123 。
- 因為最後把 a 這個 function 當作參數傳進去; 最後的 main() 內要傳東西，不然會傳空的東西進去。  

# 9. 傳 function 的用法
看值是不是正數:  

```
function isPositive(n) {
  if (n > 0) {
    return true
  } else {  // else 拿掉也沒關係;
    return false
  }
}

console.log(isPositive(1))
console.log(isPositive(-1))

function isValid(number) {

}
```
- 印出 true false 。  
簡化用法:  

```
function isPositive(n) {
  return n > 0
}

console.log(isPositive(1))
console.log(isPositive(-1))

function isValid(number) {

}
```
- 一樣印出 true false 。  

# 10.值從後面傳回來判斷

```
function isPositive(n) {
  return n > 0
}

function isValid(number) {
  console.log('isValid')
  console.log(isPositive(number))
}

isValid(100)
```
- 印出:
isValid
true

- `isValid(100)` 傳入 `isValid(number)` ， 接著印出字串 isValid 。  
- `console.log(isPositive(number))` 往上傳到 `function isPositive(n)` 做判斷並印出。  

---