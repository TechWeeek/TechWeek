## SSR과 CSR
<blockquote cite="https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8">
<p> <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F3GTws%2FbtqFURvXr0y%2FFO9BlRE4NnPSs3I1BTh7Ik%2Fimg.png"></img>
출처: The Benefits of Server Side Rendering Over Client Side Rendering 
</p>
</blockquote>
<br>

### SSR(Server-side Rendering)이란?
서버 사이드 렌더링.

기존에 자주 사용하던 방식의 렌더링이다. 클라이언트가 서버에 요청을 하면서 브라우저에 표시된 html을 넘기게 되면 서버는 그 요청에 대한 결과값을 도출하여 만들어진 새로운 html을 클라이언트에 넘겨준다. 여기서 매번 새로운 html을 서버에서 넘겨주다보니 반응 속도가 느리다. 많은 정보가 있는 웹에서 인터렉션 시마다 페이지가 전체적으로 새로 렌더링되는 것이다. (요청 시 새로고침이 일어난다) 이를 개선하기 위해 일부 html이나 스크립트만 넘기고 수정하는 방식을 사용했다고 하지만 여전히 <b>클라이언트 요청 > html 리소스 전달 > 서버 결과값 계산 > html 리소스 전달 > 클라이언트 표시</b>의 과정을 거치는 방식이다.

<br>

### CSR(Client-side Rendering)이란?
클라이언트 사이드 렌더링.

<strong>전통적인 방식</strong>에서의 SPA는 클라이언트 사이드 렌더링 방식이다.

유저가 인터렉션한 화면 영역만 변화가 필요한 경우에, 그 영역만 정보를 읽어들이고 서버에 전달한다. 그리고 받은 json 과 같은 리소스로 view 영역은 클라이언트가 처리하는 방식이다. 

<br>

### SSR과 CSR의 렌더링 과정

<blockquote cite="https://www.truebil.com/blog/what-shifting-to-server-side-rendering-looks-like">
<p> <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdXTzOU%2FbtqFUAnIVR3%2FfEJwoZ6tMNnjWskLynCzi0%2Fimg.png"></img>
출처 : What shifting to server-side rendering looks like!
</p>
</blockquote>
서버 사이드 렌더링

유저 요청 > 서버 html 파일 전송 (view가 유저에게 표시됨, 하지만 인터렉션 불가능) > 브라우저가 js를 다운로드 (인터렉션 불가) > 브라우저가 프레임워크 실행 (인터렉션 가능)

클라이언트 사이드 렌더링

유저 요청 > HTML 파일과 연관된 js를 서버에서 보내줌 > 브라우저가 HTML 파일과 js를 받음 > 브라우저가 프레임 워크 실행 (view 표시 및 인터렉션 가능)

<br>


### SSR과 CSR 방식의 차이점

서버 사이드 렌더링은 유저에게 초기 진입 시 속도가 빠르게 느껴진다. (view를 모두 렌더한 채로 전달되기 때문에)

그러나 js를 다운로드 및 적용하는 시간때문에 인터렉션이 되기까지 로딩이 있다.

클라이언트 사이드 렌더링은 클라이언트 쪽에서 view를 그리기 때문에 상대적으로 느리게 느껴질 수 있다.

하지만 view가 보여진 후 이미지를 클릭하거나 인터렉션을 하게 되면 즉각적으로 클라이언트에서 view를 새로 제공함으로써 인터렉션 속도는 빠르게 보여진다.

클라이언트 사이드 렌더링의 문제점으로는 SEO(Search Engine Optimization, 검색 엔진 최적화)와 보안 문제가 발생한다.

<br>

참고 자료

https://d2.naver.com/helloworld/7804182

https://velog.io/@zansol/확인하기-서버사이드렌더링SSR-클라이언트사이드렌더링CSR

https://asfirstalways.tistory.com/244

https://www.slipp.net/questions/368