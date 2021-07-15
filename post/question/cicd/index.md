## DevOps
- [CI/CD](#cicd)
- [빌드/배포 파이프라인 설계](#빌드배포-파이프라인-설계)

[ [← back](https://github.com/cholnh/study-cs#-devops-) ]

## CI/CD

마이크로 서비스를 (자동으로) 빌드하고 테스트한 뒤 배포할 수 있게 도와주는 개발 지원 환경을 데브옵스(DevOps)환경이라 합니다.  
(보통 개발+운영 을 병행하는 조직 또는 문화를 뜻하는데, 여기서는 자동화 환경의 의미로 사용하겠습니다)

<br/>

과거 수동 빌드/배포 과정은 매우 많은 시간이 소요되었습니다.  
또한 배포 때마다 시스템을 중단한 뒤 배포 작업을 진행하는 경우가 많았습니다.  
하지만 MSA 환경에서는 잦은 배포가 이루어져야 하므로 배포의 자동화와 무중단 배포가 절실합니다.

<br/>

자동화된 빌드/배포 작업을 CI/CD 라 합니다.  
- CI (Continuous Integration; 지속적 통합)  
    오랜 시간이 걸리는 빌드를 자동화하여 개발 생산성과 소스코드 품질을 높입니다.  
    자동으로 통합 및 테스트하고 그 결과를 리포트로 기록합니다.
    
    |<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/cicd/msa-pattern-cicd.png" width="700"/>|
    |-|
    |자동 빌드 및 배포 절차|
    
<br/>
    
- CD (Continuous Deployment; 지속적 배포)  
    소스코드 저장소에서 빌드한 소스코드의 실행 파일을 실행 환경까지 자동으로 배포하는 방식을 뜻합니다.  
    다른 의미의 CD (지속적 제공; Continuous Delivery) 와의 차이는 엄격한 배포 절차에 있습니다.

    |<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/cicd/msa-pattern-cd-diff.png" width="700"/>|
    |-|
    |Continuous Deployment 와 Continuous Delivery 차이|

<br/>

## 빌드/배포 파이프라인 설계
빌드/배포 과정 동안 수행해야 할 테스크가 정의된 것을 빌드/배포 파이프라인이라고 합니다.  

<br/>

전형적인 파이프라인 흐름도는 다음과 같습니다.  

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/cicd/msa-pattern-cicd-pipeline.png" width="700"/>|
|-|
|배포 파이프라인 절차|

배포 절차 전에 UI 테스트, 통합테스트, 배포 승인 프로세스 등을 추가하여 재설계할 수도 있습니다.  
위와 같은 일련의 프로세스를 하나로 연계해서 자동화하고 시각화한 절차로 구축합니다.

<br/>

[ [← back](https://github.com/cholnh/study-cs#-devops-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/cicd/index.md#devops) ]