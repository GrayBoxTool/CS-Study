# 📑 Array vs LinkedList 정리

> **발표자**: 권혜강  
> **날짜**: 2026-11-04  
> **카테고리**: Data Structure  
> **참고 링크**: [gyoogle 기술인터뷰 - Data Structure](https://github.com/gyoogle/tech-interview-for-developer#data-structure) · [Java ArrayList API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/ArrayList.html) · [Java LinkedList API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/LinkedList.html) · [Bjarne Stroustrup - Are lists evil?](https://isocpp.org/blog/2014/06/stroustrup-lists)

---

## 1. 개요 및 정의
> 이 기술/개념이 무엇이고 왜 등장했는지 간략히 서술합니다.

- 개념 정의:
  - **Array (배열)**: 같은 타입의 원소를 **메모리의 연속된 공간**에 나란히 저장하고, **인덱스**로 바로 접근하는 자료구조.
  - **LinkedList (연결 리스트)**: 각 **노드(데이터 + 다음/이전 노드를 가리키는 참조)** 를 포인터로 이어 붙인 자료구조. 노드들은 메모리상 **떨어져 있어도 된다(비연속)**.
- 등장 배경 및 해결하고자 한 문제:
  - 데이터를 "순서대로" 저장하는 가장 기본적인 두 가지 방식이며, **접근(Read)에 강한 쪽 vs 삽입/삭제(Write)에 유연한 쪽**이라는 트레이드오프를 가진다.
  - 순수 배열은 **크기가 고정**이고 중간 삽입/삭제 시 원소를 밀어야 한다 → 크기를 유연하게 만든 **동적 배열(Java `ArrayList`, Python `list`)** 과, 포인터만 바꿔 끼우는 **연결 리스트**가 각각 보완책으로 쓰인다.

---

## 2. 핵심 동작 원리 및 특징
> 개념의 핵심 로직, 구조, 동작 흐름을 시각 자료나 표, 불릿 포인트로 정리합니다.

### 2-1. 메모리 구조

```text
Array (연속 메모리)
 index:   0     1     2     3     4
        ┌─────┬─────┬─────┬─────┬─────┐
        │  A  │  B  │  C  │  D  │  E  │   ← 시작 주소 + index × 원소크기 로 바로 계산
        └─────┴─────┴─────┴─────┴─────┘

LinkedList (비연속 메모리, 노드를 참조로 연결)
 head
  │
  ▼
 ┌───┬───┐    ┌───┬───┐    ┌───┬───┐
 │ A │ ●─┼───▶│ B │ ●─┼───▶│ C │ ∅ │      (Singly)
 └───┴───┘    └───┴───┘    └───┴───┘
   ※ Doubly(이중)는 prev 참조도 가짐: ∅ ◀─ A ⇄ B ⇄ C ─▶ ∅
```

### 2-2. 핵심 원리
- **원리 1 – Array는 "주소 계산"으로 O(1) 접근**: `주소 = 시작주소 + index × 원소크기`. 그래서 인덱스 접근이 항상 O(1). 반대로 중간에 끼워 넣으면 뒤 원소를 전부 한 칸씩 밀어야 해서 **O(N)**.
- **원리 2 – LinkedList는 "따라가기"로 접근**: i번째 원소를 찾으려면 head부터 `next`를 i번 따라가야 하므로 **O(N)**. 대신 **삽입/삭제할 위치의 노드를 이미 알고 있다면 참조 2~3개만 바꾸므로 O(1)**.
  - Java `LinkedList`는 이중 연결 리스트이며, 인덱스 접근 시 *"the beginning or the end, whichever is closer"* 쪽부터 순회한다 (그래도 최악 O(N)). — [Java LinkedList API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/LinkedList.html)
- **원리 3 – 동적 배열(ArrayList / Python list)의 확장**: 내부 배열이 가득 차면 **더 큰 배열을 새로 할당 → 기존 원소 전체 복사 → 기존 배열 버림**. 한 번 확장은 O(N)이지만, 용량을 매번 곱셈(예: ×1.5, ×2)으로 키우면 N번 추가의 총 비용이 O(N)이라 **append 한 번당 상각(Amortized) O(1)** 이다.
  - Java 공식 문서: *"The `add` operation runs in amortized constant time, that is, adding n elements requires O(n) time."* — [Java ArrayList API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/ArrayList.html)
  - 증가 비율은 **구현 세부사항**이다. (OpenJDK `ArrayList`는 약 1.5배, CPython `list`는 약 1.125배 + 상수 정도로 over-allocate — 스펙이 아니라 구현에 따라 다름)
  - 미리 크기를 알면 `ensureCapacity` / 초기 용량 지정으로 재할당 횟수를 줄일 수 있다 (공식 문서: *"This may reduce the amount of incremental reallocation."*).
- **원리 4 – 캐시 지역성(Cache Locality)**: 배열은 연속이라 CPU 캐시 라인에 이웃 원소가 같이 올라와 순회가 매우 빠르다. 연결 리스트는 노드가 흩어져 있어 포인터를 따라갈 때마다 캐시 미스가 나기 쉽다. 노드마다 **참조(포인터) 저장 공간 + 객체 할당 비용**도 추가로 든다.

### 2-3. 비교 분석 표

| 구분 | Array / 동적 배열 (ArrayList) | LinkedList |
| :--- | :--- | :--- |
| 메모리 배치 | 연속 | 비연속 (노드가 참조로 연결) |
| 크기 | 순수 배열은 고정 / 동적 배열은 자동 확장(재할당·복사 발생) | 필요할 때마다 노드 추가 (사실상 제한 없음) |
| 인덱스 접근 `get(i)` | **O(1)** | O(N) |
| 탐색(값 검색) | O(N) | O(N) |
| 맨 앞 삽입/삭제 | O(N) (전체 이동) | **O(1)** |
| 맨 뒤 삽입 | 상각 O(1) (가끔 확장 시 O(N)) | O(1) (tail 참조 보유 시, Java LinkedList는 보유) |
| 중간 삽입/삭제 | O(N) (원소 이동) | 위치 탐색 O(N) + 연결 변경 O(1) = **결국 O(N)** (노드를 이미 알면 O(1)) |
| 메모리 오버헤드 | 적음 (여분 용량 정도) | 큼 (노드마다 참조 1~2개 + 객체 헤더) |
| 캐시 효율 | 좋음 | 나쁨 |
| 장점 | 빠른 임의 접근, 캐시 친화, 메모리 효율 | 앞/중간(노드를 알 때) 삽입·삭제 O(1), 크기 확장 시 복사 없음 |
| 단점 | 중간/앞 삽입·삭제 비용, 확장 시 복사 | 임의 접근 불가(O(N)), 포인터 메모리 + 캐시 미스 |

> 💡 **면접 포인트**: "LinkedList는 삽입/삭제가 O(1)"은 **"위치(노드)를 이미 알고 있을 때"** 한정이다. 인덱스로 위치를 찾는 순간 O(N)이 된다.

### 2-4. 언제 무엇을 쓰나
- **Array / ArrayList**: 조회가 많고, 데이터 끝에 추가하는 패턴, 크기를 대충 예측 가능 → **기본 선택지**.
- **LinkedList**: 앞/뒤에서 빈번한 삽입·삭제(큐/덱), 이미 노드(이터레이터)를 쥔 채 중간 삽입·삭제를 반복, 앞쪽 삽입/삭제 때문에 재할당·복사가 부담될 때. (단, 큐/덱 용도로는 Java에서 `ArrayDeque`가 보통 더 빠르다고 문서에 명시 → Stack & Queue 정리 참고)
- Python `list`는 연결 리스트가 아니라 **동적 배열**이다. 공식 문서도 `pop(0)`/`insert(0, v)`에 **O(n) 메모리 이동 비용**이 든다고 설명한다. — [Python collections.deque](https://docs.python.org/3/library/collections.html#collections.deque)

---

## 3. 실무 / 면접 핵심 포인트
> 면접관이 자주 묻는 꼬리 질문과 이에 대한 명쾌한 답변을 정리합니다.

### Q1. Array와 LinkedList의 장단점 및 각각 언제 사용하는 것이 적합한가요?
- **A**: Array는 연속 메모리 덕분에 **인덱스 접근 O(1)**, 캐시 효율이 좋고 메모리 오버헤드가 작지만, 중간/앞 삽입·삭제가 O(N)이고 크기가 고정(또는 확장 시 복사)이라는 단점이 있습니다. LinkedList는 **노드를 알고 있을 때 삽입·삭제가 O(1)** 이고 크기 변경이 자유롭지만, 임의 접근이 O(N)이고 노드마다 포인터 메모리와 캐시 미스 비용이 있습니다. 조회·순회 위주면 배열(ArrayList), 앞/뒤 삽입·삭제 위주이거나 노드 기반 조작이 잦으면 연결 리스트가 적합합니다.

### Q2. 동적 배열(Java ArrayList, Python list)의 동작 원리와 크기 확장(Doubling) 시 시간복잡도는?
- **A**: 내부에 고정 크기 배열을 두고, 가득 차면 더 큰 배열을 새로 만들어 **전체를 복사**합니다. 한 번 확장은 O(N)이지만 용량을 일정 비율(×1.5, ×2 등)로 키우기 때문에 **N번 append의 총 비용이 O(N)** → **append 1회당 상각(Amortized) O(1)** 입니다. (예: 용량 1→2→4→8… 로 두 배씩 늘면 복사 총합은 1+2+4+…+N/2 < N.) 공식 문서도 `add`를 *amortized constant time* 으로 명시합니다.

### Q3. LinkedList는 삽입/삭제가 O(1)인데, 왜 실제로는 ArrayList가 더 빠른 경우가 많나요?
- **A**: ① 중간 삽입 전에 **위치를 찾는 탐색이 O(N)** 이고, ② 연결 리스트는 노드가 흩어져 **캐시 미스**가 잦고 노드 객체 할당/GC 비용이 들기 때문입니다. 반면 배열은 연속이라 원소 이동(`memmove`/`System.arraycopy`)도 캐시 친화적으로 빠릅니다. C++ 창시자 Stroustrup도 "중간 삽입/삭제가 많으니 list"라는 직관을 *"completely and dramatically wrong"* 이라고 평하며, **"use std::vector by default"**, **"use a contiguous representation unless there is a good reason not to"** 라고 말합니다. — [isocpp.org](https://isocpp.org/blog/2014/06/stroustrup-lists) (단, 항상 **측정**이 우선이라는 점도 함께 강조)

### Q4. Java의 배열(`int[]`)과 `ArrayList`의 차이는?
- **A**: 배열은 **고정 크기**이고 기본형(primitive)을 직접 담을 수 있습니다. `ArrayList`는 **크기가 자동으로 늘어나는 List 구현체**이며 내부적으로 배열을 쓰되 **객체(참조 타입)만** 담기 때문에 `int`는 `Integer`로 박싱됩니다. 제네릭과 `add/remove/contains` 같은 편의 메서드를 제공합니다.

### Q5. 단일 연결 리스트(Singly)와 이중 연결 리스트(Doubly)의 차이는?
- **A**: Singly는 `next`만 가져 메모리가 적지만 **역방향 이동과 이전 노드 접근이 불가**해 특정 노드 삭제 시 이전 노드를 알아야 합니다(탐색 필요). Doubly는 `prev`도 가져 **양방향 순회와 노드 삭제가 O(1)** 이지만 노드당 참조가 하나 더 듭니다. Java `LinkedList`는 이중 연결 리스트이며, 인덱스 접근 시 head/tail 중 **가까운 쪽부터** 순회합니다.

### Q6. 두 자료구조는 스레드 안전한가요?
- **A**: 아니요. Java 공식 문서 기준 `ArrayList`와 `LinkedList` 모두 **synchronized 되어 있지 않아**, 여러 스레드가 구조를 변경한다면 외부에서 동기화하거나 `Collections.synchronizedList` 등을 사용해야 합니다.

### Q7. (꼬리) 앞쪽 삽입이 잦다면 ArrayList를 쓰면 안 되나요?
- **A**: 앞쪽 삽입/삭제는 매번 O(N) 이동이 필요하므로 불리합니다. 큐/덱처럼 양끝 연산이 중심이면 `ArrayDeque`(원형 배열 기반) 또는 연결 리스트가 낫습니다. Python도 `list.pop(0)` 대신 `collections.deque`를 쓰라고 공식 문서가 안내합니다.

---

## 4. 오프라인 모임 Q&A 기록 (발표 후 작성)
> 카페 모임에서 스터디원들과 나눈 질문이나 토론 내용을 기록합니다.

- **Q (스터디원 A)**: 
- **A (발표자)**: 
- **느낀 점 / 보충할 점**: 

---

## 5. 근거 자료 (출처)
| 내용 | 출처 |
| :--- | :--- |
| ArrayList: get/set/size 상수 시간, add는 상각 상수 시간, 그 외 선형, ensureCapacity, 비동기화 | [Oracle Java SE 21 – ArrayList](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/ArrayList.html) |
| LinkedList: 이중 연결 리스트(List+Deque), 인덱스 접근 시 가까운 끝부터 순회, 비동기화 | [Oracle Java SE 21 – LinkedList](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/LinkedList.html) |
| Python list는 `pop(0)`/`insert(0, v)`에 O(n) 이동 비용, deque는 양쪽 O(1) | [Python docs – collections.deque](https://docs.python.org/3/library/collections.html#collections.deque), [Python Tutorial – Data Structures](https://docs.python.org/3/tutorial/datastructures.html) |
| 캐시 효과, 연속 메모리 기본 권장, 리스트 직관 반박 | [Bjarne Stroustrup – Are lists evil? (isocpp.org)](https://isocpp.org/blog/2014/06/stroustrup-lists) |
| 스터디 기준 자료 | [gyoogle/tech-interview-for-developer](https://github.com/gyoogle/tech-interview-for-developer) |
