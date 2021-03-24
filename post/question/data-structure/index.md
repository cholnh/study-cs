## 자료구조
- [해시 테이블 설명](#해시-테이블-설명)
- [Separate Chaining 방식 해결 (JDK 내부에서 사용중)](#separate-chaining-방식-해결-jdk-내부에서-사용중)
- [Open Addressing 방식 해결](#open-addressing-방식-해결)
- [자바 HashMap (자바는 Amortized Constant Time을 위해 어떻게 해시 충돌 가능성을 줄이는가?)](#자바-hashmap-자바는-amortized-constant-time을-위해-어떻게-해시-충돌-가능성을-줄이는가)
- [바이너리 트리](#바이너리-트리)
- [BST (Binary Search Tree)](#bst-binary-search-tree)
- [Graph](#graph)

[ [← back](https://github.com/cholnh/study-cs#-자료구조-) ]

## 해시 테이블 설명
- key에 해당하는 value를 저장하는 데이터 구조.
- hash function을 통해 key에 대한 hash 값을 구하고 buckets 의 인덱스로 사용한다.
- hash function을 한 번만 수행하기 때문에 속도가 매우 빠름.
- 충돌 처리 알고리즘   
hash function으로 index를 구할 때 중복 index가 생성되는 것을 충돌이라 한다.

## Separate Chaining 방식 해결 (JDK 내부에서 사용중)
- index 끝부분이 -> Linked List (참조)
- 충돌시, List 맨 뒤에 추가 (List 선형검색)
> cf) jdk 1.8 의 경우 노드 8개 이하 : List 사용, 8개 이상 Tree 사용 (select 성능을 높임)

## Open Addressing 방식 해결
- 해시 테이블(buckets) 빈 공간을 활용하는 방식
- 그 중 Linear Probing 방식은 선형으로 다음 노드들이 비어있는지 계속 검사.
> cf) 삭제 처리가 어려움, 삭제가 일어날때, 삭제한 후에 연결 역할을 하는 Dummy node를 삽입함, 점점 쌓이다 보면 성능저하 발생,

- Resizing  
버킷의 사이즈가 작으면 Open Addressing 방식이든, Separate Chaining 방식이든 검색 성능이 저하 됨.  
리사이징을 통해 새로운 버킷을 생성해야 성능 향상.

## 자바 HashMap (자바는 Amortized Constant Time을 위해 어떻게 해시 충돌 가능성을 줄이는가?)
- 자바 컬렉션 프레임워크 Map 인터페이스의 구현체.
- 키에 대한 해시 값을 사용하여 값을 저장하고 조회하며, 키-값 쌍의 개수에 따라 동적으로 크기가 중가하는 associate array(=Map<K,V>) 이다.
> cf) 키 집합인 정의역과, 값 집합인 공역의 대응에 해시 함수를 이용.

- Integer, Boolean 같은 객체는 값 자체를 해시함수 대상으로 사용할 수 있음.
- String, POJO에 대하여는 완전한 해시함수 제작이 사실상 불가능.
> 논리적으로 생성가능 객체수가 2^32 보다 많을 수 있음. 2^32 배열을 해시맵이 가지고 있어야 함 = 불가능

- 객체의 해시코드 나머지값을 해시 버킷 인덱스 값으로 사용한다. (정수 범위보다 작은 M, 그 크기의 배열을 해시버킷으로 사용)  
` int index = x.hashCode() % M  `

```java
static int hashCode(String key) {
    int hash = 0;
    char[] ch = key.toCharArray();
    for (int i = 0; i < key.length(); i++) {
        hash = hash * 31 + ch[i];
    }
    return hash;
}
```

## 바이너리 트리

## BST (Binary Search Tree)

## Graph

[ [← back](https://github.com/cholnh/study-cs#-자료구조-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/data-structure/index.md#자료구조) ]