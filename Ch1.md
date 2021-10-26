應用層(Appilication Layer)一些常用的protocol:
- URL (uniform resource locator)
- HTTP
- TCP (reliable connection)(layer 4)

一個URL request需要17個messages:
- 6(to find server IP address) + 3(TCP 3 way handshake) + 4(HTTP request & acknowledge) + 4(TCP to end connection)

message: 要傳送的請求，通常會再被切分成多個packet(smaller size)去傳送

packet如何被傳送? Store(先被router儲存) and forward(然後再轉送出去)

注意在internet中，packet的路徑會有變化。網路當下的狀態會影響packet的傳送路徑(由router決定)

如果packet太大(不符網路本身限制)，也會被router切成獨立的小packet再傳送，但是傳送的順序跟路徑也不盡然相同

*另外就是，internet本身是不可靠的，packet傳送途中若是遇到阻塞，有可能會掉封包，需要另外有重送機制去保證資料能夠完整送達(ex:tcp的重送機制)

switch(網路交換機)有實作在L2,L3,L4,L5的版本

spanning tree: 生成樹，可以想成是packet在switch中旅行的路徑

封包對象?
- unicast: 封包只傳送給一個接收者
- multicast: 封包傳送給多個接受者
- broadcast: 封包傳送給範圍內"所有"接受者 (通常只在區網內，會被router擋下來)

網路大小比較: WAN > MAN > LAN

---
Resource: Links & Nodes

共享Link:
- multiplexing: 多個來源，導向至同個link
- de-multiplexing: 將同個來源的資料分流(與上方相反)
