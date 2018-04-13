# IoT Security TOP 10 物聯網十大安全測試
物聯網十大安全測試目標是幫助測試人員評估物聯網空間中的物聯網設備和應用程序。下面列出10項基本測試。但這不是全部的事項，但確保涵蓋這些基本原則將大大提高任何物聯網產品的安全性
## I1. Insecure Web Interface 不安全的網頁介面
> 其實也就是一般最常見的Web安全，任何網站在實作上可能產生的漏洞(SQLi, XSS, CSRF…)都在這個範疇，可參考OWASP Top 10。

- Assess any web interface to determine if weak passwords are allowed
- Assess the account lockout mechanism
- Assess the web interface for XSS, SQLi and CSRF vulnerabilities and other web application vulnerabilities
- Assess the use of HTTPS to protect transmitted information
- Assess the ability to change the username and password
- Determine if web application firewalls are used to protect web interfaces

## I2. Insufficient Authentication/Authorization 認證/授權不足
> 任何需要存取的動作，都需要去確認認證與授權是否合法。那麼在IoT中要去哪裡檢查認證與授權呢？答案是找出整個IoT架構中所有的介面(Interface)，無論是雲端提供介面給設備傳遞資料過去，或者是使用者透過行動裝置連至雲端提供的行動介面存取資料。建議做法如啟用雙因子認證、當使用到一些比較敏感的功能可以進行重新認證、確保發給client的認證token/session key保持不一樣等。

- Assess the solution for the use of strong passwords where authentication is needed
- Assess the solution for multi-user environments and ensure it includes functionality for role separation
- Assess the solution for Implementation two-factor authentication where possible
- Assess password recovery mechanisms
- Assess the solution for the option to require strong passwords
- Assess the solution for the option to force password expiration after a specific period
- Assess the solution for the option to change the default username and password

## I3. Insecure Network Services 不安全的網路服務
> 若物聯網裝置有不安全的網路服務公開在Local或Global Network，可能會導致Buffer Overflow或DoS的問題，可以利用自動化工具如Port Scanner或Fuzzer。

- Assess the solution to ensure network services don't respond poorly to buffer overflow, fuzzing or denial of service attacks
- Assess the solution to ensure test ports are are not present

## I4. Lack of Transport Encryption 缺少傳輸加密
> 物聯網資料間的傳輸，無論是有線或無線的都可能使用各式各樣的協定或技術(BLE, TLS, RFID, NFC…)。這些協定或技術在傳輸時是否會進行加密其實也不一定，需要去了解這些協定的實作。
- Assess the solution to determine the use of encrypted communication between devices and between devices and the internet
- Assess the solution to determine if accepted encryption practices are used and if proprietary protocols are avoided
- Assess the solution to determine if a firewall option available is available

## I5. Privacy Concerns 隱私問題
> 這個部分舉例來說，當使用者在設定或啟用物聯網裝置時，可以去檢查看看裝置所蒐集的資料。裝置是建議最好不要蒐集敏感性資料，要儲存的話可將資料去識別化或匿名後再儲存。

- Assess the solution to determine the amount of personal information collected
- Assess the solution to determine if collected personal data is properly protected using encryption at rest and in transit
- Assess the solution to determine if Ensuring data is de-identified or anonymized
- Assess the solution to ensure end-users are given a choice for data collected beyond what is needed for proper operation of the device

## I6. Insecure Cloud Interface 不安全的雲端介面
> 關於雲端介面的安全性，OWASP也有Cloud Top 10，不過這Top 10會包含整個雲的安全性問題，但這邊主要著重在提供給使用者/管理者的雲端介面安全。

- Assess the cloud interfaces for security vulnerabilities (e.g. API interfaces and cloud-based web interfaces)
- Assess the cloud-based web interface to ensure it disallows weak passwords
- Assess the cloud-based web interface to ensure it includes an account lockout mechanism
- Assess the cloud-based web interface to determine if two-factor authentication is used
- Assess any cloud interfaces for XSS, SQLi and CSRF vulnerabilities and other vulnerabilities
- Assess all cloud interfaces to ensure transport encryption is used
- Assess the cloud interfaces to determine if the option to require strong passwords is available
- Assess the cloud interfaces to determine if the option to force password expiration after a specific period is available
- Assess the cloud interfaces to determine if the option to change the default username and password is available

## I7: Insecure Mobile Interface 不安全的行動介面
> 關於行動介面的安全性，OWASP也提出了Mobile Top 10可以參考。基本上不外乎提供給使用者操作的行動介面證機制是否安全完善、資料傳輸時是否安全、連續登入失敗帳號是否鎖定、密碼復原機制是否有漏洞、APP是否有進行混淆或防竄改機制等。

- Assess the mobile interface to ensure it disallows weak passwords
- Assess the mobile interface to ensure it includes an account lockout mechanism
- Assess the mobile interface to determine if it Implements two-factor authentication (e.g Apple's Touch ID)
- Assess the mobile interface to determine if it uses transport encryption
- Assess the mobile interface to determine if the option to require strong passwords is available
- Assess the mobile interface to determine if the option to force password expiration after a specific period is available
- Assess the mobile interface to determine if the option to change the default username and password is available
- Assess the mobile interface to determine the amount of personal information collected

## I8. Insufficient Security Configurability 安全配置性不足
> 主要講得是物聯網裝置的安全設定，例如有些設備可能提供可以設定密碼的功能，但卻沒強制一定要輸入”強”密碼，這是一種安全性設定的不足；又或者傳輸中的或儲存在設備上的敏感資料未加密也是一種。另外也建議IoT設備可以對於安全事件做紀錄或通知使用者。

- Assess the solution to determine if password security options (e.g. Enabling 20 character passwords or enabling two-factor authentication) are available
- Assess the solution to determine if encryption options (e.g. Enabling AES-256 where AES-128 is the default setting) are available
- Assess the solution to determine if logging for security events is available
- Assess the solution to determine if alerts and notifications to the user for security events are available

## I9. Insecure Software/Firmware 不安全的軟體與韌體
> 此部分主要鎖定在IoT設備軟體/韌體更新的安全性。若設備具有自動更新功能時，除了更新伺服器的安全外，更新檔傳輸時(是否使用加密通道)以及更新檔本身的安全性(檔案是否加密、是否簽章並在傳遞/安裝前驗證過)都很重要。

- Assess the device to ensure it includes update capability and can be updated quickly when vulnerabilities are discovered
- Assess the device to ensure it uses encrypted update files and that the files are transmitted using encryption
- Assess the device to ensure is uses signed files and then validates that file before installation

## I10. Poor Physical Security 實體安全考量不足
> 考量到物聯網裝置的實體安全，例如裝置是否有可卸除式儲存設備如SD Card能輕易移除，若裡面的資料又未加密則可能遭到竊取或竄改；又或者有些物聯網設備可能會透過USB Port進行軟體更新，此USB Port若未受控制，也可能被利用於修改設備軟體或拿來複製資料。

- Assess the device to ensure it utilizes a minimal number of physical external ports (e.g. USB ports) on the device
- Assess the device to determine if it can be accessed via unintended methods such as through an unnecessary USB port
- Assess the device to determine if it allows for disabling of unused physical ports such as USB
- Assess the device to determine if it includes the ability to limit administrative capabilities to a local interface only

