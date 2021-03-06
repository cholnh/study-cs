## 자바
- [String, StringBuffer, StringBuilder 차이](#string-stringbuffer-stringbuilder-차이)
- [불변객체/가변객체](#불변객체가변객체)
- [자바 메모리구조](#자바-메모리구조-heap-perm)
    + heap
    + perm
- [volatile](#volatile)
- [serialize](#serialize-직렬화)
- [transient](#transient)
- [추상 클래스](#추상-클래스)
- [인터페이스](#인터페이스)
- [JVM / GC](#jvm--gc)
- [Class Loader](#class-loader)
- [Collection](#collection)
- [Annotation](#annotation)
- [Generic](#generic)
- [final](#final)
- [오버로딩 vs 오버라이딩](#오버로딩-vs-오버라이딩)
- [Access Modifier](#access-modifier-접근-지정자)
- [Wrapper class / First Collection Class](#wrapper-class--first-collection-class)

[ [← back](https://github.com/cholnh/study-cs#-자바-) ]

## String, StringBuffer, StringBuilder 차이
- String은 불변객체이다. -> 새로운 값을 append 할 때 마다 새로운 객체가 생성 -> 가비지 증가로 인한 힙메모리 부족 -> GC빈도 증가 (메모리, 성능 비효율)
- 가변성을 갖는 StringBuilder 도입. 동일 객체내에서 문자열 변경 가능. 그러나 Thread-UnSafe.
- StringBuffer 도입. Thread-Safe 하다는 것은 멀티 스레딩 환경에서 안전하다는 것. 
  > Thread-Safe: 변수 혹은 객체가 여러 스레드로부터 동시에 접근이 이루어져도 프로그램 실행에 문제가 없음을 뜻함.
- Thread-Safe하기 위해서 는 재진입성(Re-entrancy)을 띄어야 한다, 각 스레드의 호출마다 정확한 결과가 리턴되어야함,
- 공유 자원을 접근할 때 하나의 스레드만 접근하며 write과정은 atomic 해야 함.)

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## 불변객체/가변객체
- 불변 객체 Immutable object  
생성 후 그 상태를 바꿀 수 없는 객체
- 가변 객체 mutable object  
생성 후에도 상태를 변경할 수 있는 객체
- 이점  
복제나 비교를 위한 조작을 단순화, 성능 개선
- (스택 영역에 있는)불변 객체가 가리키고 있는 (힙 영역에 있는)데이터 자체의 변화 불가능
> cf) **실제 데이터**는 힙 영역에 저장  
> 힙 영역을 가리키는 주소 값은 Stack 영역에서 가지고 있음

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## 자바 메모리구조 (heap, perm)

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## volatile
- 변수를 Main Memory에 저장하겠다는 것을 명시함.
- 매번 변수를 읽을 때마다 CPU Cache에 저장된 값이 아닌 Main Memory 에서 읽음. (멀티스레딩으로 인한 변수 값 불일치 문제 때문)
- 스레드들은 멀티 스레딩 환경에서 제각각 사용하는 CPU Cache 영역이 다름, 캐시 내 값(변수 값)이 제각각 다르게 됨.
  > 주의) 여러 스레드가 write 하는 것에 원자성(atomic)을 보장하기 위해서는 synchronized 또는 명시적락(Reentrant lock) 사용.

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## serialize (직렬화)
- JVM 메모리(힙 또는 스택)내 객체를 외부에서 사용할 수 있도록 byte 형태 데이터 변환.
- (Serializable 구현)객체 -> (ByteArrayOutputStream -> ObjectOutputStream) ObjectOutputStream을 열어서 직렬화 -> 바이트 배열
- serialVersionUID 이 동일해야 역/직렬화 가능, 또한 구조가 변하면 InvalidClassException 발생
  > 주로 서블릿세션(메모리위에선 필요없지만 세션 클러스터링, OAuth 정보 db저장 등에 필요), 캐시 등  
  > 메모리기반 Cache 저장용량 한계 -> Json 직렬화(경량화)

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## transient
- 자바 직렬화중 제외하고 싶은 멤버변수를 명시하는 키워드.

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## 추상 클래스

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## 인터페이스

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## JVM / GC

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## class loader

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## Collection

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## Annotation

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## Generic

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## final
- 참조 타입에서 변수의 재할당만을 금지하는 키워드
- 참조 타입에서의 불변 주의사항 (아래 코드 참조)

```java
public class FirstClassCollection {
    private final List<Object> list;

    public FirstClassCollection(List<Object> list) {
        this.list = list;
    }
}
```

> 위와 같이 `List`를 `final`로 씌워도 `add()` 사용이 가능하다.(내부 인스턴스의 변경)  
> 완전한 불변객체로 만들기 위해서는 `setter`제거, `getter`반환 값을 `Collections.unmodifiableList()` 사용하여 반환.  

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## 오버로딩 vs 오버라이딩

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## Access Modifier (접근 지정자)

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]

<br/>

## Wrapper class / First Collection Class

[ [← back](https://github.com/cholnh/study-cs#-자바-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/java/index.md#자바) ]