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
| API 명  | 방식 | 파라미터 명 | 파라미터 타입 | 파라미터 설명 | 
| ------------- | --------- | ------------- | ------------- | ------------- |
| getList  |  GET  | pageRequestDTO | PageRequestDTO  | page, size 정보와 검색 type, keyword를 포함한 DTO |
| register  | POST  | dto  | GuestbookDTO  | gno, title, content, writer, regDate, modDate를 포함한 DTO|
| read | GET | gno | Long | 방명록 게시 글의 고유 번호 |
| modify | POST | dto  | GuestbookDTO  | gno, title, content, writer, regDate, modDate를 포함한 DTO |
| remove | POST | gno | Long | 방명록 게시 글의 고유 번호 |

<br /><br /><br /><br /><br />
# 3. ER Diagram
![image](https://user-images.githubusercontent.com/74942574/180776614-491e7fae-152c-420c-8003-7d363b623ef8.png)
