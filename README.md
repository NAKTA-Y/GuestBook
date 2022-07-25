# GuestBook
코드로 배우는 스프링 부트 웹 프로젝트 Part2 실습
<br /><br /><br /><br /><br />
# 1. 요구사항
* 사용자는 글을 등록할 수 있어야한다.
* 사용자는 작성된 글을 조회할 수 있어야한다.
* 사용자는 언제든지 작성한 글을 수정, 삭제할 수 있어야한다.
* 사용자는 제목, 내용, 작성자, 제목 + 내용, 제목 + 내용 + 작성자 타입으로 검색할 수 있어야한다.
* 사용자는 페이지 별로 작성된 글을 조회할 수 있어야한다.
<br /><br /><br /><br /><br />
# 2. API 규격서
| API 명  | 방식 | 변수 타입 | 리턴 타입  | API 설명 | API 작동원리 |
| ------------- | --------- | ------------- | ------------- | ------------- | ------------- | 
| getList  |  GET  | PageRequestDTO  | PageResultDTO<GuestbookDTO, Guestbook>  | PageRequestDTO에 page 번호와 검색 조건 type, keyword를 서버에게 요청하여 해당 결과를 얻을 수 있다. 이때 결과는 QueryDSL을 이용하여 데이터베이스에서 해당 조건에 맞는 데이터를 추출하여 가져온다. | page=4&type=t&keyword=9 (요청)<br /><br />PageRequestDTO (저장) <br /><br /> PageResultDTO (전달)
| register  | POST  | GuestbookDTO  | Long  |  사용자는 글을 작성하여 서버에 POST 방식으로 DTO 데이터를 전달하고, 서버는 해당 데이터를 Entity로 변환하여 데이터베이스에 저장한다. | title='test', content='test', writer='test' (전달) <br /><br /> GuestbookDTO (저장) <br /><br /> dtoToEntity (데이터 저장)|
| read | GET | Long | GuestbookDTO | 등록된 글을 클릭하면 해당 gno에 맞게 데이터베이스에서 해당 Entity를 DTO로 변환하여 반환해준다. 이때, 해당 gno에 맞는 Entity가 없으면 null을 반환한다. | gno = 123 (요청) <br /><br /> finById (데이터 탐색) <br /><br /> GuestbookDTO (저장 후 전달)
| modify | POST | GuestbookDTO | void | 등록된 글을 수정하여 해당 데이터를 DTO 형태로 저장하여 POST 방식으로 서버에게 전달하면 서버는 DTO를 참조하여 데이터를 수정한다. | title='modify' content='modify' (전달) <br /><br /> GuestbookDTO (저장) <br /><br /> findById (데이터 탐색) <br /><br /> dtoToEntity (수정 후 저장)
| remove | POST | Long | void | 사용자는 작성된 글의 gno를 서버에 전달하여 서버는 해당 gno를 데이터베이스를 탐색하여 찾아 삭제한다. | gno=123 (전달) <br /><br /> deleteById (탐색 후 삭제)
