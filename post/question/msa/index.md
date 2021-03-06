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

**마이크로 서비스 패턴 종류**  
마이크로 서비스를 구성하는 여러가지 패턴이 있다.  
아래 패턴을 편하게 구현하도록 도와주는 여러 오픈소스들을 같이 적어놨다.  
넷플릭스 OSS 는 MSA 관련 패턴들을 정형화하여 오픈소스화 한 프로젝트이다.  
하지만 넷플릭스 OSS 또한 각 패턴별 러닝커브가 존재하고 알아야 할 종류들이 많다.  
보통 대규모 시스템을 운영하는 기업들은 쿠버네티스를 사용하여 여러 패턴에 쓰이는 기술들을 안정적이고 효율적으로 운영한다.  

- 라우팅 패턴
    1. 서비스 디스커버리 패턴
        + 스프링 클라우드 + 넷플릭스 유레카
        + 쿠버네티스
    2. 서비스 라우팅 패턴
        + 스프링 클라우드 + 넷플릭스 주울
        + 쿠버네티스
          
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-routing-pattern.jpg" width="700"/>|
|-|
|그림 1 - 라우팅 패턴|

<br/>

- 회복성 패턴
    1. 클라이언트 부하 분산
        + 스프링 클라우드 + 넷플릭스 리본
        + 쿠버네티스
    2. 회로차단기 패턴
        + 스프링 클라우드 + 넷플릭스 히스트릭스
    3. 폴백 패턴
        + 스프링 클라우드 + 넷플릭스 히스트릭스
    4. 벌크 헤드 패턴
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
    1. 지속적 통합(CI)
        + Travis CI
        + 쿠버네티스
    2. 코드형 인프라스트럭처 (IaC)
        + 도커
    3. 불변서버
        + 도커
    4. 피닉스서버
        + Travis CI
        + 도커

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-deploy-pattern.jpg" width="700"/>|
|-|
|그림 5 - 빌드/배포 패턴|

<br/>

- 개발 패턴
    1. 핵심 마이크로서비스 패턴
        + 스프링 부트
    2. 구성 관리
        + 스프링 클라우드 컨피그
    3. 비동기 메시징
        + 스프링 클라우드 스트림

<br/>

    
[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 이벤트 드리븐 아키텍처

[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 도커

도커는 Linux 기반의 Container RunTime 오픈소스이다.  


[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]

<br/>

## 쿠버네티스

구글은 이미 사내에서 프로젝트를 컨테이너화 하여 서비스를 관리해왔다.  
(마이크로 서비스 아키텍쳐 발전에 힘입어) 이런 경험, 노하우를 바탕으로  
컨테이너 운영환경 플랫폼을 오픈소스화 하여 만든게 쿠버네티스이다.  

<br/>

**컨테이너 운영환경**  
단순하게 컨테이너를 VM 이나 온프렘(On-Premise)에 배포하면 되지 왜 컨테이너 운영환경이 필요한가?  
아래 문제점들을 하나하나 생각해보자.  

- VM 이나 온프램의 하드웨어(또는 컨테이너) 수가 많아 졌을 때 관리를 어떻게 할 것인가.
- 자원은 한정되어 있고, 한정된 자원을 최적으로 사용하기 위해서는 적절한 위치에 배포해야 한다. (스케줄링 필요성)
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

**Service**  
여러 Pod 를 하나의 IP 와 PORT 로 묶어서 서비스를 제공한다. (+ 부하분산)  

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-service-1.jpg" width="700"/>|
|-|
|그림 5 - Service|

<br/>

```yaml
kind: service
apiVersion: v1
metadata:
    name: my-service
spec:
    selector:
      app: myapp        # 라벨 셀렉터에서 라벨 이름이 myapp 인 pod 를 선택
    ports:
      -protocol: TCP
      port: 80          # 서비스는 80 포트 사용
      targetPort: 9376  # 80 포트에 들어온 요청을 컨테이너 9376 포트에 연결
```

<br/>

**Why 로드벨런서가 아니고 Service 인가**
- Pod 의 경우 동적으로 생성된다. (Auto Scaling)  
    -> 로드벨런서에 등록/삭제 빈번함
- 장애가 생기면 자동으로 리스타팅 되면서 IP 가 변경됨  
    -> 로드벨런서에 IP 등록이 어려움
- Service 는 label selector 를 사용하여 위 문제를 해결한다.

<br/>

**라벨/라벨 셀렉터**  
- 라벨
    + 리소스를 선택하는 기준 (키/값 쌍)
    + 각 리소스는 라벨을 갖는다.
    + ex) 
        + 특정 리소스만 배포 가능, 업데이트 가능
        + Service 에 Pod 연결
        + 특정 리소스만 네트워크 접근 권한 부여 등
- 라벨 셀렉터
    + 라벨링된 리소스를 선택한다.
        + Equality Based Selector  
            (=, != 조건으로 리소스 선택)
        + Set Based Selector  
            (집합개념 in, notin 조건으로 리소스 선택)

<br/>

**Namespace**  
한 쿠버네티스 클러스터 내의 논리적인 분리 단위이다.  
Pod, Service 등은 네임스페이스 별로 생성/관리 된다. (사용자 권한 부여도 가능)  

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-namespace-1.jpg" width="700"/>|
|-|
|그림 6 - Namespace|

<br/>

- 사용자 별 접근 권한을 다르게 할 수 있다.
- 네임스페이스 별로 리소스의 쿼타(할당량) 지정 가능
- 네임스페이스 별로 리소스를 나눠서 관리할 수 있다. (Pod, Service 등)
- (논리적 분리 이기에) 다른 네임스페이스 간 Pod 라도 통신이 가능하다.  
    + 물론 네트워크 정책으로 통신을 막기도 가능.  
    + 높은 수준의 분리 정책을 원하면 클러스터 자체를 분리하라.
    
<br/>

**컨트롤러**  
기본 오브젝트 생성/관리를 책임.  

- RC (Replication Controller)
    + Pod 관리/기동
    + Selector  
        : 라벨을 기반으로 RC 가 관리하는 Pod 를 가져온다.
    + Replica 수  
        : RC 가 관리하는 Pod 수. 이 숫자만큼 Pod 가 유지된다.
    + Pod Template  
        : Pod 를 추가로 기동할 때 필요한 Pod 정보 (도커이미지, 포트, 라벨 등)

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/msa/msa-kube-rc-1.jpg" width="700"/>|
|-|
|그림 7 - RC|

<br/>

- Replica Set
    + RC 의 새버전 (Set 기반 Selector)

- Deployment
    + RC 추상화 개념 (실제 운영에서 사용됨)
    
<br/> 
    
[ [← back](https://github.com/cholnh/study-cs#-MSA-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/msa/index.md#MSA) ]