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
