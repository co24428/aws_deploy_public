# deploy
first AWS deploy with Flask


# 1. 회원가입 및 로그인
  - 해외결제 계좌 필요
  - 상단바 우측에 지역을 ***서울***로 바꿔준다.
  
# 2. 인스턴스 생성
  - EC2 > 인스턴스 생성
  - 프리티어 중에서 선택 > ex) Ubuntu Server 18.04 LTS (HVM), SSD Volume Type  
    > 프리티어 사용 가능 선택  
    > 6.보안 그룹 구성 > 규칙 추가 > HTTP, 80, anywhere(위치 무관)  
    > 7. 검토 > 시작하기
  - 키 페어 선택  
    > 기존 키 페어 or 새 키 페어 > *.pem file  
  
# 3. 서버 준비
  - pip3 install fabric3
    - 

  - deploy.json
    - aws IP와 서버 연결
    - 인스턴스 리스트 > IPv4 public IP : IP 확인
  ~~~
    "REPO_URL":"github address", # 모든 파일이 git에 최신화되어 있어야 한다.
    "PROJECT_NAME":"name",
    "REMOTE_HOST":"aws ip adress",
    "REMOTE_HOST_SSH":"aws ip adress",
    "REMOTE_USER":"ubuntu"
  ~~~
  - deploy.json
    - 배포 설정 파일
  ~~~
    24 line : env.key_filename = '../key.pem' # edit
  ~~~
  - requirements.txt
    - 모듈의 버전 파일
  - wsgi.py
    - 서버 역할
    - entry point
  - run.py
    - 서버에 띄워지는 flask code ( 서비스 )

# 4. AWS 연결
  - 1. console (mac bash)
    - 인스턴스 리스트 > 해당 인스턴스 우클릭 > 연결  
      chmod 400 **.pem  
      ssh -i "**.pem" ubuntu@ec2-15-164-211-38.ap-northeast-2.compute.amazonaws.com
    - 서버 우분투에 해당되는 터미널로 접속된다.
    
  - 2. AWS & 서버 연결
    - 사전작업 : 3 과정의 것이 git에 올라가있고 최신화되있어야 한다.
    - 해당 경로로 연결된 bash에서
    ~~~
      fab new_server
    ~~~
    - git이 private이면 로그인 진행, aws 서버에 git에 있는 파일들을 업로드 및 연결
    - 이 폴더들은 위처럼 연결한 console에서 확인 가능하다(linux)
    
# 위에서 설정해준 aws ip address로 접속이 가능해진다!
    
    
    
    
    
    
    
    
    
    
