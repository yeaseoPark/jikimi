# CCTV를 통한 학교폭력 모니터링 시스템 <br/> (멀티캠퍼스 융복합 프로젝트)
## 1. 프로젝트 동인 및 내용 요약
- 2022년 1차 학교 폭력 실태조사를 기준으로, 학교폭력대책심의위 심의 유형별 현황 자료를 분석한 결과, 코로나 사태로 줄어들었던 학교 폭력이 전면 등교 이후 확연한 증가세를 보이고 있다.
- 22학년도 학교 폭력 유형별 통계를 나타낸 자료.
    - 물리적 폭력이 가장 큰 비중을 차지.
    - 금품갈취, 강요, 성폭력 등과 같은 유형들은 신체 폭력과 동반되기 쉽다는 것을 감안하면 실제로는 좀 더 높은 비율을 차지할 것으로 예상.
- **CCTV를 통해 영상을 찍고, 이에 대한 폭력 상황을 감지하여 교사에게 알림을 보낼 수 있는 시스템**, 슬기로운 지키미를 개발.

## 2. 프로젝트 진행 내역
### 2.1 진행 기간
- 진행 기간 : 2023.01.03 ~ 2023.02.16
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/f4b674a2-dbce-4ced-9fa9-081e5cf559a1)
### 2.2 개발 참여 인력
- IoT : 김준무
- 클라우드 : 류승지, 박예서(팀장, 본인), 이기복
- 빅데이터 : 박수은, 서혁준, 유영일
### 2.3 사용 기술 스택
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/ee2d96cc-251e-4ffe-be27-1a6643d1eceb)
- 언어 : Python
- 사용 프레임워크 : Django Framework
- 사용 데이터베이스 : Maria DB(Amazon RDS - Freetier)
- 서버 및 아키텍처 구성
    - 웹 프로젝트 : Linux(Centos) - AWS EC2 프리티어 이용, uwsgi - Nginx 의 3-Tier 기반, WAF 설정
    - CCTV 모니터링 : Linux(Centos) - AWS EC2 머신러닝용 이미지 사용, AWS SNS, AWS Lamda, AWS S3
- 사용 라이브러리 : OpenCV, YOLOv5, boto3(→ SSM 접속용)
- 프로젝트 관리 : 구글 드라이브, Gantter for google drive

## 3. 프로젝트 아키텍처
### 3.1 AWS 아키텍처 구성
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/dba873ee-cc09-43dd-856e-5d716dd96632)
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/70f3ad66-5b5d-452f-a834-5657f094ac86)

### 3.2 IP 및 서브넷 구성
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/10cabce2-e5ab-4a3a-b7a4-0d1362a70642)
- VPC  : IP 주소 192.168.0.0/16 (C 클래스 : 개발 초기라 이용자 수가 적기 때문에)
- 서브넷을 4개로 나누었음
    - AZ 가 2개
    - 사용자는 퍼블릭만 사용, 개발에는 Private를 사용
    - 서버 사용 용도 : YOLO 실행 서버, 인터페이스 실행 서버

### 3.3 ERD
![image](https://github.com/yeaseoPark/jikimi/assets/105956187/2e48262b-4103-41ce-b58a-6f578778ef73)

## 4. 최종 프로젝트 시연
https://youtu.be/9NF_7Q8szt8
