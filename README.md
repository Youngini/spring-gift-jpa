# spring-gift-product

## 기능 요구 사항
상품을 조회, 추가, 수정, 삭제할 수 있는 간단한 HTTP API를 구현한다.

- HTTP 요청과 응답은 JSON 형식으로 주고받는다.
- 현재는 별도의 데이터베이스가 없으므로 적절한 자바 컬렉션 프레임워크를 사용하여 메모리에 저장한다.

## 구현할 기능 목록

[] 상품 데이터를 메모리에 저장해야한다.

  [] 상품 데이터를 저장하기 위한 Product class를 생성한다.
    - id : primary key 상품 데이터를 찾기 위한 data
    - name : 상품명을 저장하기 위한 data
    - price : 상품의 가격을 저장하기 위한 data
    - description : 상품의 설명을 저장하기 위한 data
    
  [] 상품 데이터를 저장하기 위한 Map<Long, Product> 객체를 생성한다.

[] 상품을 추가하는 HTTP API를 구현한다.
  [] 상품 추가 시, 상품 id는 자동 생성된다.
  [] 상품을 추가하기 위해서는 name, price, description은 필수로 입력해야한다.
  [] 상품 추가를 위해, client에게 상품의 정보(name, price, description)을 전달받는다.
  [] 상품 추가가 성공하면 200 ok를 전달한다.
  [] 상품 정보 중 일부를 미입력해서 상품 추가가 실패한 경우, 400 "상품 정보를 모두 입력해야합니다." 를 전달한다.

[] 상품을 조회하는 HTTP API를 구현한다.
  [] 상품은 상품 id로 조회한다.
  [] 상품 조회를 위해, client에게 상품 id를 전달 받는다.
  [] 상품 조회가 성공적으로 이루어졌다면 상품의 정보(name, price, description)를 전달한다.
  [] 상품이 존재하지 않아 상품 조회가 실패했다면 400 " 일치하는 상품이 없습니다" 를 전달한다.

[] 상품을 수정하는 HTTP API를 구현한다.
  [] 수정할 상품은 상품 id로 조회한다.
  [] 상품을 수정할 때, client에서 상품 id, name, price, description을 전달한다.
  [] client에서 전달받은 데이터들로 상품 정보들을 수정한다.
  [] 수정이 성공적으로 완료되면 200, ok를 보낸다.
  [] 수정이 실패한 경우 오류 메시지를 보낸다.

[] 상품을 삭제하는 HTTP API를 구현한다.
  [] 상품 삭제는 상품 id로 데이터를 조회해서 삭제한다.
  [] 상품을 삭제하기 위해, client에게 상품 id를 전달 받는다.
  [] 상품 삭제에 성공하면 200 ok를 전달한다.
  [] 상품 삭제 중 해당 아이디의 상품이 조회가 안되서 삭제가 안된 경우, 400 "상품이 존재하지 않습니다"를 전달한다.
