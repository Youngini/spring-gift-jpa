# spring-gift-jpa

# 1단계 과제

## 기능 요구 사항
- 지금까지 작성한 JdbcTemplate 기반 코드를 JPA로 리팩터링하고 실제 도메인 모델을 어떻게 구성하고 객체와 테이블을 어떻게 매핑해야 하는지 알아본다.

- 아래의 DDL(Data Definition Language)을 보고 유추하여 엔티티 클래스와 리포지토리 클래스를 작성해 본다.
- @DataJpaTest를 사용하여 학습 테스트를 해 본다.
  ```
    create table member
    (
    id       bigint generated by default as identity,
    email    varchar(255) not null unique,
    password varchar(255) not null,
    primary key (id)
    )
  ```
  ```
    create table product
    (
    price     integer      not null,
    id        bigint generated by default as identity,
    name      varchar(15)  not null,
    image_url varchar(255) not null,
    primary key (id)
    )
  ```
  ```
    create table wish
    (
    id         bigint generated by default as identity,
    member_id  bigint not null,
    product_id bigint not null,
    primary key (id)
    )
  ```
## 구현할 기능 목록
- [x] JDBCTemplate 기반 코드 JPA로 리팩토링

  - [x] JPA 사용을 위한 dependencies 추가
  
  - [x] 엔티티 클래스 작성
    - [x] member table
      - [x] id(Long, key), email(Varchar, unique), password(Varchar)
    - [x] product
      - [x] id(Long, key), price(Integer, 0이상), name(Varchar, not null), image_url(Varchar, not null) 
    - [x] wish
      - [x] id(Long, key), member_id(Long, not null), product_id(Long, not null)
      
  - [x] 리포지토리 인터페이스 작성
    - [x] MemberRepository 인터페이스 작성
    - [x] ProductRepository 인터페이스 작성
    - [x] WishRepository 인터페이스 작성
  
  - [x] 리포지토리 구현체 작성
    - [x] MemberRepositoryImpl 클래스 작성
    - [x] ProductRepositoryImpl 클래스 작성
    - [x] WishRepositoryImpl 클래스 작성
    
- [x] 동작 쿼리를 로그로 확인하도록 property 설정

- [x] MySQL Dialect을 사용을 위한 property 추가

- [ ] 학습 테스트 작성
  - [ ] @DataJpaTest 어노테이션을 사용하여 테스트 클래스 작성
    - [x] MemberRepositoryTest 작성
    - [x] ProductRepositoryTest 작성 
    - [ ] WishRepositoryTest 작성

## 1주차 과제 피드백
- [x] spring Security 관련 내용 삭제 및 비활성화
  - [x] build 파일에서 관련 내용 비활성화
  - [x] 사용하지 않는 로직 삭제
- [x] MemberController header key 변경
- [x] 공통 Exception을 ControllerAdvice로 고치기

# 2단계 과제

## 기능 오구 사항
- 지금까지 작성한 JdbcTemplate 기반 코드를 JPA로 리팩터링하고 실제 도메인 모델을 어떻게 구성하고 객체와 테이블을 어떻게 매핑해야 하는지 알아본다.
- 객체의 참조와 테이블의 외래 키를 매핑해서 객체에서는 참조를 사용하고 테이블에서는 외래 키를 사용할 수 있도록 한다.

## 구현할 기능 목록
- [x] 엔티티 구현
  - [x] Member에 wish 참조키 설정 (1 : N)
  - [x] Product에 wish 참조키 설정 (1 : N)
  - [x] Wish에 Member와 Product의 참조키 설정 (N : 1)
  - [x] wish가 삭제되면 해당 wish가 자동 삭제되도록 리팩토링
- [x] 서비스 계층 수정 사항 수정

## 수정 사항
- [x] GlobalExceptionHandler - Exception에 코드 등을 넣어서 에러메시지 대신 사용
- [x] Repository - JPA에서 자동으로 만들어줘서 구현안해도되는 코드 삭제
- [x] LoginMemberArgumentResolver - 토큰 파싱 시, 문자 길이로 값 사용해보기
- [x] JwtTokenProvider - 변수명으로 86400000 수정
- [x] 테스트 코드 수정 - 저장하고 repository에서 불러와보기

# 3단계 과제

## 기능 요구 사항
- 상품과 위시 리스트 보기에 페이지네이션을 구현한다.

- 대부분의 게시판은 모든 게시글을 한 번에 표시하지 않고 여러 페이지로 나누어 표시한다. 정렬 방법을 설정하여 보고 싶은 정보의 우선 순위를 정할 수도 있다.
- 페이지네이션은 원하는 정렬 방법, 페이지 크기 및 페이지에 따라 정보를 전달하는 방법이다.

## 구현할 기능 목록
- [x] 상품 목록 페이지 구현
  - [x] 상품 목록을 페이지로 나눠서 표시
    - [x] Product의 findall() 에  pageable 메서드 추가
      - [x] Controller에도 페이지 네이션 관련 파라미터 추가
    - [x] Service에도 페이지네이션 관련 파라미터 추가
  - [x] 페이지 번호 및 이동 기능 제공
  - [x] 정렬 기능 제공 (가격, 상품명 등)
- [x] 위시리스트 페이지 구현
  - [x] 위시리스트 상품 목록을 페이지로 나눠서 표시
  - [x] 페이지 번호 및 이동 기능 제공
  - [x] 정렬 기능 제공 (상품명, 가격 증)

## 피드백 반영
- [ ] JwtConfig : JwtTokenProvider 코드를 분리하기 보다는 메서드로 호출하도록 구현
- [ ] WebConfig : 실제 사용하는 코드인지 한번 디버깅
- [ ] MemberController : 설정값 한곳에 모으기
- [ ] MemberService : 사용자 토큰 사용
- [ ] ProductService : 메서드 사용해서 깔끔하게 정의하기
- [ ] proporties : 파일 저장 UTF-8인지 확인
- [ ] Test : 사용하는 값들 상단 변수로 등록해서 사용해보기