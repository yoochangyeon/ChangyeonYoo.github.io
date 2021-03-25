---
title:  "그런 REST API로 괜찮은가"
excerpt: "진짜 REST API는 무엇인가?"

categories:
  - WEB
tags:
  - REST
  - REST API
---

# 진짜 REST API는 무엇인가?

## 들어가기 앞서 출처를 남깁니다

이 글은 유튜브 채널 'Naver D2'의 
'그런 REST API로 괜찮은가?' by [이응준](https://blog.npcode.com)의 영상을 보고 작성했습니다.

## REST가 나오게 된 이유

### WEB (1991)

1991년 WEB이 탄생했다.

인터넷에서 어떻게 정보를 공유할 것인가? 라는 질문을 해결하기 위해 WEB이 만들어졌다. Tim Berners-Lee는 모든 정보들을 하이퍼 텍스트로 연결하는 해결책을 제시했다,

- 표현방식 : HTML
- 식별자 : URI
- 전송 방법 HTTP

HTML이라는 형식으로 정보를 표현, 식별자로 URI 사용, 전송 방법으로 HTTP라는 프로토콜을 사용 하기로 했다.

#### HTTP/1.0 (1994-1996)

HTTP라는 프로토콜을 설계하는데 많은 사람들이 참여했다. HTTP/1.0명세가 나오기 전에 웹은 이미 급속도로 성장하고 있었다.

이 시점에서  Roy T.Fielding은 HTTP를 정립하고, 명세의 기능을 더하고, 기존 기능을 수정해야 하는 상황이었다. Roy T.Fielding이 HTTP를 고치면 기존에 있는 Web하고 충돌이 생길 수 있었다.

Roy T.Fielding이 HTTP/1.0작업에 참여 하면서 한가지 질문을 던진다. 

> "How do I improve HTTP without breaking the Web?"

Web을 깨뜨리지 않고 HTTP를 improve(개선?)할 수 없을까?

Roy T.Fielding이 이 해결책으로 **HTTP Object Model**을 제시한다. 

**이것이 4년 후에 REST라는 이름으로 Microsoft Research에서 발표한다.**

#### XML-RPC (1998) by Microsoft

그러는 한편 인터넷에서 API가 만들어지기 시작한다.

마이크로소프트에서 원격으로 다른 시스템의 메소드를 호출할 수 있는 XML-RPC라는 프로토콜을 만든다.

이는 이후 SOAP이라는 이름으로 바뀌게 된다.

#### Salesforce API (2000. 02)

Salesforce는 당시 SOAP를 사용해서 API를 만들었다. 

SOAP은 너무 복잡했기 때문에 인기가 없었다.

#### flickr API (2004. 08)

4년 후에 flickr에서 API를 만들었다.

flickr는 SOAP과 REST방식을 모두 사용해서 API를 만들었다.

REST가 SOAP에 비해서 매우 짧았다.

#### 그 당시 SOAP v.s. REST

때문에 사람들의 인식은 다음과 같이 바뀌었다.

| SOAP        | REST        |
| ----------- | ----------- |
| 복잡하다    | 단순하다    |
| 규칙이 많다 | 규칙이 적다 |
| 어렵다      | 쉽다        |

이 때문에 이후 REST의 인기가 급상승하기 시작했다.

#### REST의 승리

2006년 AWS가 자사 API의 사용량의 85%가 REST임을 밝혔다.

2010년 Salesforce.com조차 REST API를 추가했다.



## 이것은 REST가 아니다

#### CMIS (2008)

- CMS를 위한 표준
- EMC, IBM, Microsoft등이 함께 착엄
- REST 바인딩 지원

여러 큰 기업들이 참여한 CMIS라는 것이 나온다. CMIS가 REST 바인딩을 지원했다.

그러나 이를 본 Roy T. Fielding은 이런 말을 한다.

>  "No REST in CMIS"

CMIS에 REST는 없다.



#### Microsoft REST API Guidelines (2016)

또 2016년 마이크로소프트에서도 API 가이드라인을 발표했다. 내용은 다음과 같다.

- uri는 https://{serviceRoot}/{collection}/{id} 형식이어야한다.
- GET, PUT, DELETE, POST, HEAD, PATCH, OPTIONS를 지원한다.
- API 버저닝은 Major.minor로 하고 uri에 버전 정보를 포함시킨다.

사람들이 듣기에는 이는 매우 합리적인 이야기였다. 흔히 알고 있는 좋은 REST API에 부합하는 것 같았다.

그러나 Roy T. Fielding은 자신의 트위터에 이런 말을 한다.

> "이는 REST API가 아니다, HTTP API라고 불러야 한다."

또한 이런 말도 한다.

> "REST API는 반드시 hypertext-driven이어야 한다."

>  "REST API를 위한 최고의 버저닝 전략은 버저닝을 안 하는 것"

이는 사람들이 알고 있는 REST API와 이를 만든 Roy T.Fielding의 REST API는 너무 달랐다. 왜 Roy T. Fielding은 이것들이 REST가 아니라고 말했는가? roy가 말하는 REST는 무엇인가?

## 따져보자

REST API란 무엇인가?

-  REST API : REST 아키텍쳐 스타일을 따르는 API

그렇다면, REST는 무엇인가?

- REST : 분산 하이퍼미디어 시스템(예: 웹)을 위한 아키텍쳐 스타일

그렇다면, 아키텍쳐 스타일은 무엇인가?

- 아키텍쳐 스타일 : 제약조건의 집합. 즉 모든 제약조건을 만족해야 REST를 따른다고 말할 수 있다.

### REST를 구성하는 아키텍쳐 스타일

그렇다면 REST를 구성하는 아키텍쳐 스타일은 무엇일까? 아래 목록을 보자.

- Client-server
- stateless
- cache
- Uniform interface
- Layered system
- Code-on-demand (optional)

오늘날 대부분의 스타일들이 잘 지켜진다. 왜냐하면 HTTP만 따라도 대체로 지켜지는 것들이 많기 때문이다. client-server, stateless, cache, layered system이 그랬다.

그러나 uniform interface를 만족하지 못한다.

### Uniform interface

그렇다면 Uniform interface는 무엇인가? 아래는 이의 제약조건이다.

- identification of resources : resorce가 uri로 식별되면 된다.
- manipulation of resources through representations : resource를 만들거나 업데이트하거나 삭제하거나 할 때, HTTP 메세지에 표현을 담아서 전송해야 한다.

위에 두 가지 조건은 대부분 잘 지켜진다. 그러나 아래에 두가지 제약조건은 대부분이 지키지 못하고 있다.

- **Self-descriptive message** : 메세지는 스스로 설명해야한다.

- **Hypermedia as the engine of application state (HATEOAS)**

#### Self-descriptive message

목적지가 명시되어 있어야 하고 응답 메세지가 어떤 형식인지 (어떤 명세를 따르는지) 명시해야 한다. 즉, 메세지를 보고 이 메세지가 무엇인지 어떻게 해석해야 하는지를 알 수 있어야한다.

#### HATEOAS

애플리케이션 상태의 전이마다 항상 해당 페이지에 있는 하이퍼링크를 통해야 한다.

**위 두가지는 자칭 'REST API'라고 불리는 거의 모든 API들에서 잘 지켜지고 있지 않다.** 

왜 지켜지고 있지 않은지, 어떻게 지켜지고 있지 않은지는 응준님의 [영상][https://tv.naver.com/v/2292653] 을 통해 알 수 있다.

## 왜 Uniform interface를 따라야 하는가?

uniform interface를 따르지 못하고 있다는 것을 알았다.

그런데 우리는 왜 Uniform interface를 지켜야 하는 것일까? 그 이유는 REST가 만들어진 이유와 같다.

### 독립적 진화

- 서버와 클라이언트가 각각 독립적으로 진화한다.
- 서버의 기능이 변경되어도 클라이언트를 업데이트할 필요가 없다.
- REST를 만들게 된 계기 : "How do I improve HTTP without breaking the Web"

REST를 만들게 된 이유는 HTTP의 독립적인 진화였고, 이를 위해 Uniform interface를 지켜야한다.



### 오늘날의 웹은 어떤가?

그렇다면 지금 웹은 이것들이 잘 지켜지고 있는가?

- 웹 페이지를 변경했다고 웹 브라우저를 업데이트할 필요는 없다.
- 웹 브라우저를 업데이트했다고 웹 페이지를 변경할 필요도 없다.
- HTTP 명세가 변경되어도 웹은 잘 작동한다.
- HTML 명세가 변경되어도 웹은 잘 동작한다.

위의 내용들을 통해 웹에서 독립적 진화가 잘 지켜지고 있다는 것을 알 수 있다.

### 모바일 앱은 어떤가?

 그렇다면 모바일 앱은 어떤가? 잦은 업데이트가 이루어지는 모바일 앱들을 많이 볼 수 있다.

이처럼 모바일 앱은 웹에 비해 업데이트가 매우 잦다. 이는 곧 모바일 앱이 REST API를 엄격히 지키고 있지 않다고 말할 수 있는 것이다.

## 웹은 어떻게 이를 가능하게 했는가?

그렇다면 웹은 어떻게 이게 가능했을까? HTML5과 HTTP명세 작업에 걸린 시간을 보자.

- HTTML5 첫 초안에서 권고안 나오는데까지 6년
- HTTP/1.1 명세 개정판 작업하는데 7년

왜 이렇게 오랜 시간이 걸렸는가? 이는 절대로 하위호환성을 깨뜨리면 안되기 때문에 수 많은 사람들이 오랜 시간 노력을 했기 때문이다. 

상호운용성을 지키기 위해 수 많은 서버, 클라이언트 개발자들이 노력했다. 

### 상호운용성(interoperability)에 대한 집착

아래 내용들을 통해 당시 개발자들의 **상호 운용성을 지키겠다는 집착**을 잘 확인할 수 있다.

- Referer 오타지만 고치지 않는다.
  - Referer 해더에 오타가 있지만 고치지 못한다. 오타를 수정하면 이전 웹이 깨지기 때문에
- Charset 잘못 지은 이름이지만 고치지 않는다.
  - encording이라고 이름을 지어야 했지만 이름을 고치면 상호운용성이 깨지기 때문에 이름을 고치지 않는다.
- HTTP 상태 코드 416 포기함 (I'm a teapot)
  - 만우절에 만들었던 416 상태 코드를 만들었다.
  - 수많은 서버 구현체들이 416을 상태 코드로 구현을 했다.
  - 잘못 만들어진 상태코드들을 수많은 서버 구현체들이 구현을 했기 때문에 이들과의 상호 운용성을 깨뜨리지 않기 위해 HTTP 는 416 상태 코드를 포기한다.
- HTTP/0.9 아직도 지원한다.
  - 20년이 넘은 HTTP/0.9를 계속 지원하고 있다.

## REST가 웹의 독립적 진화에 도움을 주었나

웹의 독립적 진화가 성공했다는 것은 확인했다.

그렇다면 실제로 REST가 독립적 진화에 도움을 주었는가? 

아래 내용들을 보면 REST가 웹의 독립적 진화에 기여했다는 것을 확인할 수 있다.

- HTTP에 지속적으로 영향을 줌
- Host 헤더 추가
- 길이 제한을 다루는 방법이 명시 (414 URI Too Long 등)
- URI에서 리소스의 정의가 추상적으로 변경됨 : "식별하고자 하는 무언가"
- 기타 HTTP와 URI에 많은 영향을 줌
- HTTP/1.1 명세 최신파에서 REST에 대한 언급이 들어감
- Roy T.Fielding이 HTTP와 URI명세의 저자 중 한명이다.

## REST는 성공했는가?

위 내용들을 토대로 REST가 성공했는지를 따져보자.

- REST는 웹의 독립적 진화를 위해 만들어졌다
- 웹은 독립적으로 진화하고 있다.

즉, REST는 성공했다.

## 그런데 REST API는?

그렇다면 지금 우리가 쓰고 있는 REST API는 어떤가?

- REST API는 REST 아키텍쳐 스타일을 따라야한다.
- 오늘날 스스로 REST API라고 하는 API들이 대부분 REST 아키텍쳐 스타일을 따르고 있지 않다.

### REST API도 모든 제약조건들을 다 지켜야 하는 것인가?

우리는 이러한 물음을 던질 수 있다. REST API도 그 모든 제약 조건들을 반드시 지켜야 하는 것인가? Roy T. Fielding은 이에 대해 반드시 지켜야 한다고 말한다.

그렇다면 또 이런 질문을 던질 수 있다. 

"원격 API가 꼭 REST API여야 하는가?", "우리가 꼭 REST API만 사용해야 하는가?"

Roy T. Fielding은 이렇게 답한다.

>  "시스템 전체를 통제할 수 있다고 생각하거나, 진화에 관심이 없다면, REST에 대해 따지느라 시간을 낭비하지마라"

시스템을 통제 가능하다고 말하는 것은 서버 개발자가 클라이언트 개발자를 완벽히 통제할 수 있거나 자신이 서버와 클라이언트를 모두 개발하는 것처럼 완벽히 시스템을 통제할 수 있는 상황이다.



## 그럼 이제 어떻게 할까?

1. REST API를 구현하고 REST API라고 부른다.
2. REST API 구현을 포기하고 HTTP API라고 부른다.
3. REST API가 아니지만 REST API라고 부른다. 

우리는 몇번째 방안을 선택했는가? 우리는 3번 방법을 선택하고 사용하고 있다.

REST API가 아니지만 REST API라고 부르며 사용한다.

이에 대해 Roy T. Fielding은 말한다.

>  "제발 제약조건을 따르던지 아니면 다른 단어를 써라"

## REST API를 구현하기 위한 도전

위에 방안중 1번 (REST API를 구현하고 REST API라고 부르자)를 시도해보자.

### 왜 API는 REST가 잘 안되나?

올바른 REST API를 사용하기 위해서 우리는 왜 REST가 잘 안되는지 즉, 왜 REST의 규약들을 잘 지키지 못하는지 확인해보자

#### 일반적인 웹과비교

우리가 흔히 쓰는 웹페이지와 HTTP API간의 차이를 살펴보자.

|              | 흔한 웹 페이지 | HTTP API  |
| ------------ | -------------- | --------- |
| Protocol     | HTTP           | HTTP      |
| 커뮤니케이션 | 사람-기계      | 기계-기계 |
| Media Type   | HTML           | JSON      |

커뮤니케이션 대상이 다르기 때문에 Media Type의 차이가 생긴다.

HTTP API에서는 JSON이나 XML같은 기계가 이해할 수 있는 형식을 사용한다.

그렇다면 HTML과 JSON의 차이는 무엇인가?

|                  | HTML             | JSON              |
| ---------------- | ---------------- | ----------------- |
| Hyperlink        | 가능 (a 태그 등) | 정의되어있지 않음 |
| Self-descriptive | 가능 (HTML 명세) | 불완전            |

JSON은 문법은 정의가 되어있지만 그 안에 어떤 값들이 들어가야 하는지 정의가되어있지 않다. **즉, 문법 해석은 가능하지만, 의미를 해석하려면 별도로 문서(API 문서 등)가 필요하다.**

{ "id" : 1, "title" : "json" } 을 보고 id가 무엇을 의미하는지 title이 무엇을 의미하는지 알 수 없다. **때문에 JSON형식은 self-descriptive를 만족하지 못한다.**

## 그런데 Self-descriptive와 HATEOAS가 독립적 진화에 어떻게 도움이 될까?

JSON은 위 두가지 조건을 만족시키기 어렵다.

그렇다면 우리는 질문을 던진다.  **우리가 지키지 못하고 있던 두가지 규약 Self-descriptive와 HATEOAS가 정말 웹의 독립적 진화에 도움이 될까?** 도움이 된다면 도대체 어떻게 도움이 될까?

### Self-descriptive : 확장 가능한 커뮤니케이션

self-descriptive는 확장 가능한 커뮤니케이션을 만들어준다. 즉, 서버나 클라이언트가 변경되더라도 메시지는 언제나 self-descriptive하므로 언제나 해석이 가능하다.

### HATEOS : 애플리케이션 상태 전이의 late binding

HATEOS는 애플리케이션 상태 전이의 late binding을 해준다.

어디서 어디로 전이가 가능한지 미리 결정되지 않는다. 

어떤 상태로 전이가 완료되고 나서야 그 다음 전이될 수 있는 상태가 결정된다. 

쉽게 말해서, **링크는 동적으로 변경될 수 있다.**



## 이제 우리는?

REST API를 엄격히 따른다는 것은 결코 쉽지 않다는 것을 알았다.

이제 우리는 REST API를 따르기 위해서 노력할 것인지 REST API를 따르지 않을 것인지 결정해야 한다.

###  REST API를 따르기 위해서

우리는 결국 REST API를 엄격히 따르기 위해서는 어쩔 수 없이 self-descriptive와 HATEOS를 지켜야한다.

REST API를 바르게 따르기 위해서는 **custom media type이나 profile link relation등으로 self-descriptive를 만족시켜야 한다.**

**HTTP헤더나 본문에 링크를 담아** HATEOAS를 만족시켜야 한다.



### REST API를 따르지 않겠다면

우리가 REST API를 따르지 못한다면, 따르지 않겠다면

**"REST를 만족하지 않는 REST API"를 뭐라고 부를지 결정해야 한다.**

- HTTP API라고 부를 수 있다
- 그냥 이대로 REST API라고 부를 수 있다. (Roy T. Fielding이 싫어한다.)

##### 