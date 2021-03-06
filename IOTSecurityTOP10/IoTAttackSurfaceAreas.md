# IoT Attack Surface Areas 物聯網攻擊面向
> 物聯網的發展面向會更廣，尤其是當裝置感測器更多元，系統彼此間更開放互連，並能與各式應用服務相結合，攻擊面向也將更廣。
常見的攻擊像網路攻擊行為，通常就是電腦中毒、資料竊取、網站被入侵等，在物聯發展浪潮之下，現在攻擊重心開始擴散至各式連網系統與裝置，受到攻擊與濫用的比例已有明顯的增加趨勢。以往在電腦、智慧型手機上才有的隱私保護、資訊安全問題，也成為更多連網設備與系統同樣需要面對的事。
>
> 
## Ecosystem Access Control 生態系統訪問控制
- Implicit trust between components
- Enrollment security
- Decommissioning system
- Lost access procedures
## Device Memory 設備的記憶體
- Cleartext usernames
- Cleartext passwords
- Third-party credentials
- Encryption keys
## Device Physical Interfaces 設備的實體存取介面
- Firmware extraction
- User CLI
- Admin CLI
- Privilege escalation
- Reset to insecure state
- Removal of storage media
## Device Web Interface 設備的網頁介面
- SQL injection
- Cross-site scripting
- Cross-site Request Forgery
- Username enumeration
- Weak passwords
- Account lockout
- Known default credentials
## Device Firmware 設備的韌體
- Hardcoded credentials
- Sensitive information disclosure
- Sensitive URL disclosure
- Encryption keys
- Firmware version display and/or last update date
## Device Network Services 設備的網路服務
- Information disclosure
- User CLI
- Administrative CLI
- Injection
- Denial of Service
- Unencrypted Services
- Poorly implemented encryption
- Test/Development Services
- Buffer Overflow
- UPnP
- Vulnerable UDP Services
- DoS
## Administrative Interface 管理介面
- SQL injection
- Cross-site scripting
- Cross-site Request Forgery
- Username enumeration
- Weak passwords
- Account lockout
- Known default credentials
- Security/encryption options
- Logging options
- Two-factor authentication
- Inability to wipe device
## Local Data Storage 本地資料儲存
- Unencrypted data
- Data encrypted with discovered keys
- Lack of data integrity checks
## Cloud Web Interface 雲端網頁介面
- SQL injection
- Cross-site scripting
- Cross-site Request Forgery
- Username enumeration
- Weak passwords
- Account lockout
- Known default credentials
- Transport encryption
- Insecure password recovery mechanism
- Two-factor authentication
## Third-party Backend APIs 第三方的後端API
- Unencrypted PII sent
- Encrypted PII sent
- Device information leaked
- Location leaked
## Update Mechanism 更新機制
- Update sent without encryption
- Updates not signed
- Update location writable
- Update verification
- Malicious update
- Missing update mechanism
- No manual update mechanism
## Mobile Application 行動裝置的應用程式
- Implicitly trusted by device or cloud
- Username enumeration
- Account lockout
- Known default credentials
- Weak passwords
- Insecure data storage
- Transport encryption
- Insecure password recovery mechanism
- Two-factor authentication
## Vendor Backend APIs 供應商後端API
- Inherent trust of cloud or mobile application
- Weak authentication
- Weak access controls
- Injection attacks
## Ecosystem Communication 生物系統的通訊
- Health checks
- Heartbeats
- Ecosystem commands
- Deprovisioning
- Pushing updates
## Network Traffic 網路流量
- LAN
- LAN to Internet
- Short range
- Non-standard
