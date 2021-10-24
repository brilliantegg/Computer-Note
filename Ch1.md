# Appilication Layer

應用層一些常用的protocol:
- URL (uniform resource locator)
- HTTP
- TCP (reliable connection)(layer 4)

一個URL request需要17個messages:
- 6(to find server IP address) + 3(TCP 3 way handshake) + 4(HTTP request & acknowledge) + 4(TCP to end connection)

message: 要傳送的請求，通常會再被切分成多個packet(smaller size)去傳送

packet如何被傳送? Store(先被router儲存) and forward(然後再轉送出去)
