# JSP Servlet semi Project
SNS처럼 자신의 노래 취향을 공유하는 y2k 컨셉의 사이트를 구현해봤습니다.

![01](https://github.com/Yim-HaEun/semi_Project/assets/49932613/2123dea3-1f2c-49c3-9d35-a01adb64447f)

## 기술 스택
<div>
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"/>
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
<img src="https://img.shields.io/badge/oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white"> 
<img src="https://img.shields.io/badge/apache tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black"> 
</div>
## Shinee 조 <br/>
<div>
<p>
-팀장 : 서광원 -[회원가입] 정규식조건 체크,아이디 중복체크 <br/>
-팀원1 : 나세희 [로그인/둘러보기]음악,플레이리스트,유저 검색, 플레이리스트에 음악 추가, 유저 검색 후 팔로우<br/>
<strong>-팀원2 : 임하은 [마이플레이리스트]플레이리스트 생성 ,플레이리스트 삭제,내 플레이리스트 detail</strong><br/>
-팀원3 : 안승애 [마이페이지]회원정보 확인, 팔로잉 목록, 로그아웃, 회원 탈퇴, 회원정보 수정<br/>
</p>
</div>


<br>


<br>

## 구현 기능:
회원가입,로그인 : 1.정규식 조건 체크 2.아이디 중복 체크  3.회원 DB 추가
둘러보기 : 1.음악검색 2.플레이리스트 검색 3.유저 검색 4.음악 검색 후 플레이리스트에 음악 추가 5.유저 검색 후 팔로우
마이 플레이리스트 : 1.플레이리스트 생성 2.플레이리스트 삭제 3.플레이리스트 내 노래 목록 자세히 보기
마이페이지 : 1.회원 정보 확인 2.마이 플레이리스트 목록 3.팔로잉 목록 4.로그아웃 5.회원 탈퇴


### 기능 1 : 플레이리스트 생성

![myplaylist](https://github.com/Yim-HaEun/semi_Project/assets/49932613/c4d614aa-cc08-460c-a8a4-760348fcc8cd)

<p>로그인 후, 바로 Myplaylist 페이지가 뜨며</p>
![new](https://github.com/Yim-HaEun/semi_Project/assets/49932613/72810278-9a65-4f68-9de3-217546ea7c56)
<p>NEW 버튼을 누르면 공유할 플레이리스트를 생성할 수 있다.</p><br/>

<p>플리 생성 페이지</p>
![createmy](https://github.com/Yim-HaEun/semi_Project/assets/49932613/037be969-a2e8-45f9-8682-b3cacdf6e9a3)

### 기능 2 : 플레이리스트 삭제
![delete](https://github.com/Yim-HaEun/semi_Project/assets/49932613/4411d855-b20d-4270-9af6-6d9d5f3eb67d)

### 기능 3 : 플레이리스트 내 노래 목록 자세히 보기
![detail](https://github.com/Yim-HaEun/semi_Project/assets/49932613/cefb17cf-ed62-4dd0-95d9-b04a5b897e72)


![list1](https://github.com/Yim-HaEun/semi_Project/assets/49932613/ecbd498a-bc4e-4231-962e-729b8097f011)





<br>

## 배운 점 & 아쉬운 점

<p align="justify">
-프로젝트를 진행하며 배운 부분: <br/>
 db를 연결하여 데이터들을 불러오고 실제로 구현하면서 그 과정들과 동작을 배웠다. 
 버튼을 누르면 사이트를 불러와 페이지를 넘기는것 (form action을 활용하여 기능 구현)을 하였고
 데이터 저장 및 조회, 삭제를 할 수 있게 되었다.
<br/>
-아쉬웠던 점 : <br/>
프로젝트를 합치는 과정에서 오류가 발생하면서 일정에 문제가 생겼었다. 프로젝트 진행 중에 서로의 것을 완성한 뒤 합치면 된다는 생각에 오류를 잡는 기간을 생각못했던 것.


	
##에러해결(trouble shooting):

-DB에서 시퀸스 설정을 제대로 해도, 값이 2씩 넘어가는 에러가 있었다. 
 증감 값을 다시 설정 해줌
2개의 플리를 임의로 생성해놨을 때, 다음 시작점이 5로 설정되어있어서 다시 시작점을 재설정하고 빈 값(시퀸스 1)에 임의로 값을 넣어 해결함
1.alter sequence 시퀀스명increment by -4; (초기값을 0으로 만들면 안됨)
2.변경된 값을 적용 : select 시퀀스명.nextval from dual;
3.기존 값으로 증감 값 변경 : alter sequence 시퀀스명 increment by 1;
4.테이블 컬럼 에서 열 1번 값을 직접 삽입:
create table 테이블명(컬럼명 number);
insert into 테이블명(컬럼명) values(1);
5.이 후 nextval을 이용해 넘버링
insert into 테이블명(컬럼명) values(시퀀스명.nextvalue);

-INSERT 문을 이용해 플레이리스트를 생성할 때, SQL문에서 VALUES 오타로 인해 DB에 저장이 안됐었다.
생성버튼을 누르면 다시 플레이리스트 페이지로 돌아가게 됐었고 SQL문도 다시 확인했었다.
왜 오류가 나는지 몰랐었는데 E와 S가 바뀐걸 나중에 발견해 제대로 작동되는걸 확인함 
DB에 값을 넣을 때  sql문에 오타가 없는지 잘 확인해야한다고 배우게 됨.


-플레이리스트 대표 사진을 다시 보여주기 위해서 이미지 BLOB을 사용했는데 이미지가 깨지는 현상이 발생했었다.
db설계 시 이미지 컬럼을 생성해놓지 않아서 다시 추가했으며 String 값으로 받아오는 코드를 배웠다.
Blob Image = resultSet.getBlob("Image");
				byte[] imageData = Image.getBytes(1, (int) Image.length());
				String imageBase64 = Base64.getEncoder().encodeToString(imageData);
				String image = "data:image/jpeg;base64," + imageBase64;

    playlist = new PlayList(playlistId, playlistName,user_id,image);


-사진을 누르면 플레이리스트 DETAIL로 넘어가도록할 때
번호값을 사진에 어떻게 넣을지 고민했는데 playlist ID값을 사진 부분에 바로 넣어 그 문제를 해결했다.






<!-- Stack Icon Refernces -->

[js]: ./readme-static/img/javascript.svg
[java]: ./readme-static/img/java.svg
