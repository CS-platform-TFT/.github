브랜치 구조
  1.전체 브랜치 소개 및 전략
  
  1.1. 브랜치별 역할
    		      개발 라인                                                 
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ <br>
                MAIN    DEV                                                  
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
    
    MAIN            AI STUDIO 운영 환경에 배포되는 안정적인 제품 코드 유지
  	DEV             개발이 진행되는 브랜치. 소스 코드의 개발, 통합, 테스트, 유지보수 진행
 
  1.2. 브랜치 전략
  
  <img width="680" height="362" alt="git flow 전략" src="https://github.com/user-attachments/assets/fc4ba64a-49d4-45d8-91f9-384bd8acf24b" />
  
    [개발 FLOW]
    개발은 DEV에서 개인별/기능별 feature 브랜치를 따고 해당 브랜치에서 진행
    병합시 충돌 최소화를 위해 개인 feature 브랜치의 주기적인 소스 최신화 필요
    
    [배포 FLOW] - RELEASE 브랜치에서 배포 진행
    배포 일정에 맞추어 feature 소스들을 DEV에 병합
    소스 병합 완료 시점에 DEV에서 배포용 RELEASE 브랜치를 따서 테스트와 버그 수정 진행
    테스트 완료된 안정된 소스에 release Tag를 달고, 빌드 및 배포 진행
    빌드 완료 소스를 MAIN과 DEV에 병합 후, MAIN에는 해당 빌드 버전 Tag 추가




------------------------------------------------------------------------------------------------------------------------
개발 흐름에 따른 기본적인 git 사용 가이드 입니다.

[ 개발 소스 클론 ] <br><br>

[  개발 흐름  ]  <br><br>
  개발은 아래의 흐름으로 진행합니다.<br>
  
  작업해야하는 브랜치(A)를 최신화
  최신화시킨 브랜치(A)에서 개인 브랜치(A-1) 생성
  개인 브랜치(A-1)에서 개발 작업
  변경 소스 stash
  상위 브랜치(A)의 변경된 소스를 개인 브랜치(A-1)에 최신화
  변경 소스 stash 해제
  충돌 발생시 충돌 해결
  변경한 소스 add
  commit
  push 또는 merge
  개발 완료한 브랜치 삭제 <br><br>

[명령어는 위의 흐름대로 아래에서 설명하겠습니다.] <br>

  1. 작업해야할 브랜치 최신화 & 개인 브랜치 생성
  현재 브랜치 최신화
  git pull origin <현재 브랜치 이름> <br>
  
  개인 브랜치 생성 후 바로 이동:(반드시 상위 브랜치 확인 후 원하는 브랜치가 아닐시, 이동해서 브랜치를 생성해주세요)
  git switch -c <생성할 브랜치 이름> <br><br>


  2. 변경 소스 stash & pull     (작업 중인 브랜치를 최신화 하거나 완료되어 push할 경우)
  stash 진행
  git stash <br>
  
  상위 브랜치의 소스 최신화
  git pull origin <상위 브랜치 이름> <br>
  
  stash 해제
  git stash pop <br><br>


  3. 상위와 내 브랜치가 공통으로 작업한 파일이 있는 경우, stash pop 시에 충돌 발생 -> 해결 해줘야함.
  충돌이 발생할 경우, 해결하면 상위의 변화와 자신의 브랜치의 변화가 병합된 상태가 완성. <br>
  
  git에 올리는 방법은 2가지가 있습니다.
  - push 후 github에서 pull request를 생성해서 병합 
  - 상위 브랜치로 이동해서 내 브랜치 소스 merge <br>
  
  <push 후 github에서 pull request를 생성해서 병합> 
  해당 최신 코드를 상위 브랜치에 add > commit > push <br>
   
  add
  git add <변경한 파일 명 또는 디렉토리 경로>  <br>
  
  commit
  git commit -m '커밋 메시지' <br>
  
  push
  git push origin <현재 내 브랜치명> <br><br>
  
  
  4. push하면 github의 자신의 브랜치가 생성되고 상위에 compare & pull request 알림이 뜹니다. <br>
  
  
  5. compare & pull request 버튼을 누르면 아래와 같이 나오는데 compare이 내가 작업했던 브랜치 명이 맞는지 확인하고, base에는 소스가 올라갈 브랜치가 맞는지 확인해주고, create pull request 버튼을 눌러줍니다. <br>
  
  
  6. 이후 나오는 화면에서도 pull resqest 생성해주면 완료됩니다. <br>

  <상위 브랜치로 이동해서 내 브랜치 소스 merge>
  작업하던 브랜치에서 add > commit > 상위 브랜치로 이동 > merge <br>
  
  add
  git add <변경한 파일 명 또는 디렉토리 경로>  <br>
  
  commit
  git commit -m '커밋 메시지' <br>
  
  상위 브랜치로 이동
  git switch <상위 브랜치 이름> <br>
  
  merge
  git merge <개인 브랜치 이름> <br>
  
  머지한 상위 브랜치도 결국엔 로컬이기 때문에, 원격으로 push
  git push origin <상위 브랜치 이름> <br><br>
   

  7. 작업하던 개인 브랜치를 삭제
  git branch -d <삭제할 브랜치 이름>

