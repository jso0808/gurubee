##  그룹웨어 프로그램 - <img src="https://user-images.githubusercontent.com/58289304/209109327-076b6ece-0b74-4162-8b60-c10c81bea1d1.png" width="150" height="30"/>
<br>

### 📌 개발 기간
2022년 10월 14일 ~ 2022년 11월 4일 (약 3주)
<br>
<br>

### 📌 담당 기능: 전자 결재 기능, DB모델링, 메인화면 구현
##### ✔ 전자결재 주요 기능
- 전자결재 문서 발신, 수신함 조회
- 결재 문서 임시보관함 조회
- 결재 문서 유형별 폼 출력
- 결재 라인 지정 기능
- 결재 문서 등록, 수정
- 임시보관 문서 등록, 삭제
- 결재 문서 승인, 반려 기능
- 다중 파일 업로드 기능    
<br>


### 📌 Development Environment
#### ✔ Front-end 
- HTML5, CSS
- Javascript
- jQuery
- AJAX
- Bootstrap 5.2
#### ✔ Back-end
- Oracle DB 18
- Servlet & JSP
- JAVA 1.8
#### ✔ Server
- Apache Tomcat 9.0
#### ✔ 버전 관리
- GitHub    
#### ✔ 기타
- 네이버 스마트 에디터
- Bootstrap
   
<br>
<br>

### 📌 요구사항 명세서
![요구사항 명세서](https://user-images.githubusercontent.com/58289304/200155627-c58a1b1f-fa0e-461b-9743-91ebf77921ab.PNG)   
   
<br>
<br>
   

### 📌 ERD-Cloud
- https://www.erdcloud.com/d/z49JjohxLFBjZ3atD
![ERDCloud](https://user-images.githubusercontent.com/58289304/200156966-c8e74bf4-0522-418a-96ce-8ebaa4c08fd6.png)  

<br>
<br>
    
### 📌 Class-Diagram
![클래스다이어그램](https://user-images.githubusercontent.com/58289304/200156599-afd643e8-5aa5-4159-831e-d16a21ed39e9.png)     
   
   
<br>
<br>

### 📌 UseCase-Diagram
![전자결재 기능 유스케이스](https://user-images.githubusercontent.com/58289304/200157058-b1b8ff4d-e16a-4351-80bb-5723d61281e6.png)
<br>
<br>

### 📌 전자결재 주요 기능
#### ✔ 문서 발신함
- 문서의 현재 결재 상태, 결재자, 처리 결과 출력
- 이전 결재자의 결재결과에 따른 처리
   -  최종 결재자까지 대기 상태라면, 처리 결과는 진행중
   -  모두 승인으로 결재됐다면, 승인
   -  반려 결재결과가 있다면, 반려 상태와 해당 차수 출력
- 수정 이력
   - 1차 결재 대기 상태인 문서만 수정 가능
   - 수정된 문서는 수정 이력 표시 출력 
<br>

![발신함](https://user-images.githubusercontent.com/58289304/209079290-68c49f7d-e7ac-4368-95e0-e8cd9c9e241a.png)
<br>
<br>

#### ✔ 문서 수신함
- 결재자로 등록된 문서가 보이는 문서 수신함 리스트
- AJAX 방식으로 결재 처리
   - 본인 이전의 결재 상태가 대기중이거나 반려된 문서는 결재 불가
<br>

![수신함 (2)](https://user-images.githubusercontent.com/58289304/209079352-24136dff-a435-4f1c-8e39-46d90647f59d.png)
<br>
<br>

#### ✔ 문서 작성하기 (결재 요청하기)
- 작성일자는 js로 현재 년월일 계산하여 자동 입력
- 수신자는 로그인된 세션 정보의 사원 이름으로 자동 입력
- 문서 구분
   - 선택 시 미리 DB에 등록된 양식을 AJAX 방식으로 불러와서, 네이버 스마트 에디터에 출력
   - 문서 구분에 따라 양식폼이 상이 
   - 양식폼을 가이드라인으로 이용하여 간편한 문서 작성 가능 
- 수신자-사원검색
   - AJAX 방식으로 모든 사원 중에서 해당 직급에 해당하는 사원 리스트를 가져와 모달창으로 출력
   - 수신할 사원 클릭 시 사원 데이터가 자동으로 태그에 입력
- 첨부파일 업로드
   - 1개 이상의 다중 파일 업로드 가능
<br>

![문서구분 ajax1](https://user-images.githubusercontent.com/58289304/209079990-5265c27b-516b-487c-8ef2-7d64a239423e.png)
![문서구분 ajax2](https://user-images.githubusercontent.com/58289304/209080014-a8cf93ba-7a92-4221-a664-81fe849e2b64.png)
![사원검색 ajax](https://user-images.githubusercontent.com/58289304/209080038-accd1c6f-d6b9-45e3-b3d7-4c0c5060ae44.png)
![사원검색 ajax2](https://user-images.githubusercontent.com/58289304/209083526-0d41e08b-db48-4030-9643-ad73e02bd4d4.png)
![파일 업로드1](https://user-images.githubusercontent.com/58289304/209080120-d77bc4a2-ed59-4971-9a71-bf416906b5b3.png)
<img src="https://user-images.githubusercontent.com/58289304/209080139-bef76e7a-6b9b-4a51-915a-6f4ab303db2a.png" width="500" height="400"/>
<br>
<br>

#### ✔ 문서 상세보기
- 결재 요청자(발신자)
   - '결재하기' 버튼 비활성화
   - 모든 결재 결과가 대기중이면 '수정버튼' 동작
- 결재자 (수신자) 
   - 이전 결재 결과가 승인인 문서만 결재 가능
   - 결재 불가능한 경우, 불가 사유 메시지 
<br>

![문서보기1](https://user-images.githubusercontent.com/58289304/209079460-1ea4497f-5033-41fe-b696-5a13661ca77a.png)
![문서보기2](https://user-images.githubusercontent.com/58289304/209079504-d366c82f-a216-4a2d-bd68-37f03af53405.png)
<img src="https://user-images.githubusercontent.com/58289304/209079529-0b90c367-7831-4bde-a973-5a65516abf8e.png" width="300" height="200"/>
<img src="https://user-images.githubusercontent.com/58289304/209079555-e46498b5-9ecb-4259-9f54-fcfbd632d32c.png" width="300" height="200"/>
<img src="https://user-images.githubusercontent.com/58289304/209079575-17d30a3b-b95e-4753-8df9-296f696c77af.png" width="300" height="200"/>
<br>
<br>
<br>

#### ✔ 문서 임시보관함
- 임시보관한 문서의 보관함
- 작성 중이던 문서를 마저 작성하여 결재 요청 가능
- 문서 삭제 가능
<br>

![임시보관함](https://user-images.githubusercontent.com/58289304/209079704-37e66490-b54e-4e9f-9115-8fe7aaebada9.PNG)
![임시문서등록1](https://user-images.githubusercontent.com/58289304/209079731-8f389b4e-dbe5-49f9-9055-a820151020a2.PNG)
![임시보관 발신 (2)](https://user-images.githubusercontent.com/58289304/209080291-cd42dd66-4b6e-43c8-8b7f-b6b55865e32f.png)
<br>

