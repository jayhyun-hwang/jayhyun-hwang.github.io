- API란
  - Application Programming Interface
  - 프로그램들이 서로 상호작용하는 것을 도와주는 매개체
  - 서버와 DB에 대한 출입구 역할
  - 어플리케이션과 기기가 원할하게 통신할 수 있도록 해줌
  - 모든 접속을 **표준화**한다. - standarize format
  - endpoint
    - URL
    - 자원을 요청하는 신호
- GraphQL
  - facebook이 만든 새로운 API 표준
  - 데이터 주고받기 가능
  - Graph + Query Language
  - endpoint가 1개
    - 쿼리 객체의 형태로 요청
  - Overfetching 과 Underfetching 이 없음.
    - Overfetching : 불필요한 데이터까지 다 받아오는 것
    - Underfetching : endpoint가 데이터를 덜 받아와서 요청을 여러번 날리는 것
  - Static Custom Type
    - 백엔드에서 스키마 타입을 정함
  - 프론트에서 데이터 구조를 쉽게 볼 수 있다.
  - 

- 페이로드 payload

  - response 중 통신의 목적이 되는 **body data**(헤더 제외)
  - 가장 흥미로운 데이터라는 의미
    - "status"는 프로토콜 오버헤드
    - "data"가 **payload**

  ```json
  {
      "status":"OK",
      "data": {
          "message": "It's response, over."
      }
  }
  ```

  