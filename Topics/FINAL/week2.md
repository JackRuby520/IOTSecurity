# 建置dvwa測試平台在Raspberry PI 3 websecurity@IOT devices

## DVWA漏洞測試架構

![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/class/2.jpg)

### 漏洞測試
```
測試


```

### 檢視apache web server的log檔

```
/var/log/apache2
access.log       
error.log       
modsec_audit.log


```


### cat error.log

DVWA網頁下過的指令有錯誤的，會記錄在error.log中，
讓使用者知道有那些錯誤的內容
![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/DVMA/error.jpg)

### cat access.log

DVWA網頁下過的指令都會記錄在access.log中，
讓使用者了解下過那些指令

![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/DVMA/access.jpg)

在網址打 http://172.20.168.157/DVWA/vulnerabilities/fi/?page=../../../../../../etc/password

#### cat error.log 會出現剛才打網址的error message

![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/DVMA/error2.jpg)

### 安裝modsecurity
```
sudo apt-get update
sudo apt-get install libapache2-modsecurity -y
```
![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/modsecurity/1.jpg)
```
錯誤 sudo a2enconf fqdn && sudo systemctl reload apache2
sudo systemctl reload apache2

sudo  service apache2 reload
sudo apachectl -M | grep --color security2

sudo mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
sudo service apache2 reload

sudo sed -i "s/SecRuleEngine DetectionOnly/SecRuleEngine On/" /etc/modsecurity/modsecurity.conf
sudo sed -i "s/SecResponseBodyAccess On/SecResponseBodyAccess Off/" /etc/modsecurity/modsecurity.conf
```

![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/modsecurity/2.jpg)

```
sudo vim /etc/apache2/mods-enabled/security2.conf
------------------------------------------------------------------------------------
<IfModule security2_module>
        # Default Debian dir for modsecurity's persistent data
        SecDataDir /var/cache/modsecurity

        # Include all the *.conf files in /etc/modsecurity.
        # Keeping your local configuration in that directory
        # will allow for an easy upgrade of THIS file and
        # make your life easier
        IncludeOptional /etc/modsecurity/*.conf
        #在security2.conf加上底下二行
        IncludeOptional "/usr/share/modsecurity-crs/*.conf"
        IncludeOptional "/usr/share/modsecurity-crs/activated_rules/*.conf"
</IfModule>
```
![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/modsecurity/3.jpg)

```
sudo service apache2 reload

sudo cp /usr/share/modsecurity-crs/base_rules/modsecurity_crs_41_sql_injection_attacks.conf /usr/share/modsecurity-crs/activated_rules/
sudo service apache2 reload
```
![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/modsecurity/4.jpg)
```
http://172.20.168.23/DVWA/vulnerabilities/sqli/

SQL Injection 輸入 1' or '1' = '1 送出，畫面會出現無網頁，
會查不到使用者帳密
```
![image](https://github.com/JackRuby520/IOTSecurity/blob/master/pic/modsecurity/5.jpg)

# 關鍵字

python apache parser

https://github.com/rory/apache-log-parser

apache data transfer log to json

https://github.com/kadnan/logs2json

sqlmap detect waf

sqlmap bypass waf

