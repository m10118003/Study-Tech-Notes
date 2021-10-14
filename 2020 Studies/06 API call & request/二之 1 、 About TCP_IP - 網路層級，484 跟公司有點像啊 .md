# 二之 1 、  About TCP/IP  - 網路層級，484 跟公司有點像啊 ?  
###### tags: `NET101` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

---  

## 網路層級 ?  

- 由國際化標準組織 (ISO) 針對網路架構的規範標準。  

可參考 OSI 模型，共有七層 (Layer 7)，每一層都負責不同的事情，例如實體層:  

- 實體網路: 從電腦傳 request 到 server 有很多層，從海底電纜到中華電信怎麼接網路到用戶，用戶怎麼透過數據機連接到網路...等等。  

## TCP/IP 四層  

由於七層架構比較規模且複雜，目前提到網路相關的部分，則由 TCP/IP 四層:

- 應用層（application layer）， 例如 HTTP 、 FTP 、 DNS ... 等。
- 傳輸層（transport layer）， 例如 TCP 、 UDP 、 RTP 和 SCTP ...等。
- 網路層（internet layer）， 如 IP 。
- 鍵結層（network access layer） ， 如 Ethernet 和 Wi-Fi ... 等。 

## OSI 與 TCP/IP
參考鳥哥的 Linux 私房菜 的比較圖:
![](https://i.imgur.com/X7q9zQV.png)

- 目前網路主流是右邊的 TCP/IP ，  TCP/IP 模型是透過簡化 OSI 而來。
- HTTP 建立在 TCP 之上，而 TCP 建立在 IP (Internet Protocol) 之上，一層一層的關係。
- 協議是有分層的，分層好處是每層管每層級的事情。

---  

參考資料:

[鳥哥的 Linux 私房菜--基礎網路概念 OSI 七層協定](http://linux.vbird.org/linux_server/0110network_basic.php#whatisnetwork_osi)

[[網絡必學]TCP/IP四層模型講解【筆記整理通俗易懂版】](https://www.itread01.com/content/1543134037.html)

[ 什麼是OSI的7層架構？和常聽到的Layer 7有關？ ](https://ithelp.ithome.com.tw/articles/10000021)

[ TCP/IP通訊協定及網路架構研析 ](http://www.nex1.com.tw/old_version/document/paper17.htm)

[ OSI七層與TCP/IP四層 ](https://sites.google.com/site/archerdevil/home/networking/osi-qi-ceng-yutcp-ip-si-ceng)

---

# 二之 2 、  About TCP/IP  - IP address  
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

IP (Internet Protocol) ， 網路上的地址。  
- IPV4 (Internet Protocol version 4) ， 第四版網際網路協定 ， IPV4 用戶只能連 IPV4 網站。  
- IPV6 (Internet Protocol version 6) ， 第六版， IPV4 和 IPV6 不互通，各連各的。  

主要是為了解決 IP 地址不夠用的問題，且 IPV6 可以讓每人得到 100萬個 IP 位址，也較安全。  

---  
參考資料:  

[鳥哥的 Linux 私房菜--基礎網路概念 IP 封包的封裝](http://linux.vbird.org/linux_server/0110network_basic.php#tcpip_network)  
 
[認識IPv4與IPv6的差異](https://www.ithome.com.tw/tech/92046)  

---

# 二之 2 、  About TCP/IP  - various of IP address 你的名字  
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

---

## various of IP address:  

1. 固定 IP ， 理想狀況是一個人一 IP 位址，例如: server 設定的 DNS 連到這個 Domain Name 。  
2. 浮動 IP ， 每次連線的 IP 位址都不一樣，例如一般用戶、電信方面有好處。  
3. 虛擬 IP ， 很多時候根本不需要 IP ， 例如玩線上遊戲之類的。  

## 虛擬 IP 像是變色龍:
- 虛擬 IP 有內網，例如住戶有三台電腦，他們會共用一台數據機，從外面會連不到這個虛擬 IP 。  
- 虛擬 IP 可重複，像是代碼一樣，可能不同住戶的虛擬 IP 是一樣的，但其實是在不同的內網。  
- 虛擬 IP 對外連接會有固定或浮動 IP ， 一定會有一個 IP 對外連線，伺服器也是看到這個。  
- 內網透過數據機轉換連線網路伺服器; 網路伺服器看不到內網，只知數據機的固定或浮動 IP 。  
- 192.168 或是 10.0 開頭的幾乎是虛擬 IP 。  
- 虛擬 IP 好處是不用讓每台電腦連線，可以節省資源，電信商不用特別分 IP 給每台電腦，只要給數據機即可。  

---

# 二之 3 、  About TCP/IP  - Port 大船出港囉  
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

Port 連接埠，或他稱端口。

1. 一台電腦可能有很多服務對應很多 Port ， IP 後面加 ":數字"，這個 ":數字" 就是 Port 。
2. 沒有在 IP 後面加上 Port 的話，程式對應或監聽 Port 的常用預設會是:
    - HTTP 80 
    - HTTPS 443 
    - FTP  21 
3. 連接埠是為了讓在同一台電腦上的服務有所區別，自己在測試的時候，常用的有:
    - 3000
    - 4000 最常用
    - 8080 
    - 8000
4. 因為很多連接埠通常有服務在使用，因此會拿冷門、不會用到的來測試。
---

# 二之 4 、  About TCP/IP - TCP 和 UDP 同位異構體 & 三項之力  
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

__傳輸層常見的 TCP 、 UDP:__

- Transmission Control Protocol (TCP) :  
    - HTTP 和 FTP 都是建立在 TCP 上。
    - 大部分網路服務協議依賴 TCP 。
    - 可靠性高，發送資料完整。
    - 雙向傳輸，有數據封包。  

- User Datagram Protocol (UDP) :  
    - 可靠性低，常丟三落四。   
    - 傳輸速度快，適合多人遊戲、影片串流...等。   

---

__三次交握 (Three-way handshake)__  

TCP 傳送資料的機制非常複雜，簡易化如下:  
1. 發封包。  
2. 封包傳送接收與確認。  
3. 回傳確認封包。  
4. 取得最後確認。  

![](https://i.imgur.com/1u3LV8T.png)  
↑可參考 "鳥哥 Linux 私房菜介紹" 。  

參考資料:  

[鳥哥的 Linux 私房菜--基礎網路概念 TCP 的三向交握](http://linux.vbird.org/linux_server/0110network_basic.php#tcpip_transfer_tcphand)  

[TCP 與 UDP](http://www.pcnet.idv.tw/pcnet/network/network_ip_tcp.htm)  

---

# 二之 5 、  About TCP/IP - 小結  
###### tags: `NET101` `JavaScript續` `2020八月第二週` `進度筆記` `Lidemy心得` 8/12  

由上而下，碰到大多數會是應用層。

- 應用層 ， HTTP 、 FTP 協議和內容。
- 傳輸層 ， TCP/UDP ， 其 TCP 三次交握。
- 網路層 ， IP 地址 ， 固定、浮動和虛擬地址。
- 鍵結層 ， 即數據機、光纖和無線電。

---
