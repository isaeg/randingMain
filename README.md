# randingMain
홈페이지 + 영업팀 매출 단순 조회  

# 개발 환경
* JAVA 17
* Springboot 3.1.5 / thymeleaf
* Mybatis
* Mysql
    * host : db.isaegad.gabia.io : 3306
    * database: dbisaegad
    * user : isaegad
    * pwd : dltorrhkdrh2023 (이색광고2023)

# 호스팅 정보 (가비아 자바 클라우딩 호스팅)
* host : 211.47.75.61:22
* User : isaegad
* pwd : dltorrhkdrh2023 (이색광고2023)
*  https://www.gabia.com/
    * isaegad@gmail.com 계정으로 로그인 => MyGabia => 이용중인 서비스 확인
* github 계정 ID : isaegad@gmail.com   PWD :!dltorrhkdrh2023(!이색광고2023)
# 프로세스 
1. 첫 화면 -> 로그인(Spring Security 적용)  ID : sadmin  PWD : asdf1234!
2. 팀원별 매출 현황 / 팀별 매출 현황 중 팀원 별 매출 현황이 첫 페이지  
2-1. 디폴트값은 년 / 월 / 일 선택 안한 화면으로 조회
2-2. date 값이 없으면 테이블 등록일 전체 조회 기준 개인별 매출 SUM 값 / 큰 순서대로 조회
      ==> TO_BE : 조회 조건 추가 해야 할 필요 있음 (ex : 날짜 간격 조회 ,날짜 정렬 등 )
2-3. 날짜 선택 후 조회 시 그 날에 해당하는 값 만 조회
     값이 없으면 등록 버튼 노출 / 있으면 수정 버튼 노출
2-4. 등록 버튼 클릭 시 숨김버튼 처리 : 조회 버튼 다시 누르면 수정으로 변경
2-5. 등록 시 날짜 값은 조회한 날짜로 등록 해야 함. 추 후 날짜 간격 조회 추가 될 시 변경 필요함
2-6. 현재 조회 시 mybatis 에 조건문이 날짜가 있냐 없냐로 분기처리가 되어있는데, 이 역시 간격 조회 추가 시 쿼리 변경 필요
3. 팀별 매출 현황은 개인이 속해있는 팀에 누적 값 조회
3-1. 팀별 매출 현황은 단순 조회처리만 되어있음

# 참고 사항 
1. 유저 테이블 : tb_member  
2. 매출 테이블 : tb_saleshistory
3. 급하게 만들어서 매출 조회 ( salesTable.html / TeamSalesTable.html) 에 해당하는
   컨트롤러 AdminController 에 몰려있음..
4. 본래 문의하기  CRUD 용으로 만든 부분이라 나중에 필요 시 리턴 화면만 조정해서 사용하면 됨
5. 자바스크립트로 10분에 한번 자동 새로고침 되어있음 

# 기타 사항
1. 피드번호 확인 netstat -ntlp | grep :8080
2. 세션 유지 실행  nohup java -jar 파일명.jar &
3. root 권한 없음 -> 파일 업로드 / 패키지 실행 정도만 가능 
4. Port 는 8080 만 허용
5. 현재 Google Smtp로 메일 전송(개인 이메일) => 추 후 회사계정 전환  
   application.properties 
``` properties
spring.mail.username=회사 계정
spring.mail.password= 내계정 - 앱 2차 비번 
```


