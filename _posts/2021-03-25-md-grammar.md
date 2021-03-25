---
title: md grammar
read_time: true
---

# md 문법에 대한 연습중입니다.


![screensh](../assets/set_logo.png )





> 인용문
> >인용문 안의 인용문




~~~
이것또한 코드블럭
입니다
~~~




## 제목


~~~r

# r 코드 블럭
library(stringr)
library(dplyr)
library(lubridate)
library(rJava)
library(DBI)
library(RJDBC)
library(keyring)
library(data.table)

last = Sys.Date() %m-% months(1)  %>% str_remove_all("-") %>% str_sub(1, 6) %>% as.character


~~~


~~~

# 언어 지정하지 않은 코드 블럭

library(stringr)
library(dplyr)
library(lubridate)
library(rJava)
library(DBI)
library(RJDBC)
library(keyring)
library(data.table)

last = Sys.Date() %m-% months(1)  %>% str_remove_all("-") %>% str_sub(1, 6) %>% as.character


~~~




### 제목
' 인라인 코드 블럭'




#### 제목


[Google](http://www.google.co.kr "구글")



- 리스트1
- 리스트2
- 리스트3
	- 리스트 3-1
	- 리스트 3-2
