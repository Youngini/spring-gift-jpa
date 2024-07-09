# spring-gift-product

# 1단계 과제

## 기능 요구 사항
상품을 조회, 추가, 수정, 삭제할 수 있는 간단한 HTTP API를 구현한다.

- HTTP 요청과 응답은 JSON 형식으로 주고받는다.
- 현재는 별도의 데이터베이스가 없으므로 적절한 자바 컬렉션 프레임워크를 사용하여 메모리에 저장한다.

## 구현할 기능 목록

- [x] 상품 데이터를 메모리에 저장해야한다.

  - [x] 상품 데이터를 저장하기 위한 Product class를 생성한다.</br>
    - id : primary key 상품 데이터를 찾기 위한 data </br>
    - name : 상품명을 저장하기 위한 data </br>
    - price : 상품의 가격을 저장하기 위한 data </br>
    - description : 상품의 설명을 저장하기 위한 data </br>
    - imageUrl : 상품의 이미지를 저장하기 위한 data </br>
    
  - [x] 상품 데이터를 저장하기 위한 Map<Long, Product> 객체를 생성한다.

- [X] 상품을 추가하는 HTTP API를 구현한다.
  - [X] 상품 추가 시, 상품 id는 자동 생성된다.
  - [X] 상품을 추가하기 위해서는 name, price, description은 필수로 입력해야한다.
  - [X] 상품 추가를 위해, client에게 상품의 정보(name, price, description)을 전달받는다.
  - [X] 상품 추가가 성공하면 200 ok를 전달한다.
  - [X] 상품 정보 중 일부를 미입력해서 상품 추가가 실패한 경우, "상품 정보를 모두 입력해야합니다." 를 전달한다.

- [x] 전체 상품을 조회하는 HTTP API를 구현한다.
  - [x] 상품 조회가 성공적으로 이루어졌다면 상품의 정보(id, name, price, description)를 리스트들로 전달한다.
  - [x] 상품이 존재하지 않아 상품 조회가 실패했다면, "존재하는 상품이 없습니다." 를 전달한다.

- [x] 특정 상품을 조회하는 HTTP API를 구현한다.
  - [x] 상품은 상품 id로 조회한다.
  - [x] 상품 조회를 위해, client에게 상품 id를 전달 받는다.
  - [x] 상품 조회가 성공적으로 이루어졌다면 상품의 정보(name, price, description)를 전달한다.
  - [x] 상품이 존재하지 않아 상품 조회가 실패했다면, " 일치하는 상품이 없습니다" 를 전달한다.

- [x] 상품을 수정하는 HTTP API를 구현한다.
  - [x] 수정할 상품은 상품 id로 조회한다.
  - [x] 상품을 수정할 때, client에서 상품 id, name, price, description을 전달한다.
  - [x] client에서 전달받은 데이터들로 상품 정보들을 수정한다.
  - [x] 수정이 성공적으로 완료되면 200, ok를 보낸다.
  - [x] 수정이 실패한 경우 오류 메시지를 보낸다.

- [x] 상품을 삭제하는 HTTP API를 구현한다.
  - [x] 상품 삭제는 상품 id로 데이터를 조회해서 삭제한다.
  - [x] 상품을 삭제하기 위해, client에게 상품 id를 전달 받는다.
  - [x] 상품 삭제에 성공하면 200 ok를 전달한다.
  - [x] 상품 삭제 중 해당 아이디의 상품이 조회가 안되서 삭제가 안된 경우, "상품이 존재하지 않습니다"를 전달한다.

---

# 2단계 과제

## 기능 요구 사항
상품을 조회, 추가, 수정, 삭제할 수 있는 관리자 화면을 구현한다.

- Thymeleaf를 사용하여 서버 사이드 렌더링을 구현한다.
- 기본적으로는 HTML 폼 전송 등을 이용한 페이지 이동을 기반으로 하지만, 자바스크립트를 이용한 비동기 작업에 관심이 있다면 이미 만든 상품 API를 이용하여 AJAX 등의 방식을 적용할 수 있다.
- 상품 이미지의 경우, 파일을 업로드하지 않고 URL을 직접 입력한다.

## 구현할 기능 목록
- [ ] 전체 페이지
  - [ ] 모든 왼쪽 페이지 상단에 main 페이지로 돌아갈 수 있는 버튼이 존재한다.

- [x] Main page (메인 페이지)
  - [x] 전체 상품 리스트를 볼 수 있다.
    - [x] 상품의 이름, 가격만 표시한다.
  - [x] 상품 추가 버튼 클릭 시 상품 추가 페이지로 이동한다.
  - [x] 상품 삭제 버튼 클릭 시 상품 삭제 확인 모달창을 띄운다.
  - [x] 상품 수정 버튼 클릭 시 상품 수정 페이지로 이동한다.
  - [x] 상품 클릭 시 상품 상세 보기 페이지로 이동한다.
  - [x] 리스트 한 줄에 상품명, 가격, 수정버튼, 삭제버튼 있도록 구성한다.
  - [x] 상품 리스트 10개씩 보이게하고, 10개 넘으면 다음 페이지에서 확인할 수 있도록 구성한다.
  - [x] 왼쪽 페이지 상단에 main 페이지로 돌아갈 수 있는 버튼이 존재한다.
- [x] ProductAdd page(상품 추가 페이지)
  - [x] 상품 이름 입력 칸 생성한다.
  - [x] 상품 가격 입력 칸 생성한다.
  - [x] 상품 이미지 입력 칸 생성한다.
  - [x] 상품 설명 입력 칸 생성한다.
  - [x] 상품 등록 버튼 클릭 시, 상품 등록 완료 모달창을 띄우고 상품 상세 페이지로 이동한다.
  - [x] 왼쪽 페이지 상단에 main 페이지로 돌아갈 수 있는 버튼이 존재한다.


-[ ] ProductView page(상품 상세 정보 확인 페이지)
  - [x] 상품 이름, 상품 가격, 상품 이미지, 상품 설명 표시한다.
  - [ ] 상품 수정 버튼 클릭시, 상품 수정 페이지로 이동한다.
  - [x] 상품 삭제 버튼 클릭시, 상품 삭제 확인 모달창을 띄운다.
  - [x] 왼쪽 페이지 상단에 main 페이지로 돌아갈 수 있는 버튼이 존재한다.

-[x] ProductUpdate page(상품 정보 업데이트 페이지)
  - [x] 원래의 상품 이름, 상품 가격, 상품 이미지, 상품 설명을 채워놓는다.
  - [x] 상품 이름, 가격, 이미지, 설명을 수정할 수 있도록 한다.
  - [x] 상품 수정 완료 버튼을 누르면, 상품 상세 페이지로 넘어간다.
  - [x] 상품 수정 취소 버튼을 누르면, 이전 페이지로 돌아간다.
  - [x] 왼쪽 페이지 상단에 main 페이지로 돌아갈 수 있는 버튼이 존재한다.

---
# 3단계 과제 : DB 사용하기

## 기능 요구 사항
자바 컬렉션 프레임워크를 사용하여 메모리에 저장하던 상품 정보를 데이터베이스에 저장한다.

## 프로그래밍 요구 사항
메모리에 저장하고 있던 모든 코드를 제거하고 H2 데이터베이스를 사용하도록 변경한다.
사용하는 테이블은 애플리케이션이 실행될 때 구축되어야 한다.

## 구현할 기능 목록 

- [x] 데이터베이스 설정
  - [x] H2 데이터베이스 설정
  - [x] 필요한 테이블 구조 정의 및 생성

- [x] 상품 정보 관리 controller
  - [x] 상품 정보 입력/저장
  - [x] 상품 정보 조회
  - [x] 상품 정보 수정
  - [x] 상품 정보 삭제

- [x] 상품 정보 데이터베이스 CRUD (Create, Read, Update, Delete) 구현
  - [x] 상품 정보 생성 (Create)
  - [x] 상품 정보 조회 (Read)
  - [x] 상품 정보 수정 (Update)
  - [x] 상품 정보 삭제 (Delete)

- [x] 기존 메모리 기반 코드 수정
  - [x] 메모리에 저장하던 상품 정보 관련 코드 삭제
  - [x] 데이터베이스 기반 코드로 전환

- [x] 애플리케이션 실행 시 테이블 자동 생성
  - [x] 애플리케이션 실행 시 데이터베이스 테이블 자동 생성 기능 구현

- [x] 예외 처리 및 오류 처리
  - [x] 데이터베이스 연결 실패, 쿼리 실행 실패 등의 예외 처리
  - [x] 적절한 오류 메시지 출력

- [x] 테스트 및 검증
  - 각 기능별 단위 테스트 수행
  - 통합 테스트를 통한 전체 시스템 검증

## 나중에 시도해볼 것
- [ ] 성능 및 효율성 고려
  - [ ] 데이터베이스 연결 및 쿼리 실행 최적화
  - [ ] 필요한 경우 인덱스 생성 등의 성능 향상 방안 고려

# spring-gift-whishlist

## 0딘계 과제 : 피드백 반영

## 반영할 피드백
- [x] Product.java 에서 빈 생성자를 사용하지 않는데 만든 이유
  - [x] ProductService의 CreateProduct에서 빈 class를 만든 다음, 거기에 넣는 식으로 했는데 말씀해주신대로 생각해보니 생성자를 만들면서 값을 바로 설정해줄 수 있어서 그렇게 수정하였습니다.
- [x] UpdateProductDto 에서 objectType을 사용한 이유
  - [x] Spring의 자동 완성 기능을 종종 사용하는데 아무 생각없이 사용하다가 그렇게 적용됐고, 코드가 실행되서 제대로 확인을 안한것같습니다. 각 타입에 맞게 수정하였습니다.
- [x] Validation 주석 지우기
- [x] JdbcProductRepository.java에서 SimpleJdbcInsert 사용해보기
- [x] ProductService에서 불필요한 주석 지우기
- [x] Try catch문 대신, ControllerAdvice 사용해보기

---

## 1단계 과제 :유효성 검사 및 예외 처리

## 기능 요구 사항
- 상품을 추가하거나 수정하는 경우, 클라이언트로부터 잘못된 값이 전달될 수 있다. 
- 잘못된 값이 전달되면 클라이언트가 어떤 부분이 왜 잘못되었는지 인지할 수 있도록 응답을 제공한다.

- 상품 이름은 공백을 포함하여 최대 15자까지 입력할 수 있다.
- 특수 문자  
  - 가능: ( ), [ ], +, -, &, /, _
  - 그 외 특수 문자 사용 불가
  - "카카오"가 포함된 문구는 담당 MD와 협의한 경우에만 사용할 수 있다.

## 구현할 기능 목록
상품 추가/수정 시 잘못된 값 전달에 대한 응답 제공 요구사항을 구현하기 위해 다음과 같은 목록을 정리할 수 있습니다:

- [x] 상품 이름 길이 검증
  - [x] 상품 이름은 최대 15자까지 입력할 수 있도록 검증
  - [x] 길이가 15자를 초과하는 경우 에러 메시지 반환

- [x] 상품 이름 특수 문자 검증
  - [x] 허용된 특수 문자 ( ), [ ], +, -, &, /, _ 만 사용할 수 있도록 검증
  - [x] 허용되지 않은 특수 문자가 포함된 경우 에러 메시지 반환

- [x] "카카오" 포함 문구 검증
  - [x] "카카오"가 포함된 문구는 담당 MD와 협의한 경우에만 사용할 수 있도록 검증
  - [x] "카카오"가 포함된 경우 에러 메시지 반환

- [x] 잘못된 입력 값에 대한 에러 메시지 반환
  - [x] 각 검증 단계에서 발생한 에러에 대한 정보를 클라이언트에게 제공
  - [x] 예를 들어, 상품 이름 길이가 초과된 경우 "상품 이름은 최대 15자까지 입력할 수 있습니다."와 같은 메시지 반환

- [x] Spring Validation 활용
  - [x] spring-boot-starter-validation 의존성을 추가하여 Spring Validation 활용
  - [x] 상품 이름 길이, 특수 문자, "카카오" 포함 문구 검증을 위한 Validator 구현

- [x] 예외 처리 및 응답 포맷팅
  - [x] 검증 과정에서 발생한 예외를 처리하여 적절한 HTTP 상태 코드와 에러 메시지를 반환
  - [x] 에러 메시지를 일관된 포맷으로 제공하여 클라이언트가 이해하기 쉽도록 함

---
## 2단계 : 회원 로그인

## 기능 요구 사항
- 사용자가 회원 가입, 로그인, 추후 회원별 기능을 이용할 수 있도록 구현한다.

  - 회원은 이메일과 비밀번호를 입력하여 가입한다.
  - 토큰을 받으려면 이메일과 비밀번호를 보내야 하며, 가입한 이메일과 비밀번호가 일치하면 토큰이 발급된다.
  - 토큰을 생성하는 방법에는 여러 가지가 있다. 방법 중 하나를 선택한다.
  - (선택) 회원을 조회, 추가, 수정, 삭제할 수 있는 관리자 화면을 구현한다.
  - 아래 예시와 같이 HTTP 메시지를 주고받도록 구현한다.

    - 회원 가입
      - Request
      ```
        POST /members/register HTTP/1.1
        content-type: application/json
        host: localhost:8080
      
        {
          "email": "admin@email.com",
          "password": "password"
        }
      ```
      - Response
      ```
        HTTP/1.1 200
        Content-Type: application/json
      
        {
          "token": ""
        }
      ```
    - 로그인
      - Request
      ```
      POST /members/login HTTP/1.1
      content-type: application/json
      host: localhost:8080
  
      {
      "email": "admin@email.com",
      "password": "password"
      }
      ```
      - Response
      ```
        HTTP/1.1 200
        Content-Type: application/json
            
      {
      "token": ""
      }
      ```

## 프로그래밍 요구 사항
- 힌트
  - Basic 인증
  - Base64로 인코딩된 사용자 ID, 비밀번호 쌍을 인증 정보(credentials) 값으로 사용한다.

  - Authorization: Basic base64({EMAIL}:{PASSWORD})
  - JSON Web Token
  - JJWT 라이브러리를 사용하여 JWT을 쉽게 만들 수 있다.
```
  dependencies {
    compileOnly 'io.jsonwebtoken:jjwt-api:0.12.6'
    runtimeOnly 'io.jsonwebtoken:jjwt-impl:0.12.6'
    runtimeOnly 'io.jsonwebtoken:jjwt-jackson:0.12.6'
  }
 ```
```
  String secretKey = "Yn2kjibddFAWtnPJ2AFlL8WXmohJMCvigQggaEypa5E=";
  String accessToken = Jwts.builder()
  .setSubject(member.getId().toString())
  .claim("name", member.getName())
  .claim("role", member.getRole())
  .signWith(Keys.hmacShaKeyFor(secretKey.getBytes()))
  .compact();
```

### 응답 코드
- Authorization 헤더가 유효하지 않거나 토큰이 유효하지 않은 경우 401 Unauthorized를 반환한다.
- 401 Unauthorized 클라이언트 오류 상태 응답 코드는 해당 리소스에 유효한 인증 자격 증명이 없기 때문에 요청이 적용되지 않았음을 나타냅니다. 이 상태는 WWW-Authenticate (en-US) 헤더와 함께 전송되며, 이 헤더는 올바르게 인증하는 방법에 대한 정보를 포함하고 있습니다. 이 상태는 403과 비슷하지만, 401 Unauthorized의 경우에는 인증이 가능합니다.

- 잘못된 로그인, 비밀번호 찾기, 비밀번호 변경 요청은 403 Forbidden을 반환한다.
- HTTP 403 Forbidden 클라이언트 오류 상태 응답 코드는 서버에 요청이 전달되었지만, 권한 때문에 거절되었다는 것을 의미합니다. 이 상태는 401과 비슷하지만, 로그인 로직(틀린 비밀번호로 로그인 행위)처럼 반응하여 재인증(re-authenticating)을 하더라도 지속적으로 접속을 거절합니다.

## 구현할 기능 목록
- [x] 회원가입 기능
  - [x] 이메일, 비밀번호를 입력하여 가입한다.
  - [x] 이메일은 중복되지 않아야한다.
  - [x] 이메일이 중복된 경우, 오류 메시지를 보낸다.
  - [x] 비밀번호는 암호화되어 저장된다.
  
- [x] 로그인 기능
  - [x] 토큰을 받기 위해 이메일과 비밀번호를 보낸다.
  - [x] 이메일과 비밀번호 중 하나도 일치하지 않으면 오류 메시지를 전달환다.
  - [x] 로그인 성공 시, 토큰을 전달한다.
  
- [x] 토큰을 사용하기 위한 환경을 구성
  - [x] build.gradle에 의존성 추가
  - [x] 토큰을 다루기 위한 코드 작성

## 추가할 기능
- [ ] 회원 가입 기능
  - [ ] 이메일, 비밀번호 말고도 이름, 성별, 생년월일, 전화번호와 같은 정보들을 추가한다.
  - [ ] 전화번호는 중복되지 않아야 한다.
- [ ] 회원 CRUD
  - [ ] 전체 회원 조회
  - [ ] 특정 회원 조회
  - [ ] 특정 회원 수정
  - [ ] 특정 회원 삭제
  
---

## 3단계 : 위시리스트 
## 기능 요구 사항
- 이전 단계에서 로그인 후 받은 토큰을 사용하여 사용자별 위시 리스트 기능을 구현한다.

- 위시 리스트에 등록된 상품 목록을 조회할 수 있다.
- 위시 리스트에 상품을 추가할 수 있다.
- 위시 리스트에 담긴 상품을 삭제할 수 있다.

## 구현할 기능 목록
- [x] 위시 리스트 관련 엔티티 및 리포지토리 구현
  - [x] Wish 엔티티 생성 (userId, productId, createdAt 필드 포함)
  - [x] WishRepository 인터페이스 생성 및 구현

- [x] WishService 생성 및 구현
  - [x] 위시 리스트 조회 
  - [x] 위시 리스트에 상품 추가 
  - [x] 위시 리스트에서 상품 삭제

- [x] WishController 생성
  - [x] GET /wishes: 위시 리스트 조회 
  - [x] POST /wishes: 위시 리스트에 상품 추가 
  - [x] DELETE /wishes/{id}: 위시 리스트에서 상품 삭제 
  
- [x] 사용자 인증 및 인가 처리
  - [x] 요청 헤더의 Authorization 필드를 통해 사용자 정보 추출
  - [x] 추출한 사용자 정보를 컨트롤러 메서드에 주입

- [ ] 예외 처리 및 응답 코드 설정
  - [ ] 위시 리스트 관련 예외 처리 (상품 중복 추가, 존재하지 않는 상품 삭제 등)

- [ ] HTTP 응답 코드 설정 (200 OK, 201 Created, 404 Not Found 등)

## 피드백
- [x] 인증 처리를 여전히 여러 서비스들을 컨트롤러에서 하는 문제 
  - [x] 비지니스 로직은 서비스 내부로 정리하기
- [ ] SpringSecurity가 필수가 아님 
  - [ ] 단순한 인증 인가
  - [ ] Resolver를 컴포넌트 계층단위로 구분


