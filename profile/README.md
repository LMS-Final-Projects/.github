# LMS-FINAL-PROJECT
<br/>

![image](https://github.com/LMS-Final-Projects/.github/assets/67565707/19b03332-c371-4418-a9e0-830ed437de42)

## 📌 프로젝트 목적 
학사정보관리 시스템을 MSA 방식으로 구현하여 서비스 간 의존도를 낮추고, 유연한 서비스를 구축하는 것이 목표입니다.

<br/>

## 📁 API 명세서
- [API](https://teal-beef-c93.notion.site/f5e921a5de284902a56837b01f087cdf?v=2680c1384e634e61bc39ceff0c191cb8&pvs=4)

<br/>

## 📸 시연 영상 
- [LMS-FINAL-PROJECT](https://www.youtube.com/watch?v=Y5-bsJD7zK4)

<br/>
  
## 👥 팀원 소개 
| 이름       | 포지션       | 담당한 핵심 기능          |
| ---------- | ------------ | ----------------------------------------|
| 안재원 | `FE` / `BE` | `Gateway 및 프론트 서버 등 전체적인 서버 환경 구축` `수강신청 서비스` `성적 서비스` | 
| 채오성 | `FE` / `BE` | `스케줄 등록` `파일 관리 서비스` `쪽지 서비스` | 

<br/>

## 🗣️ 프로젝트 진행 
매주 정해진 날짜에 회의를 진행하여 의견을 공유했고, 작업 내용은 JIRA를 통해 공유했습니다.

<br/>

![image](https://github.com/LMS-Final-Projects/.github/assets/134196095/d8389cb3-3e20-4293-9edd-4db3a22d7bf4)

![image](https://github.com/LMS-Final-Projects/.github/assets/67565707/b0e0909c-e4a9-4a6f-a7d9-13316f69d080)

<br/>

> ![지라(메인페이지)](https://github.com/LMS-Final-Projects/.github/assets/134196095/534a5b1b-69f8-4e9c-b519-2f9afd358bf6)
![지라(기획)](https://github.com/LMS-Final-Projects/.github/assets/134196095/1ba75e36-ccdf-4fc6-8973-ca2fc5bb333d)
![지라(기획-세부)](https://github.com/LMS-Final-Projects/.github/assets/134196095/e8fb6e26-c3d4-48b3-b1bd-0a9c80237428)
![지라(프로젝트)](https://github.com/LMS-Final-Projects/.github/assets/134196095/b78b8bb4-c140-442e-ab5c-65b2009c6135)
![지라(프로젝트-세부)](https://github.com/LMS-Final-Projects/.github/assets/134196095/ae7dbf26-c8aa-4bb1-acc0-5c0f0538837d)

<br/>

## 📁 서비스 아키텍처 
![제목 없는 다이어그램](https://github.com/LMS-Final-Projects/.github/assets/67565707/10fedad3-aaf6-4ba3-993d-939abd4cf3da)

<br/>

## 📢 트러블 슈팅
> ### kafk 통신
> 
 * 문제상황
   * 1. Kafka와 OpenFeign을 동시에 사용하려 하였으나, 해당 API를 호출하는 과정에서 충돌이 발생함.
      OpenFeign에서는 Http통신이 동기적으로 이루어지는데 반해, Kafka의 이벤트처리는 비동기적으로 이루어지 때문에 해당 문제가 발생함.
   * 2. Kafka의 비정상적인 종료시 데이터 유실이 발생함. 
   * 3. Kafka는 데이터를 바이트 배열로 저장하기 때문에, 특정한 Class를 직접 저장할 경우, 불러올때 문제가 발생함.

<br/>

 * 해결방안
   * 1. OpenFeign 통신을 제거하고 분산시스템간의 데이터전달을 Kafka로 처리하였음.
   * 2. 해당 에러가 발생한 모든 이벤트를 기록하여 추적함.
   * 3. 그래서 해당 특정 Class를 Json타입의 데이터형식으로 저장함. Jackson라이브러리를 사용하여 ObjectMapper를 통해, json 객체를 생성하고 이를 json타입의 문자열로 전송하였음.

<br/>

> ### 동시성 문제
> 
 * 문제상황
   * 수강신청 과정에서 최대 수강 가능 인원을 체크하는 로직이 있었으나, 테스트시 다수의 쓰레드가 동시에 수행될 때 최대인원을 초과하는 신청이 발생함

<br/>

 * 해결방안
   * 각 수강신청 과정에서 Redis의 특정 메소드를 사용하여 최대 수강 가능 인원을 업데이트하고 이를 확인함으로써, 다중 쓰레드 간의 충돌을 방지하였음

<br/>

## 🖋️ 사용 기술 
#### Environment & tools
<img src="https://img.shields.io/badge/IntelliJ-000000?style=flat&logo=intellijidea&logoColor=white"> <img src="https://img.shields.io/badge/Github-181717?style=flat&logo=github&logoColor=white"> <img src="https://img.shields.io/badge/Slack-4A154B?style=flat&logo=slack&logoColor=white"> <img src="https://img.shields.io/badge/Notion-000000?style=flat&logo=notion&logoColor=white"> 

#### Development - FrontEnd
<img src="https://img.shields.io/badge/Javascript-F7DF1E?style=flat&logo=javascript&logoColor=white"> <img src="https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=white"> <img src="https://img.shields.io/badge/Axios-5A29E4?style=flat&logo=axios&logoColor=white"> <img src="https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white"> <img src="https://img.shields.io/badge/Redux-764ABC?style=flat&logo=redux&logoColor=white">

#### Development - BackEnd
<img src="https://img.shields.io/badge/Springboot-6DB33F?style=flat&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/SpringbootJpa-6DB33F?style=flat&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/Jsonwebtokens-000000?style=flat&logo=jsonwebtokens&logoColor=white"> <img src="https://img.shields.io/badge/Gradle-02303A?style=flat&logo=gradle&logoColor=white"> 
<img src="https://img.shields.io/badge/KAFKA-231F20?style=flat&logo=KAFKA&logoColor=white">


#### Distribution - CI / CD
<img src="https://img.shields.io/badge/Googlecloud-4285F4?style=flat&logo=googlecloud&logoColor=white"> <img src="https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=white"> <img src="https://img.shields.io/badge/jenkins-D24939?style=flat&logo=jenkins&logoColor=white">  

<br/>

