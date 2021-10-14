# 五、 JS 最直覺的變數型態: 物件(object)
###### tags: `JavaScript` `JS101` `2020六月第五週` `進度筆記` `Lidemy心得`

---

## 以儲存學生分數和姓名為例

用一個陣列 [  ] 可以存相似資料，分開分數和姓名:

    var student_names =  ['a', 'b', 'c']
    var student_scores = [100, 30, 50]...
    
    // 這樣就可以存多筆資料，但如果多新增了地址:
    
    var student_address = ['ewew', '忠孝東路走九遍', 'woowowow']
    
    student_names[0]
    student_scores[0]
    student_address[0]
    
    // 但這樣存取會很不方便，如果有個資料結構可以存取所有的變數和元素，就是 "物件" (objest)，以大括號 { key: 'value' } ， "key" 為變數， "value" 為元素表示:
    
    var students = []
    {
    name: 'SpiderMan'
    score: 100,
    address: 'NewYork City',
    phone: "010101010"
    } 
    
這樣的物件資料結構就可以代表學生的屬性，也可以與陣列一起使用。

key: 為屬性的名稱，任何字串都可以作為 key，陣列 (array) 是一個很好的範例。
value: 在元素 (value) 中可放入任何型別的值，當然也包括物件。

[參考來源: JavaScript - 物件 與 屬性](https://ithelp.ithome.com.tw/articles/10193605)

實際做法，宣告一個變數，並將物件內的變數和元素賦予給他:

    var spiderMan = {
      name: 'spiderMan',
      score: 100,
      address: 'NewYork City',
      phone: "010101010"
    }
    
    console.log(spiderMan)    

會印出:    
![](https://i.imgur.com/ZKQLWX4.png)

`console.log(typeof spiderMan)` 則會顯示 object 。 

---

## 陣列可以跟物件合併使用
如果陣列跟物件用在一起就會是:
    
    var students = []
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的元素要記得用逗點 , 隔開;
      score: 100,
      address: 'NewYork City',
      phone: "010101010"
    }
    
    students.push(spiderMan)
    console.log(students[0].name)  
    
    // 這個會印出 name ; 
    
如 ， [0].name ; [ ]後可以接 { }內的變數及元素，像是 .score 、 .address 、 .phone ...等;
如不混用，只用物件的話就去掉 push 只接 console.log(spiderMan.name) 。
   
    var students = []
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的變數和元素要記得用逗點 , 隔開;
      score: 100,
      address: 'NewYork City',
      phone: "010101010"
    }
    
    students.push(spiderMan)
    console.log(students['name', 'score', 'address', 'phone'])  
    
    // 這個會 undefined 。
  
---

## 宣告要有值

.name 、 .score 這種變數 (key) 如果以 .name.key 會 undefined，因為 spiderMan 沒有宣告變數 (key) ， 因此可以用中括號 宣告(var)['變數'] ， 因此如變數內有存值的話:

    var students = []
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的元素要記得用逗點 , 隔開;
      score: 100,
      address: 'NewYork City',
      phone: "010101010"
    }
    var key = 'name'
    console.log(spiderMan[key])
    
    //會印出 spderMan 

而物件內是可以放很多東西的，如 "陣列" :
      
    var students = []
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的元素要記得用逗點 , 隔開;
      scores: [1, 2, 3],
      address: 'NewYork City',
      phone: "010101010"
    }
    var key = 'scores'           // 可以置換成 var key = 'name' 但下行要用:
    console.log(spiderMan[key])  // 跟上行合用置換成 console.log(spiderMan.scores) ;
    
    // 會印出 [1, 2, 3] 。
    
# 物件內可以塞很多東西

物件內可以塞物件 ， function 也行:

    var students = []
    
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的元素要記得用逗點 , 隔開;
      scores: [1, 2, 3],
      address: 'NewYork City',
      phone: "010101010",        // {  } 內的物件也要記得用逗點 , 隔開;
      father: {
        name: 'nick',
        phone:'12345'
      }
    }
    var key = 'scores'           // 可以置換成 var key = 'name' 或其他元素，但主要是下行宣告要用:
    console.log(spiderMan.father.name)  // 跟上行合用，但以這行宣告為準 console.log(spiderMan.father.name) ; 還可以置換成 console.log(spiderMan['father']['name'])
    
    // 會印出蜘蛛人他老爸名字。
    
    var students = []
    
    var spiderMan = {
      name: 'spiderMan',         // {  } 內的元素要記得用逗點 , 隔開;
      scores: [1, 2, 3],
      address: 'NewYork City',
      phone: "010101010",        // {  } 內的物件也要記得用逗點 , 隔開;
      father: {
        name: 'nick',
        phone:"12345"
      }
    }
    var key = 'name'           // 可以置換成 var key = 'name' 但下行要用:
    console.log(spiderMan['father'])
    
    // 會印出蜘蛛人他老爸的名字和手機。