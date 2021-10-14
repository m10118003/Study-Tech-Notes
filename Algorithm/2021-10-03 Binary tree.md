# 10/03 Binary tree   
###### tags: `algorithm` `計算機概論` `data structure` `2021/10/01` `進度筆記` `前端心得`  
---

[雜湊表 Hash map - Rust Algorithm Club (rust-algo.club)](https://rust-algo.club/collections/hash_map/)   


- 資料結構: 一個整體架構去安排程式會要用到的資料, 一個連一個的就是練接串列  
- 鏈結串列: 放在記憶體中  
    - - 二元樹: 放在記憶體中, 一個連兩個的就是二元樹, 連多個的就是多元樹, 例如 B Tree      
- 多元樹: 放在硬碟上, 是常見的 database 主要結構   
- 紅黑樹: 特殊的資料用途結構, 例如交易搓合   
- 雜湊表    
- 演算法: 想像力就是你的超能力, 用抽象的方式去做程式設計   
> 是方法論, 探套程式用甚麼方法下去做, 包含要花多少時間下去解決問題, 電腦要解決問題要花多久的時間就是演算法的"複雜程度" → 數學符號表述為 `O()`  Big O,  
- 計算機概論:   
> 探討電腦能力的極限, 內含更深入的可不可以解決問題, 也包含問題要解決多久, 要花多久時間   
---

# 二元樹 (binary tree)   
# 參考資料   

[二元樹 \- 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%8F%89%E6%A0%91)   

[二元搜尋樹 \- 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%85%83%E6%90%9C%E5%B0%8B%E6%A8%B9)   

[二元搜尋樹 \- YouTube](https://www.youtube.com/watch?v=sNWmwl6OWGg&ab_channel=%E8%A8%B1%E6%99%81%E7%9D%BF)   

[演算法筆記 \- Binary Tree (ntnu.edu.tw)](https://web.ntnu.edu.tw/~algo/BinaryTree.html)   

[二元樹(Binary Tree)基礎 - 寫點科普 Kopuchat](https://kopu.chat/2017/06/18/%E4%BA%8C%E5%85%83%E6%A8%B9/)   

[資料結構 \- 二元樹(Binary Tree) @ 小殘的程式光廊 :: 痞客邦 :: (pixnet.net)](https://emn178.pixnet.net/blog/post/94164966)  

[擁抱「資料結構」的「演算法」(10) - 二元樹 Binary Tree - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10242571)   

[Tree (ntu.edu.tw)](https://www.csie.ntu.edu.tw/~r95116/CA200/slide/C10_Tree.pdf)   

[Microsoft PowerPoint - tree (takming.edu.tw)](http://wayne.cif.takming.edu.tw/datastru/tree.pdf)   

[【圖解演算法教學】【Tree】不單純的二元樹遍歷(Traversal) 入門|介紹|教學|LeetCode|資料結構 - YouTube](https://www.youtube.com/watch?v=7FpkEAYTIZI&ab_channel=%E5%9C%96%E8%A7%A3%E7%A8%8B%E5%BC%8F%E6%95%99%E5%AD%B8SamTsai)   

[引線二元樹 \- YouTube](https://www.youtube.com/watch?v=9b2GAFGZ6yw)   

[\[軟體工程師雜談\] 輕鬆搞懂資料結構: 樹(tree) |IT鐵人賽: 從零開始搞懂寫程式，資工系4年最重要的學科，資料結構，演算法，物件導向 - YouTube](https://www.youtube.com/watch?v=xDwFMffqLbw)   

[\[軟體工程師雜談\] 輕鬆搞懂演算法:搜尋(search) 二元搜尋 (Binary search) |IT鐵人賽: 從零開始搞懂寫程式，資料結構，演算法，物件導向 - YouTube](https://www.youtube.com/watch?v=llSvc4rwxi0&ab_channel=%E5%A5%AEgame%E7%8E%8B%E7%B4%AB%E6%A5%93)   

[\[軟體工程師雜談\] 輕鬆搞懂資料結構: 堆積(Heap) |IT鐵人賽: 從零開始搞懂寫程式，資工系4年最重要的學科，資料結構，演算法，物件導向 - YouTube](https://www.youtube.com/watch?v=klbGg8dmYTM&ab_channel=%E5%A5%AEgame%E7%8E%8B%E7%B4%AB%E6%A5%93)   

[\[軟體工程師雜談\] 輕鬆搞懂演算法:合併排序(merge sort) |IT鐵人賽: 從零開始搞懂寫程式，資工系4年最重要的學科，資料結構，演算法，物件導向 - YouTube](https://www.youtube.com/watch?v=C9Xes8wH6Co&ab_channel=%E5%A5%AEgame%E7%8E%8B%E7%B4%AB%E6%A5%93)   

---

# 雜湊  
# 參考資料   

[雜湊函式 \- 維基百科，自由的百科全書 (wikipedia.org)](https://zh.wikipedia.org/wiki/%E6%95%A3%E5%88%97%E5%87%BD%E6%95%B8)   

[使用雜湊程式碼確定資料完整性 | Microsoft Docs](https://docs.microsoft.com/zh-tw/dotnet/standard/security/ensuring-data-integrity-with-hash-codes)  

[Hash是什麼？5分鐘帶你了解區塊鏈雜湊相關的知識 - 區塊吧 BLOCKBAR](https://blockbar.io/blockchain/hash%E6%98%AF%E4%BB%80%E9%BA%BC-what-is-hash/)   

[hash function 觀念和實務 - HackMD](https://hackmd.io/@jkrvivian/HJln3jU_e?type=view)   

[algo.nttu.edu.tw/1071ITWWW/10711140/雜湊函數.html](http://algo.nttu.edu.tw/1071ITWWW/10711140/%E9%9B%9C%E6%B9%8A%E5%87%BD%E6%95%B8.html)   

[EP2 - 什麼是資訊安全？ - 資安解壓縮 (infosecdecompress.com)](https://infosecdecompress.com/posts/EP2-what-is-infosec)   

[雜湊表 Hash map - Rust Algorithm Club (rust-algo.club)](https://rust-algo.club/collections/hash_map/)   

[\[資料結構\] 雜湊 (Hash) - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天 (ithome.com.tw)](https://ithelp.ithome.com.tw/articles/10208884)   

[加密和雜湊有什麼不一樣？ | Just for noting (m157q.tw)](https://blog.m157q.tw/posts/2017/12/25/differences-between-encryption-and-hashing/)   

[第四章 雜湊與亂數演算法 (tsnien.idv.tw)](http://www.tsnien.idv.tw/Security_WebBook/%E7%AC%AC%E5%9B%9B%E7%AB%A0%20%E9%9B%9C%E6%B9%8A%E8%88%87%E4%BA%82%E6%95%B8%E6%BC%94%E7%AE%97%E6%B3%95.html)   

[Preprocessing Data : Hash介紹. \[Hash概念\] 很多人以為雜湊就是加密，但雜湊不是加密！ 雜湊不是加密！… | by Ryan Lu | AI反斗城 | Medium](https://medium.com/ai%E5%8F%8D%E6%96%97%E5%9F%8E/preprocessing-data-hash%E4%BB%8B%E7%B4%B9-8ade1128928c)   

[\[Security\] 雜湊不是加密，雜湊不是加密，雜湊不是加密。 | 小朱® 的技術隨手寫 - 點部落 (dotblogs.com.tw)](https://dotblogs.com.tw/regionbbs/2017/09/21/hashing_is_not_encryption)    

---

# 計算機概論   

[計算機概論 \- 臺大開放式課程 (NTU OpenCourseWare)](http://ocw.aca.ntu.edu.tw/ntu-ocw/ocw/cou/101S210/1)   

