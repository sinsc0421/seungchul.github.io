---
title: '공유기 없이 노트북으로 와이파이 만들기'
layout: post
tags : etc
category: etc
subtitle: 공유기 없이 노트북으로 와이파이 만들기
author : ssc
---

**공유기 없이 노트북으로 와이파이 만들기**{: style="display:inherit;text-align:center;"}

---

## 1. 명령프롬프트 열기


- window키 + R > cmd 확인

![cmd](/assets/images/post/cmd.PNG)

### 1) 지원되는 노트북 확인
```sh
netsh wlan show drivers
```

호스트 된 네트워크 지원 : "예" 로 메세지가 나온다면 정상적으로 진행 가능

### 2) Wifi 만들기
```sh
netsh wlan set hostednetwork mode=allow ssid=와이파이 이름 key=비밀번호

ex)
netsh wlan set hostednetwork mode=allow ssid=pcwifi key=12345678
```

이름 : 영문  // 비밀번호 : 8자리 이상

![wifi2](/assets/images/post/wifi2.PNG)

### 3) Wifi 시작
```sh
netsh wlan start hostednetwork
```

![wifi3](/assets/images/post/wifi3.PNG)

### 4) Wifi 시작 확인
```sh
netsh wlan show hostednetwork
```

### 5) Wifi 중지
```sh
netsh wlan stop hostednetwork
```

### 5) Wifi 연결

![wifi4](/assets/images/post/wifi4.PNG)
