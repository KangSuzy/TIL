# Http 상태코드

![image](https://miro.medium.com/max/1400/1*i9zcutz-89o-13oyK6ZVTQ.png)

# Http 메서드 ( GET, POST, PUT, PATCH, DELETE )

- POST : 자원 생성

  보통 하위 자원을 생성하는데 .. 테이블안의 데이터를 생성하는 ..

  성공적으로 생성되면 HTTP 상태 201 반환 !

- GET : 읽기

  성공시 200, 가장 자주 404 또는 400 ( Bad Request ) 를 반환

  데이터를 수정, 삭제하는데 사용하면 안된다

- PUT : 업데이트 ( 전체자원 )

  요청을 보낼때 전체를 보내야한다

- PATHCH : 업데이트 ( 일부자원 )

  요청을 보낼때 수정하는 일부분을 보내야한다

- DELETE : 삭제

---

# REST API

API 란 소프트웨어와 소프트웨어 사이 데이터 전송을 가능하게 하는 프로그램 이다 ..

**REST API**

웹의 장점을 잘 살린 아키텍처, Uniform-Interface 를 갖는 것이 특징 !

    _Uniform-interface : 자원들이 각각의 독립적인 인터페이스를 가짐_

    - 웹페이지를 변경했다고 웹 브라우저를 업데이트하는 일이 없어야한다

    - HTTP 명세나 HTML 명세가 변경되더라도 웹페이지는 잘 작동해야 한다

## 아키텍처의 규칙

1. Self-descriptive messages

   Http Header 에 타입을 명시하고 각 메세지( 자원 )들은 MIME types 에 맞춰 표현되어야 함

   예로 .json 을 반환한다면 application / json 으로 명시해주어야한다 !

2. HATEOAS 구조

   하이퍼링크에 따라 다른 페이지를 보여줘야 하며 데이터마다 어떤 URL 에서 원해는지 명시해주어야한다

3. Stateless

   이 규칙은 HTTP 자체가 Stateless 이기 때문에 HTTP 를 이용하는 것만으로도 만족

   즉 REST API 를 제공해주는 서버는 세션(Session) 을 해당 서버쪽에 유지하지 않는다는 의미

4. Cacheable

   Http 는 원래 캐싱이 된다 !

   캐싱은 네트워크 요청을 줄여주며 UX 향상에 도움이 되는데 ..

   네트워크 요청시 해당하는 자원들을 복사해서 메모리에 저장해 두었다가

   같은 요청시 네트워크 요청을 하지 않고 브라우저 메모리에 있던 자원들을 다시 반환하는 ..

   HTTP 메서드 중 GET 에 한정되며 'Cache-Control:max-age:100' 이런식으로 한정된 시간을 정할 수 있따

   **캐싱된 데이터가 유효한지 판단**하기 위해 'Last-modifed' 와 'Etag' 를 사용

   - Etag : 전달되는 값에 태그를 붙여서 캐싱되는 자원인지 확인

5. Client-Server 구조

   클라이언트와 서버가 서로 독립적인 구조를 가져야 한다는 규칙 !

   HTTP 를 통해 가능한 구조, 서버에서 HTTP 표준만 지킨다면 웹에서는 그에 따른 화면이 잘 나타난다

   서버에서는 API 를 제공하고 그에 맞는 비즈니스 로직을 처리하고

   클라이언트에서는 HTTP 로 받는 로직만 잘 처리하면 된다 !

6. Layered System

   계층 구조로 아키텍처를 만들 수 있다는 뜻

   아래의 자원을 표기하는 URI 규칙을 적용해야 한다

   1. 동작은 HTTP 메소드로 ..

   2. 확장자는 표기 X

   3. 동사가 아닌 명사로만 표기

   4. URI 는 계층적인 내용을 담아야 한다

   5. 소문자로 쓰며 너무 길경우 **-** 를 사용

   6. HTTP 응답 상태코드를 활용