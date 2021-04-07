## MSA
- [모놀리식 아키텍처](#모놀리식-아키텍처)
- [마이크로서비스 아키텍처](#마이크로서비스-아키텍처)
- [이벤트 드리븐 아키텍처](#이벤트-드리븐-아키텍처)
- [도커](#도커)
- [쿠버네티스](#쿠버네티스)

[ [← back](https://github.com/cholnh/study-cs#-MSA-) ]

## 모놀리식 아키텍처

[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 마이크로서비스 아키텍처

마이크로서비스는 독립적으로 확장될 수 있는 작은 규모로 분할 된 서비스이다.  
Service Discovery, API Gateway, Orchestration, Choreography, Context Boundary 등의 서비스들의 조합으로 이루어진다.  

- 관리 컨테이너
    + 개별 서비스 인스턴스를 구동/관리 할 컨텍스트.
    + VM, Docker 등
- 외부 게이트웨이
    + 외부에 api 형태로 기능 노출
    + 외부 엑세스 관리, 트래픽 관리, 보안 정책 등 내부 마이크로서비스 환경 보호
- 서비스 메쉬 기능
    + 서비스 간 통신을 느슨하게 결합 (유연성)
    + 서비스 분리, 버전관리 전략 지원, Auto Scaling 관리 등 가능
        + 서비스 라우팅
        + 로드 밸런싱
        + 서비스 디스커버리 : 서비스 레지스트리를 사용하여 구현. (마이크로 서비스간에 호출, 종속성관리)
        + Config 저장소
        + ID 공급자 : 서비스 인스턴스는 (신뢰할 수 있는)ID를 사용하여 통신.
- 서비스 이미지 레지스트리
    + 빌드되고 테스트 된 서비스의 불변 이미지를 저장하는 레지스트리
    + 코드 저장소 or Docker 이미지 레지스트리 or VM 이미지 BLOB 등등..
- 메시지 지향 미들웨어
    + (게시/가입/화재/잊어버리기 등 과 같은)이벤트 및 메시지 중심 패턴을 지원하기 위해 비동기 메시징 채널이 필요.
- 빌드/테스트 자동화
- 배포 자동화
    + 배포 뿐만 아니라 외부 아키텍처 자체의 변경 자동화 지원이 필요.
        + 서비스 라우팅 설정
        + 로드 균형 조정
        + 서비스 검색 및 서비스 구성 데이터 업데이트 등
- 플랫폼 자동화
    + 컨테이너의 프로비저닝
    + 각 마이크로 서비스의 실행중인 인스턴스 관리 등
- 모니터링/경고
- 로깅/진단
- ID 제공
    + 토큰 기반 인증/인가 서비스 사용하여 신뢰성 보장

<br/>

**마이크로 서비스 패턴**  

- 라우팅 패턴
    + 서비스 디스커버리 패턴
        + 스프링 클라우드 + 넷플릭스 유레카
        + 쿠버네티스
    + 서비스 라우팅 패턴
        + 스프링 클라우드 + 넷플릭스 주울
        + 쿠버네티스
          
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-routing-pattern.jpg" width="700"/>|
|-|
|그림 1- 라우팅 패턴|

<br/>

- 회복성 패턴
    + 클라이언트 부하 분산
        + 스프링 클라우드 + 넷플릭스 리본
        + 쿠버네티스
    + 회로차단기 패턴
        + 스프링 클라우드 + 넷플릭스 히스트릭스
    + 폴백 패턴
        + 스프링 클라우드 + 넷플릭스 히스트릭스
    + 벌크 헤드 패턴
        + 스프링 클라우드 + 넷플릭스 히스트릭스

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-mediation-pattern.jpg" width="700"/>|
|-|
|그림 2 - 회복성 패턴|

<br/>

- 보안 패턴
    + 스프링 클라우드 시큐리티
    + OAuth2, JWT

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-security-pattern.jpg" width="700"/>|
|-|
|그림 3 - 보안 패턴|

<br/>

- 로그 패턴
    + 스프링 클라우드
    + 슬루스
    + 페이퍼 트레일
    + 집킨

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-log-pattern.jpg" width="700"/>|
|-|
|그림 4 - 로그 패턴|

<br/>

- 빌드/배포 패턴
    + 지속적 통합(CI)
        + Travis CI
        + 쿠버네티스
    + 코드형 인프라스트럭처 (IaC)
        + 도커
    + 불변서버
        + 도커
    + 피닉스서버
        + Travis CI
        + 도커

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-deploy-pattern.jpg" width="700"/>|
|-|
|그림 5 - 빌드/배포 패턴|

<br/>

- 개발 패턴
    + 핵심 마이크로서비스 패턴
        + 스프링 부트
    + 구성 관리
        + 스프링 클라우드 컨피그
    + 비동기 메시징
        + 스프링 클라우드 스트림

<br/>

    
[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 이벤트 드리븐 아키텍처

[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 도커

[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 쿠버네티스

구글은 이미 사내에서 프로젝트를 컨테이너화 하여 서비스를 관리해왔다.  
(마이크로 서비스 아키텍쳐 발전에 힘입어) 이런 경험, 노하우를 바탕으로  
컨테이너 운영환경 플랫폼을 오픈소스화 하여 만든게 쿠버네티스이다.  

<br/>

**컨테이너 운영환경**  
단순하게 컨테이너를 VM 이나 온프렘(On-Premise)에 배포하면 되지 왜 컨테이너 운영환경이 필요한가?  
- VM 이나 온프램의 하드웨어 수가 많아 졌을 때 관리를 어떻게 할 것인가
- 자원은 한정되어 있고, 한정된 자원을 최적으로 사용하기 위해서는 적절한 위치에 배포해야 한다.(스케줄링)
- 내부에 컨테이너가 정상적으로 동작하는지 모니터링하고 셀프 힐링이 가능해야 한다.

**컨테이너 운영환경** 은 이 모든것을 종합적으로 관리 해주는 환경이다.  
- 컨테이너 스케줄링
- 컨테이너 모니터링
- 컨테이너 생명주기 관리 등

이런 컨테이너 운영환경을 지원하는 솔루선 중 가장 주목받고 있는 것이 쿠버네티스(Kubernetes, 약어로 k8s) 이다.

<br/>

> cf) 컨테이너 환경을 VM 위에 올릴 수도 있다.  
> 데이터 센터에서는 흔히 온프렘 환경을 사용한다.  
> 온프렘 환경에서 쿠버네티스를 올릴 때 베어메탈(가상화를 위한 하이퍼바이저 OS 없는 물리 서버)에 올리지 않고, VM(가상화 환경)을 올린 후에, 그 위에 쿠버네티스를 배포하는 구조를 갖는다.  
> Why? 하드웨어 자원의 효율성때문. 컨테이너 환경은 하드웨어 자원을 컨테이너화 하여 격리(isolation) 하는 기능이 주다.  
> 그에 반해 가상화 환경은 isolation 기능도 가지고 있지만 가상화를 통해 자원, 특히 CPU 수를 늘릴 수 있다.  
> 예를 들면 8 CPU 머신을 쿠버네티스로 운영하면 8 CPU 밖에 사용할 수 없지만,  
> 가상화 환경에서는 8 CPU 를 가상화하여 2배일 경우 16 CPU 로, 8배일 경우 64 CPU 로 자원을 잘게 나눠서 사용이 가능하다.  
> 이외에도 스토리지 자원의 활용 용이성, 노드 확장 등을 유연하게 할 수 있는 장점이 있다고 한다.  
> (by - https://bcho.tistory.com/1255)

<br/>

**쿠버네티스 구조**  
쿠버네티스는 상당히 심플한 구조를 갖는다.  
- 마스터노드
    + 클러스터 전체 관리
- 워커노드
    + 컨테이너가 배포되는 머신

> cf) GKE 는 (운영환경에서 변화의 영역이 적은)마스터 노도에 대한 완전관리 서비스를 제공.  
> kNative 같은 경우 서버운영에 관한 관심이 전혀 없도록(?) 서버리스에 대한 편의성을 지원한다.

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-architecture-1.jpg" width="700"/>|
|-|
|그림 1 - 쿠버네티스 구조|

<br/>

**쿠버네티스 오브젝트**
쿠버를 이해하기 위해, 쿠버를 구성하는 가장 기본적인 단위가되는 기본 오브젝트(Basic Object) 와 오브젝트를 생성/관리 하는 컨트롤러에 대한 이해는 필수이다.  
추가로 오브젝트의 스펙(설정), 메타정보(추가정보)로 구성된다.

- Basic Object
    + 쿠버에 의해 관리/배포 되는 가장 기본적인 오브젝트.
    + (컨테이너화 되어 배포되는)어플리케이션의 워크로드를 기술하는 오브젝트이다.
        + Pod
        + Service
        + Volume
        + Namespace
- Object Spec
    + 오브젝트를 정의하는 설정 정보.
    + yaml, json 으로 정의하거나 커멘드라인을 통해 오브젝트 생성시 인자로 전달.

<br/>
    
**Pod**
쿠버에서 가장 기본적인 배포 단위. (하나 이상의 컨테이너)

```yaml
apiVersion: v1            # 스크립트 실행하기 위한 쿠버 API 버전 (보통 v1사용)
kind: Pod                 # 대상 리소스 종류 정의 (여기서는 Pod 를 정의한다)
metadata:                 # 메타데이타 (라벨 이나 리소스 이름 등)
  name: nginx
spec:                     # 리소스 상세 스팩 정의
  containers:             # Pod 는 Container 를 가지고 있으니 정의해준다.
  - name: nginx           # 컨테이너 이름은 'nginx' 라 한다.
    image: nginx:1.7.9    # Docker 이미지 nginx:1.7.9 를 사용한다.
    ports:
    - containerPort: 8090 # 컨테이너 포트 8090 을 오픈한다.
```
   
**Why 여러 컨테이너를 묶어 하나의 Pod 로 배포할까 ?**  
Pod 는 다음과 같은 특성이 있다.  
- Pod 내 컨테이너는 IP 와 PORT 를 공유한다.  
    두 컨테이너가 하나의 Pod 를 통해 배포되었을 때, localhost 를 통해서 통신이 가능하다.
    
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-pod-1.jpg" width="700"/>|
|-|
|그림 2 - Pod 내부 통신|

- Pod 내 배포된 컨테이너 간에는 디스크 볼륨을 공유할 수 있다.  
    애플리케이션 들은 배포될 때 Reverse Proxy, 로그수집기 등 주변 다양한 솔루션과 같이 배포되는 경우가 많음.
    
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-pod-2.jpg" width="700"/>|
|-|
|그림 3 - Pod 내 사이드카 패턴|

<br/>

**Volume**  
- Pod 의 경우 기동할 때 Container 마다 로컨 디스크를 생성한다.  
    (영구적 디스크 x, 컨테이너 리스타트 시 초기화)  
    DB 같이 영구적 저장을 위해서 스토리지 볼륨에 저장한다.
- Pod 가 기동할 때 Container 에 마운트 해서 사용한다.

아래와 같은 시나리오에서 볼륨이 사용된다.  
- web server 컨테이너는 `/htdocs` 디렉터리의 컨테이너를 서비스 하고, `/logs` 디렉토리에 웹 로그를 기록한다.
- content manager 컨테이너는 `/htdocs` 디렉터리에 컨텐츠를 업데이트 및 관리한다.
- logger 컨테이너는 `/logs` 디렉터리 내 로그를 수집한다. 

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-volume-1.jpg" width="700"/>|
|-|
|그림 4 - Volume|

- `htdocs` 볼륩은 web server 컨테이너와 content manager 컨테이너에 마운트 됨.
- `logs` 볼륨은 logger 컨테이너와 web server 컨테이너에 마운트 됨.

<br/>



    
[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]