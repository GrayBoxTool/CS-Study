# 🗂️ 자료구조 학습 주제별 요약 및 핵심 질문 가이드

> 참고: [gyoogle tech-interview-for-developer - Data Structure](https://github.com/gyoogle/tech-interview-for-developer#data-structure)

---

### 1. Array vs LinkedList
- **핵심 요약**:
  - **Array**: 메모리 상에 연속적으로 할당됨. 인덱스를 통한 임의 접근(Random Access) 시간복잡도 $O(1)$. 데이터 삽입/삭제 시 원소 이동으로 $O(N)$ 소요.
  - **LinkedList**: 노드들이 데이터와 다음 포인터를 가지며 불연속적 메모리에 위치. 임의 접근 불가하여 순차 탐색 $O(N)$. 삽입/삭제 위치를 알고 있다면 포인터 변경만으로 $O(1)$.
- **빈출 면접 질문**:
  - Q. Array와 LinkedList의 장단점 및 각각 언제 사용하는 것이 적합한가요?
  - Q. 동적 배열(예: Java의 ArrayList, Python의 List)의 동작 원리와 크기 확장(Doubling) 시 시간복잡도는?

---

### 2. Stack & Queue
- **핵심 요약**:
  - **Stack**: LIFO (Last In First Out, 후입선출). 함수 호출 스택, 브라우저 뒤로가기, 괄호 검사 등에 활용.
  - **Queue**: FIFO (First In First Out, 선입선출). 프로세스 스케줄링(BFS, 인쇄 대기열) 등에 활용.
  - **Deque (Double-Ended Queue)**: 양쪽 끝에서 삽입/삭제가 모두 가능한 자료구조.
- **빈출 면접 질문**:
  - Q. Stack 두 개를 사용하여 Queue를 구현하는 방법을 설명해주세요.
  - Q. Queue 두 개를 사용하여 Stack을 구현하는 방법을 설명해주세요.

---

### 3. Tree & Binary Search Tree (BST)

> 📌 **2회차 (11/6)**: 이 주제의 토픽 2개(Tree·이진 트리 / BST)에 대해 각자 예상 질문 2개씩을 **Issue**로 작성합니다. (마감 11/6 13:30, [Issue 템플릿](./expected-questions-issue-template.md))

- **핵심 요약**:
  - **Tree**: 계층적 구조를 표현하는 비선형 자료구조 (노드와 간선으로 구성, 사이클 없음).
  - **Binary Tree**: 각 노드가 최대 2개의 자식을 갖는 트리 (포화 이진 트리, 완전 이진 트리 등).
  - **BST**: 왼쪽 자식 노드 < 부모 노드 < 오른쪽 자식 노드 규칙을 만족.
  - **BST 시간복잡도**: 균형 트리 시 탐색/삽입/삭제 $O(\log N)$, 편향 트리(Skewed Tree) 시 최악 $O(N)$.
- **빈출 면접 질문**:
  - Q. BST의 장점과 한계(최악의 경우)는 무엇인가요?
  - Q. 이진 트리의 순회 방식 4가지(전위, 중위, 후위, 레벨)의 차이는 무엇인가요?

---

### 4. Balanced Tree (AVL Tree & Red-Black Tree)
- **핵심 요약**:
  - BST의 편향 문제를 해결하기 위해 스스로 균형을 유지하는 자가 균형 이진 탐색 트리.
  - **AVL Tree**: 높이 차이(Balance Factor)가 1 이하를 엄격히 유지. 회전(Rotation) 연산이 잦음. 탐색이 빈번한 경우 유리.
  - **Red-Black Tree**: 각 노드에 Red/Black 색상을 부여하고 특정 규칙을 통해 대략적인 균형 유지. 삽입/삭제 시 회전 횟수가 적어 C++ STL `std::map`, Java `TreeMap` 등에 널리 쓰임.
- **빈출 면접 질문**:
  - Q. AVL Tree와 Red-Black Tree의 차이점은 무엇인가요?
  - Q. Red-Black Tree의 5가지 기본 규칙과 색상 반전/회전 과정은 어떻게 되나요?

---

### 5. Heap & Priority Queue (우선순위 큐)
- **핵심 요약**:
  - **Heap**: 완전 이진 트리(Complete Binary Tree) 기반으로 최댓값 또는 최솟값을 $O(1)$에 찾기 위한 자료구조 (Max Heap, Min Heap).
  - 삽입 및 삭제 연산 시 Heapify 과정을 거쳐 $O(\log N)$ 소요.
- **빈출 면접 질문**:
  - Q. Heap과 BST의 차이점은 무엇인가요?
  - Q. Heap을 배열(Array)로 구현할 때 인덱스 계산 공식은 어떻게 되나요?

---

### 6. Hash Table (해시 테이블)
- **핵심 요약**:
  - Key-Value 구조로 데이터를 저장. 해시 함수를 통해 인덱스를 산출하여 평균 $O(1)$에 접근 가능.
  - **해시 충돌(Collision) 해결 기법**:
    1. **Chaining (체이닝)**: 충돌 발생 시 LinkedList나 Red-Black Tree로 연결.
    2. **Open Addressing (개방 주소법)**: 비어있는 다른 버킷을 찾아 저장 (Linear Probing, Quadratic Probing, Double Hashing).
- **빈출 면접 질문**:
  - Q. 해시 충돌(Hash Collision)의 해결 방법 2가지와 각각의 장단점을 설명해주세요.
  - Q. 해시 테이블의 최악 시간복잡도가 $O(N)$이 되는 경우와 이를 방지하기 위한 방법은?

---

### 7. Graph & 탐색 (DFS, BFS)
- **핵심 요약**:
  - **표현 방식**:
    - 인접 행렬(Adjacency Matrix): $O(1)$ 간선 확인, 공간 복잡도 $O(V^2)$ (밀집 그래프에 적합).
    - 인접 리스트(Adjacency List): 정점 간 연결 탐색 효율적, 공간 복잡도 $O(V + E)$ (희소 그래프에 적합).
  - **DFS (깊이 우선 탐색)**: 재귀 또는 Stack 사용, 백트래킹 및 사이클 탐지에 용이.
  - **BFS (너비 우선 탐색)**: Queue 사용, 가중치가 동일한 그래프에서 최단 경로 탐색에 사용.
- **빈출 면접 질문**:
  - Q. DFS와 BFS의 차이점과 각각 어떤 문제 상황에 적합한가요?
  - Q. 인접 행렬과 인접 리스트의 장단점 및 시간/공간 복잡도 비교를 설명해주세요.

---

### 8. Trie (트라이) & B-Tree / B+Tree
- **핵심 요약**:
  - **Trie**: 문자열 검색을 $O(L)$(단어 길이) 만에 수행할 수 있는 트리 자료구조. 자동 완성 기능에 활용되나 메모리 소비가 큼.
  - **B-Tree**: 자식 노드를 2개 이상 가질 수 있는 다원 탐색 트리. 디스크 I/O 횟수를 줄이기 위해 트리의 높이를 낮춤.
  - **B+Tree**: 모든 실제 데이터는 리프 노드에만 저장되고 리프 노드끼리 LinkedList로 연결되어 있어 범위 검색(Range Scan)에 최적화됨. 관계형 데이터베이스(RDBMS)의 인덱스 구조로 널리 채택.
- **빈출 면접 질문**:
  - Q. B-Tree와 B+Tree의 차이점과 데이터베이스 인덱스로 B+Tree를 사용하는 이유는?
  - Q. Trie의 장단점과 단점을 보완하기 위한 압축 트라이에 대해 아시나요?
