# 📑 Stack & Queue 정리

> **발표자**: 권혜강  
> **날짜**: 2026-11-04  
> **카테고리**: Data Structure  
> **참고 링크**: [gyoogle 기술인터뷰 - Data Structure](https://github.com/gyoogle/tech-interview-for-developer#data-structure) · [Java ArrayDeque API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/ArrayDeque.html) · [Java Stack API](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Stack.html) · [Python Tutorial – Data Structures](https://docs.python.org/3/tutorial/datastructures.html)

---

## 1. 개요 및 정의
> 이 기술/개념이 무엇이고 왜 등장했는지 간략히 서술합니다.

- 개념 정의:
  - **Stack (스택)**: 한쪽 끝(top)에서만 삽입/삭제가 일어나는 **LIFO (Last In First Out, 후입선출)** 자료구조. 연산: `push`(넣기), `pop`(꺼내기), `peek`(top 확인).
  - **Queue (큐)**: 한쪽(rear)으로 넣고 반대쪽(front)에서 꺼내는 **FIFO (First In First Out, 선입선출)** 자료구조. 연산: `enqueue`(넣기), `dequeue`(꺼내기), `peek/front`.
  - **Deque (Double-Ended Queue, 덱)**: **양쪽 끝 모두**에서 삽입/삭제가 가능한 자료구조. Stack과 Queue를 모두 표현할 수 있다.
- 등장 배경 및 해결하고자 한 문제:
  - 배열/연결 리스트는 **어디에든 접근 가능**해 자유도가 높은 대신, "순서 규칙"이 필요한 문제(되돌리기, 작업 대기열 등)에서 실수 여지가 크다.
  - 접근 지점을 **제한**(스택: 한쪽 끝, 큐: 양끝의 역할 분리)해서 **규칙을 구조 자체로 강제**하고, 핵심 연산을 **O(1)** 로 만든 추상 자료형(ADT)이다.

---

## 2. 핵심 동작 원리 및 특징
> 개념의 핵심 로직, 구조, 동작 흐름을 시각 자료나 표, 불릿 포인트로 정리합니다.

### 2-1. 구조 도식

```text
Stack (LIFO)                       Queue (FIFO)

   push(D)   pop() → D                dequeue() ←  [ A | B | C | D ] ← enqueue(E)
      ↓        ↑                                   front          rear
    ┌───┐   ← top
    │ D │
    ├───┤                           Deque (양쪽 모두)
    │ C │                           addFirst/removeFirst ⇄ [ A | B | C ] ⇄ addLast/removeLast
    ├───┤
    │ B │
    ├───┤
    │ A │
    └───┘
```

### 2-2. 핵심 원리
- **원리 1 – Stack은 "배열 + top 인덱스" 또는 "연결 리스트의 head"로 구현**: 배열 기반이면 `top` 인덱스만 증감하므로 `push/pop/peek` 모두 **O(1)**. 연결 리스트면 head에 삽입/삭제하므로 역시 O(1).
- **원리 2 – Queue는 "원형 배열(Circular Buffer)" 또는 "연결 리스트(head/tail)"로 구현**: 단순 배열로 만들면 `dequeue` 때마다 앞쪽 원소를 당겨야 해서 O(N)이 된다 → `front`, `rear` 인덱스를 `% capacity` 로 순환시키는 **원형 큐**로 **enqueue/dequeue 모두 O(1)** 달성.
- **원리 3 – Python 공식 문서도 같은 이유로 `list`를 큐로 쓰지 말라고 안내**: *"doing inserts or pops from the beginning of a list is slow"* (나머지 원소를 한 칸씩 밀어야 하므로) → `collections.deque` 사용 권장 (양끝 `append/popleft` O(1)). — [Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html), [collections.deque](https://docs.python.org/3/library/collections.html#collections.deque)
- **원리 4 – Java에서는 `Stack` 클래스보다 `Deque`(`ArrayDeque`)를 쓰라고 안내**
  - `Stack`은 `Vector`를 상속한 레거시 클래스이며, 공식 문서가 *Deque 인터페이스가 더 완전하고 일관된 LIFO 연산을 제공하므로 `Stack` 대신 사용하라(should be used in preference to this class)* 고 명시.
  - `ArrayDeque`: *"This class is likely to be faster than Stack when used as a stack, and faster than LinkedList when used as a queue."* / *"Null elements are prohibited."*
  - 실무 관용구: `Deque<Integer> stack = new ArrayDeque<>();` / `Queue<Integer> queue = new ArrayDeque<>();`
- **원리 5 – Queue 연산 메서드 (Java `Queue` 인터페이스)**: 실패 시 예외를 던지는 쪽(`add/remove/element`)과 `null`/`false`를 반환하는 쪽(`offer/poll/peek`) 두 계열이 있다.

### 2-3. 비교 분석 표

| 구분 | Stack | Queue | Deque |
| :--- | :--- | :--- | :--- |
| 규칙 | LIFO (후입선출) | FIFO (선입선출) | 양끝 삽입/삭제 |
| 주요 연산 | push / pop / peek | enqueue / dequeue / peek | addFirst·addLast / removeFirst·removeLast |
| 삽입·삭제 시간복잡도 | O(1) | O(1) (원형 배열·연결 리스트 구현 시) | O(1) |
| 탐색(검색) | O(N) | O(N) | O(N) |
| 대표 활용 | 함수 호출 스택(콜 스택), 브라우저 뒤로가기, Undo/Redo, 괄호 검사, 후위 표기식 계산, **DFS** | 프로세스/작업 스케줄링, 프린터 대기열, 메시지 큐, **BFS**, 캐시(FIFO) | 슬라이딩 윈도우 최댓값, 스택/큐 겸용, 양방향 탐색(0-1 BFS) |
| 구현 시 주의 | 빈 스택 `pop` → **Underflow**, 고정 배열이 가득 차면 **Overflow** | 배열 큐는 원형 큐로 구현해야 O(1) | Java는 `ArrayDeque` 권장 |
| 장점 | 구현 단순, 연산 O(1), 재귀를 반복문으로 바꿀 때 유용 | 처리 순서 보장(공정성) | 유연함 |
| 단점 | 중간 원소 접근 불가 | 중간 원소 접근 불가, 원형 처리 필요 | 구현이 상대적으로 복잡 |

### 2-4. Stack / Queue 상호 구현 (면접 빈출)

**① Stack 2개로 Queue 만들기** (`inStack`, `outStack`)
```text
enqueue(x): inStack.push(x)
dequeue():  outStack이 비어 있으면 → inStack의 모든 원소를 pop해서 outStack에 push (순서가 뒤집힘 = 큐 순서)
            outStack.pop()
```
- 각 원소는 `inStack → outStack`으로 **최대 한 번만** 옮겨지므로 **상각(Amortized) O(1)** (최악 한 번의 dequeue는 O(N)).

**② Queue 2개로 Stack 만들기** (`q1`, `q2`)
```text
[push 비용 O(N) 방식]
push(x): q2.enqueue(x) → q1의 모든 원소를 q2로 옮김 → q1, q2 이름 교체   (q1의 front가 항상 top)
pop():   q1.dequeue()    → O(1)

[pop 비용 O(N) 방식]
push(x): q1.enqueue(x)   → O(1)
pop():   q1에서 마지막 1개만 남기고 q2로 옮김 → 남은 1개 dequeue → q1, q2 교체
```
- 큐는 순서를 뒤집지 못하므로 한 연산은 O(N)을 감수해야 한다 (push 또는 pop 중 하나).

---

## 3. 실무 / 면접 핵심 포인트
> 면접관이 자주 묻는 꼬리 질문과 이에 대한 명쾌한 답변을 정리합니다.

### Q1. Stack 두 개를 사용하여 Queue를 구현하는 방법을 설명해주세요.
- **A**: `inStack`과 `outStack`을 둡니다. enqueue는 `inStack`에 push하고, dequeue는 `outStack`이 비었을 때만 `inStack`의 모든 원소를 pop해 `outStack`에 push(순서가 뒤집혀 FIFO가 됨)한 뒤 `outStack`에서 pop합니다. 한 원소가 두 스택 사이를 최대 1번만 이동하므로 **상각 O(1)** 입니다.

### Q2. Queue 두 개를 사용하여 Stack을 구현하는 방법을 설명해주세요.
- **A**: push 때 새 원소를 빈 큐 `q2`에 넣고, 기존 `q1`의 원소를 전부 `q2`로 옮긴 뒤 두 큐의 역할을 바꾸면 `q1`의 front가 항상 top이 됩니다. 이 경우 push가 O(N), pop은 O(1)입니다. (반대로 push를 O(1)로 하고 pop에서 마지막 하나만 남기고 옮기는 방식도 있으며, 이 경우 pop이 O(N)입니다.)

### Q3. Java에서 Stack 클래스 대신 ArrayDeque를 쓰라고 하는 이유는?
- **A**: `Stack`은 `Vector` 상속 레거시 클래스라 설계가 오래됐고(공식 문서도 Deque 사용을 권장), 공식 문서가 `ArrayDeque`는 스택으로 쓸 때 `Stack`보다, 큐로 쓸 때 `LinkedList`보다 **빠를 가능성이 높다**고 명시합니다. 단, `ArrayDeque`는 **null 원소 불가**, **스레드 안전하지 않음**이라 멀티스레드에서는 별도 동기화 또는 동시성 컬렉션이 필요합니다.

### Q4. 큐를 배열로 구현할 때의 문제와 해결책은?
- **A**: 단순 배열은 dequeue 후 앞칸이 비어도 `front`만 이동해 공간이 낭비되고(또는 매번 당기면 O(N)), 결국 rear가 끝에 닿아 "가득 찬 것처럼" 보입니다. `front`/`rear`를 `% capacity`로 **순환**시키는 **원형 큐(Circular Queue)** 로 해결하고, 가득 찬 상태와 빈 상태를 구분하려고 칸 하나를 비워두거나 `size` 변수를 둡니다.

### Q5. Stack과 Queue는 각각 어떤 알고리즘에서 쓰이나요?
- **A**: **DFS**는 재귀(= 시스템 콜 스택) 또는 명시적 Stack, **BFS**는 Queue를 사용합니다. 그 외 Stack은 괄호 유효성 검사, 후위 표기식 계산, 브라우저 뒤로가기/Undo, Queue는 작업 스케줄링·프린터 대기열·메시지 큐 등에 쓰입니다.

### Q6. 재귀 호출과 스택의 관계는? Stack Overflow는 왜 발생하나요?
- **A**: 함수가 호출될 때마다 매개변수·지역변수·복귀 주소를 담은 **스택 프레임**이 **호출 스택**에 쌓이고, 반환하면 pop됩니다. 종료 조건이 없거나 재귀 깊이가 너무 깊으면 호출 스택의 허용 크기를 넘어 **StackOverflow**가 발생합니다. 해결책: 종료 조건 점검, 반복문 + 명시적 스택으로 전환, 꼬리 재귀 최적화(지원 언어 한정).

### Q7. (꼬리) 우선순위 큐(PriorityQueue)도 Queue인가요? FIFO인가요?
- **A**: 인터페이스는 Queue지만 **FIFO가 아니라 우선순위 순서**로 꺼냅니다. 보통 **힙(Heap)** 으로 구현해 삽입/삭제가 O(log N)입니다 (3회차 이후 Heap & Priority Queue에서 다룸).

### Q8. (꼬리) Python에서 리스트로 큐를 만들면 안 되나요?
- **A**: 스택은 `append()`/`pop()`으로 충분하지만, 큐를 `list`로 만들어 `pop(0)`을 쓰면 **나머지 원소를 한 칸씩 당기느라 O(N)** 입니다. 공식 문서도 `collections.deque`의 `append/popleft`(양끝 O(1))를 쓰라고 안내합니다.

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
| `Stack`은 LIFO 스택이자 `Vector` 상속, Deque 사용 권장 | [Oracle Java SE 21 – Stack](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Stack.html) |
| `ArrayDeque`: Stack보다·LinkedList보다 빠를 가능성, null 금지, 스레드 비안전, 대부분 연산 상각 상수 시간 | [Oracle Java SE 21 – ArrayDeque](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/ArrayDeque.html) |
| Python `list`로 큐 구현 시 앞쪽 삽입/삭제가 느림 → `deque` 권장 | [Python Tutorial – Data Structures](https://docs.python.org/3/tutorial/datastructures.html) |
| `deque`는 양끝 append/pop이 O(1), `list.pop(0)`/`insert(0, v)`는 O(n) | [Python docs – collections.deque](https://docs.python.org/3/library/collections.html#collections.deque) |
| 스터디 기준 자료 | [gyoogle/tech-interview-for-developer](https://github.com/gyoogle/tech-interview-for-developer) |
