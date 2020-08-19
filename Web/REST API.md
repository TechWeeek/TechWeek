
## SSR과 CSR
<blockquote cite="https://digital-goal.net/foundation-of-restful-api-architecture/">
<p> <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcnaZul%2FbtqGe6MggNK%2FqlmjutLJN4UOJhmmmFUSv1%2Fimg.png"></img>
<br>
출처 : Foundation Of RESTful API Architecture
</p>
</blockquote>
<br>


### REST (REpresentational State Transfer)
REST의 구성 요소는

자원Resources : <sup>[1](#uri)</sup>URI

행위Verb : Http Method (EX. GET, POST, PATCH, PUT, DELETE)

표현Representation 이다.


즉, REST란 간단히 말해서 웹이 존재하는 모든 자원Resources에 고유한 URI를 정의하고 자원에 <sup>[2](#crud)</sup>CRUD를 실행하는 방식(HTTP Method)을 정해놓은 아키텍처 스타일이다.

<br>

### REST 아키텍처의 6가지 제한 조건
클라이언트/서버 구조 : 자원이 있는 쪽이 서버이며, 요청Request을 보내는 쪽이 클라이언트이다.

무상태 (Stateless) : 각 요청 간 클라이언트의 내용이 서버에 저장되어서는 안 된다. (<sup>[3](#session)</sup>서버 세션Session을 사용하면 안 된다.) 즉, 이전 요청과 다음 요청이 연관되어서는 안 된다. 

캐시 처리 가능 (Cacheable) : WWW에서와 같이 클라이언트는 응답을 캐싱할 수 있어야 한다.

계층화 (Layered System) : 클라이언트는 보통 대상 서버에 직접 연결되었는지, 또는 <sup>[4](#midserv)</sup>중간 서버를 통해 연결되었는지를 알 수 없다. 

Code on demand (optional) : 자바 애플릿이나 자바스크립트의 제공을 통해 서버가 클라이언트에 실행시킬 수 있는 로직을 전송하여 기능을 확장시킬 수 있다.

인터페이스 일관성 (Unifom interface) : 아키텍처를 단순화시키고 작은 단위로 분리함으로써 클라이언트-서버의 각 파트가 독립적으로 개선될 수 있도록 한다. HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.

<br>

### RESTful
REST의 원리를 따르는 시스템은 RESTful이란 용어로 지칭된다.

<br>

### REST API 설계 규칙
1. URI는 정보의 자원을 표시해야 한다. (동사보다는 명사를 사용한다, 컨트롤 자원을 의미할 때는 예외적으로 동사를 허용)

해당 사항은 예시를 보면 쉽게 느낄 수 있다.

> GET /user/get-info/13

13번 유저의 정보를 가져온다고 했을 때 get-info 와 같은 부가적인 표현을 제외하고

GET /user/13
user라는 명확한 정보의 자원만을 표시하는 것이다.



2. 자원에 대한 행위는 HTTP Method를 사용한다.

> POST /user/13?action=createUser <br>
GET /user/13?action=getUser <br>
POST /user/13?action=modifyUser <br>
POST /user/13?action=deleteUser 

이전 방식이 예시와 같이 URL에 행위를 표시하는 방식이었다면 REST에서는

> POST /user/13 유저 13번 등록하기 <br>
GET /user/13 유저 13번 불러오기 <br>
PUT /user/13 유저 13번 수정하기 <br>
DELETE /user/13 유저 13번 삭제 

다음과 같이 대상에 대한 행위를 Method를 통해 표현해줍니다.


3. 슬래시(/)는 계층관계를 표현할 때 사용한다.

4. 마지막에 슬래시를 사용하지 않는다.

5. 언더바(_) 대신 하이픈(-)을 사용한다. (하이픈을 사용하게 된다면 가독성을 높이기 위해 사용)

6. URI는 대문자보다 소문자를 사용한다. (대소문자에 따라 다른 자원으로 인식하기 때문)

7. 파일 확장자는 URI에 포함하지 않는다.

8. 정확한 HTTP 응답 코드를 사용한다.

> 성공응답 2XX <br>
실패응답 4XX <br>
서버오류 5XX

서버오류는 사용자에게 표시하지 않는다.

<br>

### 기존 방식과 RESTful API의 차이점
> POST : 자원 생성(Create) <br>
GET : 자원 조회(Read) <br>
PUT : 자원 수정(Update) <br>
DELETE : 자원 삭제(Delete)


기존 방식은 GET과 POST 방식만을 사용하여 CRUD를 처리한다.

RESTful API는 GET, POST, PUT, DELETE 방식을 사용하여 CRUD를 처리한다.

이때의 URI는 제어하려는 자원을 나타낸다.

<br>


REST API를 사용하지 않더라도 API를 정의하는 방식은 무척 다양하고, 사용하려는 프로그램에 따라 맞는 API를 사용하는 것이 중요하다. 실제로 트위터의 API 구조만 해도 GET과 POST만 사용하고 있는 구조임을 알 수 있다. 이처럼 순수한 퍼포먼스 향상을 위해서는 반드시 REST API를 사용해야하는 것은 아니다는 점. REST API는 개발팀이 바뀌더라도 통일성과 확장성이 있기 때문에 쉽게 구조를 이해하고 파악할 수 있게 만들어주는 주 목적이라는 점을 알아두면 더 좋을 것 같다.

<br>

<b id="uri"><sup>1</sup></b>URI : Uniform Resource Identifier. 통합 자원 식별자. 인터넷에 있는 자원을 나타내는 유일한 주소.

<b id="crud"><sup>2</sup></b>CRUD : Create Read Update Delete의 약어

<b id="session"><sup>3</sup></b>Session : 클라이언트의 요청에 따른 정보를 클라이언트 메모리에 저장하는 것이 아닌 웹 서버가 세션 아이디 파일을 만들어 서비스가 돌아가고 있는 서버에 저장한 것.

<b id="midserv"><sup>4</sup></b>중간 서버 : 다중 계층으로 구성된 서버 중 메인 서버와 클라이언트가 아닌 서버. 중간 서버는 <sup>[5](#loadbal)</sup>로드 밸런싱Load Balancing 기능이나 <sup>[6](#shared)</sup>공유 캐시Shared Cache 기능을 제공함으로써 규모 확장성, 보안성을 향상시키는 데 유용하다.

<b id="loadbal"><sup>5</sup></b>Load Balancing : 웹 서버의 부하(Load)를 줄이기 위한 방법 중 하나이다. 다른 방식으로는 DB 서버를 분리하는 방식도 있다. 웹 서버를 증설하며 부하(Load)를 나눠갖는(Balancing) 방식이다.

<b id="shared"><sup>6</sup></b>Shared Cache : 예를 들면 프록시proxy가 있다. 클라이언트와 서버 간에 게이트웨이 역할을 하며 서버 리소스를 저장(혹은 캐싱)하는 것을 의미한다. 클라이언트가 서버에 접근하려하면 프록시가 먼저 리소스 복사본이 있는지 확인하고 있다면 사용자에게 전달한다. 아닌 경우엔 리소스를 소스에서 검색하고 프록시에 리소스를 저장(캐싱)하고 전달한다.

<br>

참고 자료

https://ko.wikipedia.org/wiki/REST

https://beyondj2ee.wordpress.com/2013/03/21/당신의-api가-restful-하지-않은-5가지-증거/

https://mygumi.tistory.com/55

https://www.a-mean-blog.com/ko/blog/REST와-RESTful-API

https://velog.io/@stampid/REST-API와-RESTful-API

https://brainbackdoor.tistory.com/53