---
title:  "네이버 뮤직 가사 크롤링"
excerpt: "BeautifulSoup를 이용한 네이버 뮤직 가사 크롤링"

categories:
  - PYTHON
tags:
  - CRAWLING
  - PYTHON
---

## 들어가며 : BeautifulSoup 설치

BeautifulSoup를 파이썬에 설치하는 과정은 다른 블로그에 좋은 글들이 많습니다  
다음 블로그를 참고하면 좋을것 같습니다. [파이썬에서 BeautifulSoup설치하기](https://shaeod.tistory.com/900)

# 네이버 뮤직 가사 크롤링

#### [전체 코드 : 깃허브](https://github.com/ChangyeonYoo/CCM_Lyrics/blob/main/testcrawling.py)

```py
import requests
from bs4 import BeautifulSoup
lyrics = []
musicId = 19399121
url = "https://music.naver.com/lyric/index.nhn?trackId="+str(musicId)
response = requests.get(url2)
```

가사를 불러올 리스트를 하나 생성해주고 네이버 뮤직 url을 가져옵니다.  
네이버 뮤직의 경우에는 trackID파라미터 값으로 음악의 가사를 읽어옵니다.  
때문에 뒤에 숫자를 변경하면 그 음악의 가사를 나타내줍니다.  
!\[\]![](https://images.velog.io/images/changyeonyoo/post/26d8bb57-62f1-474a-9648-679384541614/image.png)  
BeautifulSoup를 사용하기 위해 parser객체를 생성해줍니다.

```py
html = response.text
soup = BeautifulSoup(html, 'html.parser')
```

가사를 표시해주는 웹에서 가사 부분만 파싱하기 위해 크롬 개발자도구 (크롬 창에서 F12)를 사용하여 html태그를 확인해봅니다.  
![](https://images.velog.io/images/changyeonyoo/post/496b9931-0e95-4db2-926b-238f37723774/image.png)  
div아래 show\_lyrics라는 id를 가진 부분이 가사가 적혀있는 곳 입니다.  
이부분을 크롤링하기위해

soup.select 메소드를 사용해봅니다.

```py
requst_lyrics = soup.select('div.show_lyrics')
```

다음으로 크롤링한 부분을 이전에 만들어 두었던 리스트에 저장합니다.

```py
for i in requst_lyrics:
    lyrics.append(i.get_text())
```

이렇게만하고 출력하면 어떻게될까?  
![](https://images.velog.io/images/changyeonyoo/post/5fe2d6d1-ada4-45c3-a12f-f72254897002/image.png)

위와같이 개행없이 가사가 출력됩니다.

## `<br/>`태그 가공하기

위와 같은 형태도 단순히 데이터베이스에 저장하기 위해서는 무리가 없습니다.  
그러나 보기 편하게 바꿔주기 위해서는 약간의 작업을 더 해주어야 합니다.

```py
for i in requst_lyrics:
    lyrics.append(i)
```

i.get\_text()로 리스트에 추가하지 않고 i를 추가해줍니다.

![](https://images.velog.io/images/changyeonyoo/post/ac627d4d-3155-48d0-b435-f594f1b56449/image.png)

그러면 위와같이 약간의 테그들이 섞여서 들어오는 것을 확인할 수 있습니다.

```py
s = ""
s = s + str(lyrics[0])
s = s[40:]
s = s[:-6]
s = s.replace('<br/>', '\n')
print(s)
```

정말 기초적인 문법으로 가공해봅니다.  
위와 같이 리스트에 들어온 데이터를 string형태로 바꿔주고  
앞에 40글자를 잘라줍니다.  
`[<div class="show_lyrics" id="lyricText">`  
이부분은 어떠한 음악을 크롤링해오던 고정적으로 들어오기 때문에  
40글자로 딱 잘라줄 수 있습니다.

뒷부분에 들어오는 6글자 `</div>]`또한 잘라줍니다.

이후 궁극적인 목표였던 `개행`을 위해서  
replace 메소드를 사용하여 `<br/>`태그를 `\n`으로 변경해줍니다.  
이후 다시 출력해주면 원하는 모양으로 출력되는것을 확인할 수 있습니다.

![](https://images.velog.io/images/changyeonyoo/post/dae57d4d-3a41-435b-ab7e-07dfaa5972c7/image.png)