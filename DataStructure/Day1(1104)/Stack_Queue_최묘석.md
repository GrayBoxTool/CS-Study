# 📑 Stack & Queue 구조 및 활용 사례 정리

> **발표자**: 최묘석  
> **날짜**: 2026-11-03  
> **카테고리**: Data Structure  
> **참고 링크**: [gyoogle 기술인터뷰 - Stack & Queue](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Stack%20%26%20Queue.md)

---

## 1. 개요 및 정의

> Stack과 Queue의 구조 및 동작 방식, 각각의 활용 사례를 정리.

- **Stack(스택)**: LIFO(Last In First Out, 후입선출) 구조로, 가장 나중에 들어온 데이터가 가장 먼저 나오는 자료구조이다. 데이터의 삽입과 삭제가 같은 방향에서 이루어진다.
- **Queue(큐)**: FIFO(First In First Out, 선입선출) 구조로, 가장 먼저 들어온 데이터가 가장 먼저 나오는 자료구조이다. 데이터의 삽입은 rear, 삭제는 front에서 이루어진다.
- **사용 목적**: Stack은 최근에 저장한 데이터를 먼저 처리해야 할 때, Queue는 입력된 순서대로 데이터를 처리해야 할 때 사용한다.

---

## 2. 핵심 동작 원리 및 특징

> 교육자료의 Java 코드를 익숙한 Python으로 바꿔 생각하며 동작 원리를 이해하려고 함.

- **Stack의 동작 원리**: `push()`로 데이터를 추가하고 `pop()`으로 가장 위에 있는 데이터를 제거한다. 배열로 구현할 경우 top 또는 스택 포인터(SP)를 이용해 마지막 데이터의 위치를 관리할 수 있다.
- **Queue의 동작 원리**: `enqueue()`로 rear에 데이터를 추가하고 `dequeue()`로 front의 데이터를 제거한다. front와 rear를 통해 데이터의 입력과 출력 위치를 관리한다.
- **원형 큐(Circular Queue)**: 일반적인 배열 기반 큐에서 앞쪽에 빈 공간이 생겨도 재사용하기 어려운 문제를 개선한 구조이다. `(index + 1) % size`를 이용해 배열의 끝에서 다시 처음으로 돌아가도록 구현한다.
- **연결 리스트 기반 구현**: Stack과 Queue 모두 LinkedList로 구현할 수 있으며, 노드의 연결 관계를 이용해 데이터를 삽입하거나 삭제한다.

**Python으로 이해한 예시**

```python
# Stack: Python list 활용
stack = []

stack.append(10)
stack.append(20)
stack.append(30)

print(stack.pop())  # 30
print(stack.pop())  # 20


# Queue: collections.deque 활용
from collections import deque

queue = deque()

queue.append(10)
queue.append(20)
queue.append(30)

print(queue.popleft())  # 10
print(queue.popleft())  # 20
```

| 구분            | Stack                     | Queue                       |
| :-------------- | :------------------------ | :-------------------------- |
| 처리 방식       | LIFO (후입선출)           | FIFO (선입선출)             |
| 데이터 삽입     | push (top)                | enqueue (rear)              |
| 데이터 삭제     | pop (top)                 | dequeue (front)             |
| 주요 특징       | 가장 최근 데이터부터 처리 | 가장 오래된 데이터부터 처리 |
| 삽입 시간복잡도 | O(1)                      | O(1)                        |
| 삭제 시간복잡도 | O(1)                      | O(1)                        |
| 활용 사례       | 함수 호출, 뒤로 가기, DFS | BFS, 작업 대기열, 버퍼      |

※ 시간복잡도는 적절한 자료구조로 구현했을 때의 일반적인 기준이다. Python의 `list.append()`와 `list.pop()`은 평균적으로 O(1)이며, `deque.append()`와 `deque.popleft()`는 O(1)이다.

---

## 3. 실무 / 면접 핵심 포인트

### Q1. Stack과 Queue의 가장 큰 차이점을 설명하시오.

- **A**: Stack은 가장 나중에 들어온 데이터가 먼저 나오는 LIFO 구조이고, Queue는 가장 먼저 들어온 데이터가 먼저 나오는 FIFO 구조입니다. 따라서 최근 작업부터 처리해야 한다면 Stack을, 입력된 순서를 유지해야 한다면 Queue를 사용하는 것이 적절합니다.

### Q2. Python에서 Queue를 구현할 때 list보다 deque를 사용하는 이유를 설명하시오.

- **A**: 

  Python의 `list`에서 `pop(0)`을 사용하면 첫 번째 요소를 제거한 후 나머지 요소들을 앞으로 이동시켜야 하므로 O(n)이 걸립니다. 반면 `collections.deque`의 `popleft()`는 O(1)로 처리할 수 있어 Queue를 구현할 때 더 효율적입니다.

### 실제 활용 사례

**Stack - 웹 브라우저 방문 기록**

브라우저의 뒤로 가기 기능에서 LIFO 구조를 활용할 수 있다는 사례를 조사했다.

- A → B → C 순서로 방문한 뒤 뒤로 가기를 누르면 B로 이동
- 가장 최근의 방문 상태부터 되돌리는 방식
- 실제 브라우저에서는 앞으로 가기 등의 기록도 별도로 관리해야 함

**Stack - 함수 호출 관리**

함수가 다른 함수를 호출하면 호출 정보가 스택에 쌓이고, 마지막에 호출된 함수부터 실행을 마친다.

**Queue - 서버 요청 처리**

서버에서 대기 중인 작업을 Queue에 저장하고, 먼저 들어온 작업부터 처리하는 사례를 조사했다.

- 요청을 받은 순서대로 대기열에 추가
- 작업자(worker)가 대기열에서 작업을 꺼내 처리
- 실제 서비스에서는 우선순위나 병렬 처리에 따라 완료 순서가 달라질 수 있음

**Queue - BFS 탐색**

BFS는 먼저 발견한 노드부터 탐색하기 위해 Queue를 사용하며, 시작점에서 가까운 노드부터 탐색할 수 있다.

### 학습하며 느낀 점

Stack과 Queue의 실제 활용 사례를 찾아보면서 **데이터를 처리하는 순서가 자료구조 선택의 기준**이 된다는 점을 확인했다.

브라우저 방문 기록과 함수 호출은 최근 작업을 먼저 처리하는 Stack의 특성과 연결되며, 서버의 작업 대기열과 BFS는 먼저 들어온 데이터를 처리하는 Queue의 특성과 연결된다.

Python에서는 `list`와 `deque`로 두 구조를 간단하게 구현할 수 있지만, 같은 데이터라도 처리 방식에 따라 적합한 구현이 달라진다는 점을 정리했다.

---

## 4. 오프라인 모임 Q&A 기록 (발표 후 작성)

> 스터디원들과 나눈 질문이나 토론 내용을 발표 후 작성.

- **Q (스터디원 A)**:
- **A (발표자)**:
- **느낀 점 / 보충할 점**:
