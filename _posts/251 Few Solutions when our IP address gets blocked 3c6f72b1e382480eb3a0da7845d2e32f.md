
---
title: "[R] html->md test"
category: R
---

# ggplot2 : 분석 결과 시각화 패키지



251. Few Solutions when our IP address gets blocked (Webcrawling) {.page-title}
=================================================================

### 1. Concept {#86aca5f1-662e-4d16-8b0c-f12f6f3bf4ba}

-   network protocols : standard set of rules that helps in governing
    the way a particular technology functions for communication (i.e.
    computers)

​(1) types of protocols

HTTP: Hyper Text Transfer Protocol

HTTPS: Hyper Text Transfer Protocol Secure

FTP: File Transfer Protocol

SFTP: Secure File Transfer Protocol

Telnet: TErminal NETwork

POP3: Post Office Protocol version 3

SMTP: Simple Mail Transfer Protocol

SSH: Secure Shell

SOAP: Simple Object Access Protocol

ARP: Adress Resolution Protocol

​(2) IP address: (Internet Protocol, a computer's address on the
internet)

-   IP is a unique address that identifies the sender and the receiver
    using tcp/ip protocol. It's a 12-digit number with a format like
    123.456.789.101 and uses numbers between 0\~255. This means this
    number range produces 4.2 billion combinations. of IP address

-   chop the sentence when it is too long!!!!! ALWAYS

### 2. Problem Definition {#db6f2e2e-84d4-4c3e-a740-85cdd1a28da7}

​1) (from a POV of a server) How to block an IP address

-   How does a server block the IP addresses of users who attempt to
    crawl massive amounts of data?

​2) (from a POV of a user) How to prevent an IP from getting blocked
(before/after)

-   How do we prevent a server from blocking the IP address to continue
    crawling the data needed?

### 3. Solution {#a63c540e-ef9c-410c-a52a-b1c7e3a2ad76}

3.1 Utilize a of security techniques such as Black listing and
Whitelisting

link :
[https://consoltech.com/blog/blacklisting-vs-whitelisting/](https://consoltech.com/blog/blacklisting-vs-whitelisting/)

-   black listing : definining which entities should be blocked
    (excluded)

-   white listing : definiting a list of permitted entities (included)

``` {#eb20b2af-e0bf-4033-be76-360392cc6717 .code}
#Black listing using Python Flask 

from flask import abort, request 
from flask import Flask 
app = Flask(__name__) 

# abort : limit an IP before a request   
# remote_addr : when recieves a request from a specific IP, reject it  

@app.before_request 
def limit_remote_addr(): 
    if request.remote_addr == '10.20.30.40':
          abort(403) # Forbidden

#White listing using Python Flask 

from flask import abort, request 
from flask import Flask 
app = Flask(__name__) 

@app.before_request 
def limit_remore_addr():
        if request.remote_addr != '10.20.30.40': 
              abort(403) # Forbidden 


# reference: https://m.blog.naver.com/dsz08082/222025157731
```

3.2 pre(post)-blocking prevention methods

​1) Changing an IP address using VPN when connecting to a server (In
Python, setting a Proxy)

[https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/](https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/)
(4. Make requests through Proxies and rotate them as needed)

``` {#f7c8220b-ef68-42ef-b9a5-57e826b7a973 .code}
# sample code 

from selenium import webdriver
import chromedriver_autoinstaller
import time 

path = chromedriver_autoinstaller.install()

PROXY = "IP: Port"

webdriver.DesiredCapabilities.CHROME['proxy'] = {
    "httpProxy": PROXY,
    "ftpProxy": PROXY,
    "sslProxy": PROXY, 
    "proxyType": "MANUAL"    
}

driver = webdriver.Chrome(path)
driver.get("https://www.google.com")
```

​2) Using a time interval (implict vs explicit waits)

[https://www.guru99.com/implicit-explicit-waits-selenium.html](https://www.guru99.com/implicit-explicit-waits-selenium.html)

​3) Constructing multiple virtual servers

3.1 the concept of virtual server

[https://cloud.google.com/learn/what-is-a-virtual-server](https://cloud.google.com/learn/what-is-a-virtual-server)

3.2 How to construct a virtual server using Amazon AWS

[https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2\_GetStarted.html](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2_GetStarted.html)

### 4. Application at Work {#d30a3618-e5c0-4b0d-9f2d-79b215fa7525}

​1) (POV from a service provdier) Blocking an IP

​(1) Establish a Security Policy (white/blacklisting)

​(2) Apply a blocking technology that fits the security policy

(Please refer to the application of Python flask code above)

​(3) Security Test to confirm blocking

​(4) Feedback from the team

​2) How to prevent IP from getting blocked / How to evade blocking (when
collecting data via crawling)

​(1) Select a topic/keyword to be crawled

​(2) Apply preventive blocking technology

​(3) Verify if the crawled/collected data has been collected sucessfully

​(4) Confirm whether there is a ban or not

5.  Reference

    ​1) types of network protocols

    [https://www.w3schools.in/types-of-network-protocols-and-their-uses/](https://www.w3schools.in/types-of-network-protocols-and-their-uses/)

[https://cloud.google.com/learn/what-is-a-virtual-server](https://cloud.google.com/learn/what-is-a-virtual-server)
