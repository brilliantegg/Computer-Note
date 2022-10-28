# 與加密函式庫相關的應用程式集區設定問題

### 問題描述
在本地端使用加密函式庫功能(System.Security.Cryptography.CngKey.Import)時沒有遇到任何問題，但是在其他Server環境上會遇到錯誤，內容為：**System.Security.Cryptography.CryptographicException: System cannot find specified file.**

### 問題原因
This is most likely because the Windows Cryptographic Service Provider was trying to store or load a key for your certificate in the user store, and since a profile was not available, a cryptographic context was not available. Note that the Load User Profile setting only applies to user accounts. Service Accounts like NETWORK SERVICE and ApplicationPoolIdentity have special handling. 
(參考資料來源：[What exactly happens when I set LoadUserProfile of IIS pool?](https://https://stackoverflow.com/questions/17149132/what-exactly-happens-when-i-set-loaduserprofile-of-iis-pool))

### 解決方式
設定當前使用的Application Pool內的Load User Profile選項為True，即可正常運行

### 參考資料
[CryptographicException was unhandled: System cannot find the specified file](https://stackoverflow.com/questions/17840825/cryptographicexception-was-unhandled-system-cannot-find-the-specified-file)

[X509Certificate Constructor Exception](https://stackoverflow.com/questions/9951729/x509certificate-constructor-exception/10048789#10048789)

[What exactly happens when I set LoadUserProfile of IIS pool?](https://https://stackoverflow.com/questions/17149132/what-exactly-happens-when-i-set-loaduserprofile-of-iis-pool)
