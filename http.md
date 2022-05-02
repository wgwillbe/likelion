# HTTP는 무엇일까요?
## HTTP
**HTTP** = **H**yper**T**ext**T**ransfer**P**rotocol  
하이퍼텍스트 문서를 교환하기 위해 사용된 통신 규약  
->웹 서버와 클라이언트 간의 통신을 하기 위한 통신 규약  
HTTP는 1989년 팀 버너스-리에 의해 처음 설계되어 인터넷을 통한 월드 와이드 웹(World-Wide Web : www)기반에서 전 세계적인 정보 공유를 이루는데 큰 역할  
HTTP는 웹에서만 사용하는 프로토콜로 TCP/IP 기반으로 한 지점에서 다른 지점(서버와 클라이언트)으로 요청과 응답을 전송

## HTTP의 특징
HTTP 메시지는 HTTP 서버와 HTTP 클라이언트에 의해 해석  
TCP/IP를 이용하는 응용 프로토콜(application protocol)  
HTTP는 연결 상태를 유지하지 않는 비연결성 프로토콜 (이러한 단점을 해결하기 위해 Cookie와 Session 등장)  
HTTP는 연결을 유지하지 않는 프로토콜이기 때문에 요청/응답(request/response) 방식으로 동작
- 서버 : 어떠한 자료에 대한 접근을 관리하는 네트워크 상의 시스템(요청에 대한 응답을 보내줌)
- 클라이언트 : 그 자료에 접근할 수 있는 프로그램  
예) 웹 브라우저, 핸드폰 어플리케이션 등

<img src="https://user-images.githubusercontent.com/101981594/166189002-a56f92ba-06ff-4b40-b948-7ae43936048f.jpg" width="800px" height="400px"/>

클라이언트(Client) 즉, 사용자가 브라우저를 통해서 어떠한 서비스를 url을 통하거나 다른 것을 통해서 요청을 하면   
서버에서는 해당 요청사항에 맞는 결과를 찾아서 사용자에게 응답하는 형태로 동작한다.

**요청 : client -> server**  
**응답 : server -> client**

### Request (요청)
클라이언트가 서버에게 연락하는 것  
요청을 보낼때는 요청에 대한 정보를 담아 서버로 전달
### Request Method (요청의 종류)
GET : 자료를 요청할 때 사용  
POST : 자료의 생성을 요청할 때 사용  
PUT : 자료의 수정을 요청할 때 사용  
DELETE : 자료의 삭제를 요청할 때 사용

### Request HTTP 메시지 예시

>GET https://velog.io/@surim014 HTTP/1.1								// 시작줄  
>User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...			  // 헤더  
>Upgrade-Insecure-Requests: 1

### 1. 시작줄 (첫 줄)
메서드 구조 버전으로 구성

GET : HTTP Method  
https://velog.io/@surim014 : 사이트 주소
HTTP/1.1 : HTTP 버전

### 2. 헤더 (두 번째 줄부터)
**요청에 대한 정보** 담고 있음  
User-Agent, Upgrade-Insecure-Requests 등이 헤더에 해당  
헤더의 종류는 매우 많음

### 3. 본문(헤더에서 한 줄 띄고)
요청을 할 때 함께 보낼 데이터를 담는 부분  
현재 예시에는 단순히 주소로만 요청을 보내고 있고 따로 데이터를 담아 보내지 않기 때문에 본문이 비어있다.

## Response (응답)
서버가 요청에 대한 답변을 클라이언트에게 보내는 것

### Status Code (상태 코드)
상태 코드에는 굉장히 많은 종류가 있다. 모두 숫자 세 자리로 이루어져 있으며, 아래와 같이 크게 다섯 부류로 나눌 수 있다.

- 1XX (조건부 응답) : 요청을 받았으며 작업을 계속한다.
- 2XX (성공) : 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며 성공적으로 처리했음을 가리킨다.
- 3XX (리다이렉션 완료) : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
- 4XX (요청 오류) : 클라이언트에 오류가 있음을 나타낸다.
- 5XX (서버 오류) : 서버가 유효한 요청을 명백하게 수행하지 못했음을 나타낸다.

### Response HTTP 메시지 예시

>HTTP/1.1 200 OK														// 시작줄  
>Connection: keep-alive												 // 헤더  
>Content-Encoding: gzip												   
>Content-Length: 35653  
>Content-Type: text/html;  
>  
><!DOCTYPE html><html lang="ko" data-reactroot=""><head><title...

### 1. 시작줄 (첫 줄)
버전 상태코드 상태메시지로 구성  
200은 성공적인 요청

### 2. 헤더 (두 번째 줄부터)
헤더로 응답에 대한 정보

### 3. 본문 (헤더 뒤부터)
응답에는 대부분의 경우 본문이 있다.  
보통 데이터를 요청하고 응답 메시지에는 요청한 데이터를 담아서 보내주기 때문이다.  
응답 메시지에 HTML이 담겨 있는데 이 HTML을 받아 브라우저가 화면에 렌더링 한다.

### Chrome에서 HTTP header확인하기
1. Chorme에서 개발자 도구창 열기(F12 또는 Ctrl+Shift+I)
2. Network 클릭
3. 하단의 Name에서 url를 클릭하면 Header확인 가능
4. 주소를 https에서 http로 변경하면 더 자세히 알 수 있다.
#### Response HTTP Message
<img src="https://user-images.githubusercontent.com/101981594/166188990-419d3a9d-e72e-48db-aa21-140a2115de4a.jpg" width="800px" height="450px"/>

#### Request HTTP Message
<img src="https://user-images.githubusercontent.com/101981594/166188969-8f8a2377-7f99-4e28-9156-effe43720504.jpg" width="800px" height="450px"/>