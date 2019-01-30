---
title: '리눅스 파일 검색(Find, exec grep)'
layout: post
tags : Linux
category: Linux
subtitle: 리눅스 파일 검색(Find, exec grep)
author : ssc
---

**리눅스 파일 검색(Find, exec grep)**{: style="display:inherit;text-align:center;"}

---

서버 로그를 찾아보기 위해 쉬운 방법이 있을까 하다 다음 방법을 찾았습니다. 

파일을 하나하나 뒤지는게 아니라 찾고 싶은 검색어를 입력하여 어느 파일에 있는지 찾기 위한 간단한 팁을 공유하려 합니다.
## 1. 최종 커맨드

```sh
find [원하는 경로] -type f -name "*" -exec grep -Hn --color "Your_KeyWord" {} \;
```
= 위 스크립트는 특정 키워드가 있는 파일명과 줄번호를 보여줍니다.

## 2. 키워드 분석
```sh
find [원하는 경로]	#(1)
-type f					#(2)
-name "*"				#(3)
-exec grep -Hn --color "Your_KeyWord" {} \;	#(4) 
```

4개의 섹션으로 나누어 보았습니다.

(1) find *커맨드로 원하는 경로*를 넣어 줍니다. ex) /app-log

(2) 찾고자 하는 *파일 형식* 지정. 

들어갈 타입값은 ```man find``` 를 이용하여 상세한 설명을 볼 수 있습니다.

예제로는 f를 사용하였고, regular file을 뜻합니다.

(3) 찾고자 하는 *파일의 규칙*을 정규식으로 지정 할 수 있습니다.

ex) *.jsp, *.log 등

예제로는 모든 파일인 *로 지정했습니다.

(4) find 커맨드 실행을 통해 나온 결과 파일 목록을 ```grep``` 커맨드로 넘겨줍니다.
 
여기서 grep의 옵션으로 -H가 있는데 이는 해당 파일의 이름을 보여주는 것이고, -n은 키워드를 찾은 줄번호를 출력합니다.
 
마지막으로 --color 옵션은 출력할 내용에 예쁘게 색칠(!)을 해주는 용도입니다.
 
바로 옆에 "YOUR_KEYWORD" 부분은 찾고자 하는 문자열을 넣어줍니다.
 
그리고 마지막에는 {} \;를 넣어주도록 합니다.

```
{} \;
```
{} 은 앞서 찾은 파일을 뜻하고, \; 은 옵션의 끝을 알립니다.

##3. 검색결과

![findLog](/assets/images/post/findLog.PNG)

