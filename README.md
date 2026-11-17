# ☕ CS-Study (Computer Science 기술 면접 스터디)

> **"지식을 나누며 함께 성장하는 주 2회 CS 기술 면접 아카이빙 스터디"**  
> SSAFY 일과 후 카페에 모여 준비한 주제를 짧게 발표하고 질의응답을 나눈 뒤, GitHub에 기록하여 취업 준비를 위한 우리만의 레퍼런스를 구축합니다.

---

## 👥 스터디원 (총 7명)

<table>
  <tr>
    <td align="center" width="120px">
      <a href="https://github.com/strongsun806">
        <img src="https://github.com/strongsun806.png" width="80px" alt="권혜강 프로필" style="border-radius: 50%;" /><br />
        <sub><b>권혜강</b></sub>
      </a><br />
      <a href="https://github.com/strongsun806">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/GrayBoxTool">
        <img src="https://github.com/GrayBoxTool.png" width="80px" alt="최묘석 프로필" style="border-radius: 50%;" /><br />
        <sub><b>최묘석</b></sub>
      </a><br />
      <a href="https://github.com/GrayBoxTool">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/aaaaef">
        <img src="https://github.com/aaaaef.png" width="80px" alt="최승우 프로필" style="border-radius: 50%;" /><br />
        <sub><b>최승우</b></sub>
      </a><br />
      <a href="https://github.com/aaaaef">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/gudtjq32450">
        <img src="https://github.com/gudtjq32450.png" width="80px" alt="윤형섭 프로필" style="border-radius: 50%;" /><br />
        <sub><b>윤형섭</b></sub>
      </a><br />
      <a href="https://github.com/gudtjq32450">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/peanut-cherry">
        <img src="https://github.com/peanut-cherry.png" width="80px" alt="최나현 프로필" style="border-radius: 50%;" /><br />
        <sub><b>최나현</b></sub>
      </a><br />
      <a href="https://github.com/peanut-cherry">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/xodrndishfwk-crypto">
        <img src="https://github.com/xodrndishfwk-crypto.png" width="80px" alt="김영웅 프로필" style="border-radius: 50%;" /><br />
        <sub><b>김영웅</b></sub>
      </a><br />
      <a href="https://github.com/xodrndishfwk-crypto">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
    <td align="center" width="120px">
      <a href="https://github.com/sue9585">
        <img src="https://github.com/sue9585.png" width="80px" alt="조수연 프로필" style="border-radius: 50%;" /><br />
        <sub><b>조수연</b></sub>
      </a><br />
      <a href="https://github.com/sue9585">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
    </td>
  </tr>
</table>

---

## 📅 진행 현황 & 다음 일정

| 회차 | 날짜 | 주제 | 상태 |
| :---: | :---: | :--- | :---: |
| 1회차 | 11/4 (수) | DS: Array vs LinkedList / Stack & Queue<br>NW: OSI 7 계층 & TCP/IP 4 계층 | ✅ 완료 |
| 2회차 | 11/6 (금) | DS: Tree 기초 & BST (예상 질문 Q&A)<br>NW: 네트워크 전체 흐름 개요 | ✅ 완료 |
| 3회차 | 11/10 (화) 18:30 · 투썸플레이스 | DS: Balanced Tree (AVL, Red-Black)<br>NW: TCP vs UDP / TCP Handshake, TCP 제어 기법 / 포트 포워딩 | ✅ 완료 |
| 4회차 | 11/12 (목) · SSAFY 건물 내부 / 각자 개인 공간 | DS: Heap & Priority Queue / Hash Table<br>NW: HTTP vs HTTPS / SSL 핸드셰이크 | ✅ 완료 |
| 5회차 | 11/17 (화) 19:00 · 최묘석 집 | DS: Graph 기본 & DFS / BFS<br>NW: HTTP 1.1 vs 2.0 vs 3.0 | ✅ 완료 |
| 6회차 | 11/20 (금) 19:00 · 최묘석 집 | DS: 최단 경로 알고리즘 / MST<br>NW: DNS 동작 원리 / 브라우저에 URL 입력 시 흐름 | 🔜 예정 |

### ✅ 2회차 (11/6) 요약

<details>
<summary>펼쳐서 보기</summary>

**DS: Tree 기초 & BST**

- 트리는 연결되고 사이클이 없는 그래프라서, 노드가 N개면 간선은 항상 N-1개입니다.
- 이진 트리는 모양 규칙, BST는 값의 정렬 규칙까지 포함합니다. BST 판별은 직속 자식만 비교하면 오답이고, 범위 전달이나 중위 순회로 확인합니다.
- BST는 정렬된 순서로 넣으면 편향 트리가 되어 O(N)으로 퇴화하고, 이를 막는 것이 자가 균형 트리(AVL, Red-Black)입니다.
- 자식이 둘인 노드를 삭제할 땐 중위 선행자나 후속자로 대체합니다.

**NW: 네트워크 전체 흐름 개요**

- 구성: 노드와 간선, 호스트, 네트워크 장비, 통신 매체, 메시지. 서버와 클라이언트는 기계가 아니라 역할입니다.
- 범위: LAN, CAN, MAN, WAN. 인터넷은 WAN의 대표 예시일 뿐입니다.
- 교환 방식: 회선 교환(길 예약)과 패킷 교환(쪼개서 전송). 오늘날 인터넷은 대부분 패킷 교환입니다.
- 요청 흐름: DNS로 IP 획득, TCP 연결, TLS, HTTP 요청, 응답, 렌더링.
- 캡슐화: TCP, IP, 링크 헤더를 차례로 붙이고, 라우터는 구간마다 링크 포장(MAC)을 새로 씌웁니다.
- 이슈에서 나온 추가 주제(포트 포워딩, NAPT)는 3회차에서 이어서 다룹니다.

</details>

### ✅ 3회차 (11/10) 요약

<details>
<summary>펼쳐서 보기</summary>

**📂 발표 자료**

| 파트 | 발표자 | 자료 |
| :---: | :---: | :--- |
| DS | 최묘석, 김영웅 | [Balanced Tree (AVL, Red-Black)_최묘석.md](./DataStructure/Day3/Balanced%20Tree%20(AVL,%20Red-Black)_최묘석.md)<br>[AVL_RedBlack_발표자료_22페이지.pdf](./DataStructure/Day3/AVL_RedBlack_발표자료_22페이지.pdf) |
| NW | 조수연, 권혜강 | [TCP_Handshake_조수연_발표자료.pdf](./Network/Day3/TCP_Handshake_조수연_발표자료.pdf) ([pptx](./Network/Day3/TCP_Handshake_조수연_발표용.pptx))<br>[3회차_NW_TCP_UDP_포트포워딩_권혜강.pdf](./Network/Day3/3회차_NW_TCP_UDP_포트포워딩_권혜강.pdf) |

---

#### 🌳 DS: Balanced Tree (AVL, Red-Black)

**왜 필요한가**

- BST는 정렬된 값을 순서대로 넣으면 한쪽으로 치우쳐 탐색이 O(N)이 됩니다.
- 균형 트리는 높이를 O(log N)으로 묶어 탐색·삽입·삭제의 최악 시간을 O(log N)으로 보장합니다.

**AVL 트리**

- 균형 인수 `BF = 왼쪽 높이 - 오른쪽 높이`가 모든 노드에서 -1, 0, +1이어야 합니다.
- 균형이 깨지면 회전합니다. 회전은 값을 바꾸지 않고 부모·자식 연결만 바꾸며, BST 대소 관계는 그대로 유지됩니다.

| 유형 | 발생 위치 | 해결 |
| :---: | :--- | :--- |
| LL | 왼쪽 자식의 왼쪽 | 오른쪽 회전 |
| RR | 오른쪽 자식의 오른쪽 | 왼쪽 회전 |
| LR | 왼쪽 자식의 오른쪽 | 왼쪽 회전 → 오른쪽 회전 |
| RL | 오른쪽 자식의 왼쪽 | 오른쪽 회전 → 왼쪽 회전 |

- **삽입**: 회전 한 번(단일 또는 이중)이면 위쪽까지 균형이 맞춰집니다.
- **삭제**: 회전 후 서브트리 높이가 줄 수 있어 루트까지 올라가며 반복합니다. 회전이 최대 O(log N)번 일어날 수 있습니다.

**Red-Black 트리**

1. 모든 노드는 빨강 또는 검정
2. 루트는 검정
3. 모든 NIL 노드는 검정
4. 빨강 노드의 자식은 검정 (빨강 연속 불가)
5. 어떤 노드에서 NIL까지 가는 모든 경로의 검정 노드 수는 같음

→ 가장 긴 경로가 가장 짧은 경로의 2배를 넘지 않는 **느슨한 균형**입니다.

- **삽입**: 새 노드는 빨강으로 넣고, 부모도 빨강이면 **삼촌**의 색을 봅니다.
  - 삼촌이 빨강 → **Recoloring**: 부모·삼촌을 검정, 조부모를 빨강으로 바꾸고 위로 반복
  - 삼촌이 검정 → **Restructuring**: 회전 후 종료 (최대 2번)
- **삭제**: 검정 노드를 지우면 그 경로의 검정이 1개 모자란 **Double Black**이 생기고, **형제**를 보고 해결합니다.

| 상황 | 처리 |
| :--- | :--- |
| 형제 검정 + 먼 조카 빨강 | 부모 기준 회전 + 색 정리 → 끝 |
| 형제 검정 + 가까운 조카만 빨강 | 형제 기준 회전 → 위 경우로 |
| 형제 검정 + 조카 모두 검정 | 형제를 빨강으로 바꾸고 부족분을 부모로 넘김 |
| 형제 빨강 | 부모·형제 색 교환 후 회전 → 형제가 검정인 경우로 |

> 💡 **"형제에게 빌릴 빨강이 있으면 회전, 없으면 위로 넘긴다."** 삭제 회전은 최대 3번입니다.

**자식이 2개인 노드 삭제 (AVL·RB 공통)**

- 바로 지우지 않고 **중위 후속자**(오른쪽 서브트리의 최솟값)로 값을 교체한 뒤, 후속자 노드를 대신 지웁니다.
- 후속자는 왼쪽 자식이 없어서 항상 자식이 0~1개입니다. 그래서 균형 복구는 실제로 지워진 후속자 자리에서 시작합니다.

**AVL vs Red-Black**

| 구분 | AVL | Red-Black |
| :---: | :--- | :--- |
| 균형 기준 | 서브트리 높이 차 | 색 규칙 |
| 균형 정도 | 엄격 | 느슨 |
| 탐색 | 더 빠른 편 | 약간 느릴 수 있음 |
| 삽입 회전 | 최대 1번 (이중 포함) | 최대 2번 |
| 삭제 회전 | 최대 O(log N)번 | 최대 3번 |
| 추가 정보 | 높이(BF) | 색 1비트 |
| 시간 복잡도 | 탐색·삽입·삭제 O(log N) | 탐색·삽입·삭제 O(log N) |

**실무 연결**

- **Java TreeMap**: Red-Black 트리입니다. `deleteEntry()`가 후속자 교체 → 실제 삭제 → `fixAfterDeletion()` 순서로 동작하고, `ceilingKey()`도 후속자 찾기와 같은 원리입니다.
- **DB 인덱스(B+트리)**: 페이지가 비면 형제에게서 빌리거나 병합 후 부모로 넘깁니다. RB 삭제와 비슷한 발상이고, 대량 DELETE를 나눠 실행하거나 소프트 삭제(`deleted_at`)를 쓰는 이유 중 하나입니다.
- **리눅스 CPU 스케줄러**: 가장 왼쪽(가장 덜 실행된) 프로세스를 꺼내 실행합니다. 삽입·삭제가 매우 잦아 회전이 적은 RB가 유리합니다.

---

#### 🌐 NW: TCP vs UDP / Handshake / TCP 제어 / 포트 포워딩

**TCP vs UDP**

- IP는 "어느 컴퓨터로", 포트는 "그 컴퓨터의 어느 프로그램으로"를 정합니다. 연결 하나는 (출발지 IP, 출발지 포트, 목적지 IP, 목적지 포트, 프로토콜) 5개 값으로 구분합니다.

| 구분 | TCP | UDP |
| :---: | :--- | :--- |
| 연결 | 연결 지향 (3-way handshake 후 전송) | 비연결 |
| 신뢰성 | 재전송·순서 보장·중복 제거 | 보장 안 함 |
| 제어 | 흐름·혼잡·오류 제어 | 없음 |
| 데이터 경계 | 바이트 스트림 | 데이터그램 단위 |
| 헤더 | 20~60바이트 | 8바이트 |
| 사용처 | 웹(HTTP/1.1·2), SSH, 이메일, DB | DNS, 게임, 음성·영상 통화, DHCP, QUIC |

**3-way Handshake (연결)**

- `SYN(seq=x)` → `SYN+ACK(seq=y, ack=x+1)` → `ACK(ack=y+1)`
- 서로의 준비 상태와 초기 순서 번호(ISN)를 확인합니다. ISN은 이전 연결 패킷과 섞이거나 예측당하지 않도록 무작위로 정합니다.
- **2번이 아닌 이유**: 서버는 자기 번호가 클라이언트에 닿았는지 확신할 수 없고, 늦게 도착한 옛 SYN에 속아 연결을 열 수 있습니다.
- 전화 비유: "연결할래요?" → "좋아요, 저도 준비됐어요" → "확인했어요!"

**4-way Handshake (종료)**

- `FIN` → `ACK` → (남은 데이터 전송) → `FIN` → `ACK`
- TCP는 양방향을 각각 닫습니다. FIN을 받은 쪽은 아직 보낼 데이터가 있을 수 있어 ACK와 FIN을 합치지 못합니다(Half-Close).
- **CLOSE_WAIT**가 서버에 잔뜩 쌓였다면 코드에서 소켓을 안 닫은 버그일 가능성이 큽니다.
- **TIME_WAIT**: 먼저 끊은 쪽이 2MSL 동안 기다립니다. ① 마지막 ACK가 유실되면 상대가 FIN을 다시 보내기 때문이고, ② 늦게 온 옛 패킷이 새 연결에 섞이는 것을 막기 위해서입니다.
- 실무: 짧은 연결을 대량으로 맺고 끊으면 TIME_WAIT 소켓이 쌓여 포트가 부족해집니다 → Keep-Alive, 커넥션 풀로 재사용합니다.

**TCP 제어 기법**

| 제어 | 지키는 대상 | 방법 |
| :---: | :---: | :--- |
| 흐름 제어 | 수신자 | 슬라이딩 윈도우, rwnd(수신 윈도우). rwnd = 0이면 전송 중단 후 Zero Window Probe |
| 혼잡 제어 | 네트워크 | cwnd(혼잡 윈도우). Slow Start(지수 증가) → 임계치 이후 AIMD(선형 증가, 손실 시 절반). 3 Duplicate ACK → Fast Retransmit/Recovery |
| 오류 제어 | 데이터 | 체크섬, ACK, 타임아웃·중복 ACK 시 재전송 |

> 💡 송신자가 한 번에 보낼 수 있는 양은 `min(rwnd, cwnd)`입니다.

**포트 포워딩**

- **공유기(라우터)의 NAT**에서 일어납니다. 외부에서 `공인 IP:포트`로 들어온 요청을 미리 정한 규칙에 따라 `내부 사설 IP:포트`로 바꿔 전달합니다(DNAT).
- IP(3계층)와 포트(4계층)를 함께 다루므로 **L3~L4 동작**입니다.
- 여러 기기가 공인 IP 하나를 쓸 때는 포트까지 변환하는 **NAPT**와 변환 테이블을 씁니다.

```plaintext
[외부 사용자] → 203.0.113.5:8080
      ↓
[공유기 NAT] 규칙: 외부 8080 → 192.168.0.10:80
      ↓
[내부 서버 192.168.0.10:80]
```

| 구분 | 일반 NAT (NAPT) | 포트 포워딩 |
| :---: | :--- | :--- |
| 방향 | 내부 → 외부 | 외부 → 내부 |
| 규칙 | 나갈 때 자동 생성 | 관리자가 미리 설정 |
| 예시 | 집 PC로 웹 서핑 | 집 서버를 외부에 공개 |

- 생각해볼 질문: ngrok은 공유기 설정 없이 어떻게 로컬 서버를 외부에 공개할까? 포트가 고갈되면 어떻게 될까?

</details>

### ✅ 4회차 (11/12) 요약

<details>
<summary>펼쳐서 보기</summary>

**📂 발표 자료**

| 파트 | 발표자 | 자료 |
| :---: | :---: | :--- |
| DS | 권혜강, 윤형섭, 조수연 | [Heap & Priority Queue Hash Table[권혜강].pdf](./DataStructure/Day4/CS%20스터디%204회차%20—%20Heap%20&%20Priority%20Queue%20Hash%20Table[권혜강].pdf)<br>[Heap & Priority Queue Hash Table[조수연].pdf](./DataStructure/Day4/CS%20스터디%204회차%20—%20Heap%20&%20Priority%20Queue%20Hash%20Table[조수연].pdf) |
| NW | 김영웅, 최나현, 최묘석, 최승우 | [HTTP_vs_HTTPS_TLS_Handshake_최묘석.md](./Network/Day4/HTTP_vs_HTTPS_TLS_Handshake_최묘석/HTTP_vs_HTTPS_TLS_Handshake_최묘석.md)<br>[HTTP_HTTPS_발표자료.pdf](./Network/Day4/HTTP_HTTPS_발표자료.pdf) ([정리](./Network/Day4/권혜강_HTTP_HTTPS.md))<br>[SSL TLS 핸드셰이크_최승우.pdf](./Network/Day4/SSL%20TLS%20핸드셰이크_최승우.pdf) ([정리](./Network/Day4/권혜강_SSL_TLS.md)) |

---

#### ⛰️ DS: Heap & Priority Queue / Hash Table

**우선순위 큐와 힙**

- 우선순위 큐는 "우선순위가 높은 것부터 꺼낸다"는 **추상 자료형(ADT)**이고, 힙은 이를 **구현하는 자료구조**입니다.
- 정렬 안 된 배열·정렬된 배열·연결 리스트는 삽입이나 삭제 중 하나가 O(N)이지만, 힙은 둘 다 O(log N)이라 삽입·삭제가 섞일 때 가장 유리합니다.

| 구현 방법 | 삽입 | 삭제 | 조회(peek) |
| :--- | :---: | :---: | :---: |
| 정렬 안 된 배열 | O(1) | O(N) | O(N) |
| 정렬된 배열 / 연결 리스트 | O(N) | O(1) | O(1) |
| 힙 | O(log N) | O(log N) | O(1) |

- **힙 = 완전 이진 트리 + 힙 속성**. 최대 힙은 부모 ≥ 자식, 최소 힙은 부모 ≤ 자식입니다. 형제끼리는 순서가 없어서 **반정렬** 구조입니다.
- 완전 이진 트리라서 배열에 저장합니다. 0번부터 쓰면 부모 `(i-1)//2`, 왼쪽 자식 `2i+1`, 오른쪽 자식 `2i+2`입니다.
- **삽입(sift-up)**: 맨 끝에 넣고 부모와 비교하며 올립니다. **삭제(sift-down)**: 루트를 꺼내고 마지막 원소를 루트로 옮긴 뒤 더 큰(작은) 자식과 교환하며 내립니다. 둘 다 높이만큼이라 O(log N)입니다.
- **Heapify**: 마지막 내부 노드부터 거꾸로 sift-down 하면 O(N)에 힙을 만듭니다. **힙 정렬**은 O(N log N), 추가 메모리 O(1), 불안정 정렬입니다.
- Python `heapq`는 최소 힙입니다. 최대 힙은 음수로 넣고 꺼낼 때 부호를 바꾸고, `(우선순위, 값)` 튜플로 우선순위 큐를 만듭니다.

**해시 테이블**

- 키 → 해시 함수 → 인덱스(버킷)로 바로 찾아가서 검색·삽입·삭제가 **평균 O(1)**입니다. (Python `dict`/`set`, Java `HashMap`)
- **해시 충돌**은 비둘기집 원리상 피할 수 없고, 핵심은 처리 방법입니다.

| 해결법 | 방식 | 특징 |
| :---: | :--- | :--- |
| 체이닝 | 같은 버킷에 연결 리스트로 이어 붙임 | 구현 단순, 한 버킷에 몰리면 O(N) |
| 개방 주소법 | 테이블 안의 다른 빈칸을 찾음 | 선형 탐사(1차 군집) · 이차 탐사 · 이중 해싱(군집 최소) |

- Java 8+ `HashMap`은 한 버킷이 8개 이상이고 테이블이 64칸 이상이면 리스트를 **Red-Black 트리**로 바꿔 최악을 O(log N)으로 줄입니다. (3회차와 연결)

| 연산 | Heap | Hash Table |
| :---: | :---: | :---: |
| 추가 | O(log N) | 평균 O(1) |
| 삭제 | 루트 O(log N) | 키로 평균 O(1) |
| 특정 값 찾기 | O(N) | 키로 평균 O(1) |
| 최솟값 확인 | 최소 힙 O(1) | O(N) |

---

#### 🔒 NW: HTTP vs HTTPS / SSL·TLS 핸드셰이크

**HTTP vs HTTPS**

- HTTP는 평문이라 공유기·통신사 장비를 거치는 동안 **도청 · 변조 · 사칭**에 노출됩니다. ("HTTP는 엽서")
- HTTPS = **HTTP + TLS**. TLS는 TCP 위, HTTP 아래에서 포장을 대신 해 줍니다.

| 구분 | HTTP | HTTPS |
| :---: | :--- | :--- |
| 전송 내용 | 평문 | TLS로 암호화 |
| 서버 확인 | 제공 안 함 | 인증서로 도메인 확인 |
| 변조 확인 | 제공 안 함 | 무결성 검증 |
| 기본 포트 | 80 | 443 |

- TLS가 주는 세 가지: **기밀성**(암호화), **무결성**(변조 감지), **인증**(인증서 + 디지털 서명)

**대칭키 + 비대칭키를 섞어 쓰는 이유**

- 대칭키는 빠르지만 열쇠를 건네기 어렵고, 비대칭키는 열쇠를 건넬 필요가 없지만 느립니다.
- → **느리지만 안전한 방법으로 열쇠만 정하고, 실제 대화는 빠른 대칭키로** 합니다. 이 과정이 TLS 핸드셰이크입니다.

**인증서와 신뢰 체인**

- 인증서 = 서버의 신분증 (도메인, 서버 공개키, CA 서명, 유효기간). CA가 인증서를 통째로 암호화하는 게 아니라 **디지털 서명**합니다.
- 신뢰 체인: `루트 CA`(OS·브라우저에 내장) → `중간 CA` → `서버 인증서`
- 자물쇠는 도메인 신원만 확인할 뿐, 사이트 운영자의 신뢰성까지 보증하지 않습니다. 피싱 사이트도 HTTPS를 쓸 수 있습니다.

**TLS 1.3 핸드셰이크 (1-RTT)**

1. TCP 3-way handshake 완료
2. ① **ClientHello**: 지원 암호 목록 · 랜덤값 · 키 재료(임시 공개 키)
3. ② **ServerHello**: 고른 암호 · 랜덤값 · 서버 키 재료 → **양쪽이 각자 같은 세션 키 계산**
4. ③ 서버 **인증서 · 서명 · Finished** (여기부터 암호화)
5. ④ 클라이언트 **Finished** → ⑤ 암호화된 HTTP 데이터

- **물감 섞기(Diffie-Hellman)**: 공통 색 + 각자 비밀 색을 섞은 결과만 교환하고, 받은 색에 내 비밀 색을 섞으면 양쪽이 같은 색(세션 키)을 얻습니다. **세션 키는 네트워크로 전송되지 않습니다.**
- TLS 1.2의 RSA 키 교환은 클라이언트가 Pre-Master Secret을 서버 공개키로 암호화해서 보냈지만, TLS 1.3은 이를 없애고 (EC)DHE만 씁니다.
- TCP 3-way handshake는 **연결 수립**, TLS 핸드셰이크는 그 위에서 **보안 통신 준비**로 목적이 다릅니다.

> 💡 인증서 확인을 건너뛰면 공격자가 서버인 척 키 재료를 보내는 **중간자 공격(MITM)**이 가능해집니다.

</details>

### ✅ 5회차 (11/17) 요약

<details>
<summary>펼쳐서 보기</summary>

**📂 발표 자료**

| 파트 | 발표자 | 자료 |
| :---: | :---: | :--- |
| DS | 권혜강, 윤형섭, 최승우, 최나현 | [Graph 기본 & DFS BFS_권혜강.pdf](./DataStructure/Day5/Graph%20기본%20&%20DFS%20BFS_권혜강.pdf)<br>[Graph 기본 & DFS BFS_윤형섭.pdf](./DataStructure/Day5/Graph%20기본%20&%20DFS%20BFS_윤형섭.pdf)<br>[그래프 표현법 & 탐색 (DFS·BFS)_최승우.pdf](./DataStructure/Day5/그래프%20표현법%20&%20탐색%20(DFS·BFS)_최승우.pdf)<br>[Graph_표현법과_DFS_BFS_발표_최나현.pdf](./DataStructure/Day5/Graph_표현법과_DFS_BFS_발표_최나현.pdf) |
| NW | 김영웅, 조수연, 최묘석 | [HTMP버전별 진화_최묘석.md](./Network/Day5/HTMP버전별%20진화_최묘석.md)<br>[HTTP_versions_조수연.pdf](./Network/Day5/HTTP_versions_조수연.pdf)<br>[HTTP_버전_비교_핵심편.pdf](./Network/Day5/HTTP_버전_비교_핵심편.pdf) ([pptx](./Network/Day5/HTTP_버전_비교_핵심편.pptx)) |

> 📝 회고 전문: [Network/Day5/5회차회고.md](./Network/Day5/5회차회고.md)

---

#### 🕸️ DS: Graph 기본 & DFS / BFS

**왜 알아야 하나**

- 지도 길찾기, 친구 추천(거리 2인 사람), 웹 크롤러, 패키지·마이그레이션 의존성 순서가 모두 그래프 탐색입니다.
- 핵심은 **문제를 그래프로 바꾸는 눈**입니다. 정점과 간선만 정하면 나머지는 DFS / BFS 템플릿이 풉니다.

| 문제 | 정점 | 간선 | 탐색 |
| :--- | :--- | :--- | :---: |
| 미로 탈출 최소 이동 | 칸 | 상하좌우로 붙은 칸 | BFS |
| 친구 추천 | 사람 | 친구 관계 | BFS |
| 순환 참조 검사 | 모듈 | A가 B를 import | DFS |
| 섬의 개수 | 땅 칸 | 붙어 있는 땅 | DFS / BFS |

**표현법**

| 구분 | 인접 행렬 | 인접 리스트 |
| :---: | :---: | :---: |
| 공간 | O(V²) | O(V + E) |
| u–v 연결 확인 | O(1) | O(deg(u)) |
| DFS / BFS 전체 | O(V²) | O(V + E) |
| 이럴 때 | 정점이 적고 간선이 빽빽할 때 | 간선이 듬성듬성한 대부분의 실제 그래프 |

- 정점 10만 개면 행렬은 100억 칸(약 40GB)이라 실전은 대부분 인접 리스트입니다.
- 대규모 그래프 라이브러리는 연속 배열 2개에 담는 **CSR** 포맷으로 인접 리스트의 캐시 미스를 줄입니다.

**DFS vs BFS**

| 구분 | DFS | BFS |
| :---: | :--- | :--- |
| 자료구조 | 스택 (재귀) | 큐 (deque) |
| 방문 순서 | 한 경로를 끝까지 → 되돌아옴 | 가까운 곳부터 (거리 순) |
| 최단 거리 (무가중치) | 보장 안 됨 | 보장 (처음 도착 = 최단) |
| 추가 메모리 | 최대 깊이만큼 | 최대 너비만큼 |
| 시간 | O(V + E) | O(V + E) |
| 잘 맞는 문제 | 백트래킹, 사이클 찾기 | 최단 거리, 최소 이동 횟수 |

> 💡 **차이는 꺼내는 자료구조 하나: 스택이냐 큐냐.** "최소·최단"이 보이면 BFS, "모든 경우"가 보이면 DFS.

**구현 함정**

- 재귀 DFS는 깊이가 최악 V라 파이썬 기본 한도(1,000)를 넘을 수 있습니다 → `sys.setrecursionlimit` 또는 명시적 스택.
- BFS는 **큐에 넣을 때** 방문 표시해야 같은 정점이 두 번 들어가지 않습니다.
- `list.pop(0)`은 O(N), `deque.popleft()`는 O(1)입니다.

**실무 연결**

- OS 데드락 탐지(Wait-For Graph의 사이클), GC Mark & Sweep(루트에서 도달 가능한 객체만 생존), Git 커밋 히스토리·빌드 의존성(DAG), 네트워크 STP(스패닝 트리로 루프 방지)

---

#### ⚡ NW: HTTP 1.1 vs 2.0 vs 3.0

| 버전 | 핵심 기술 | 개선하려는 문제 |
| :---: | :--- | :--- |
| HTTP/1.1 | 지속 연결(Keep-Alive), 파이프라이닝 | 요청마다 TCP 연결을 새로 맺는 비용 |
| HTTP/2 | 다중화, 이진 프레이밍, HPACK, 서버 푸시 | 응답 순서 대기, 중복 헤더 |
| HTTP/3 | QUIC(UDP 기반), 독립 스트림, TLS 1.3 통합 | TCP 수준 HOL Blocking, 연결 설정 지연 |

- **HTTP/1.1**: 연결을 재사용하지만 응답이 순서대로 와야 해서, 앞 응답이 늦으면 뒤가 막히는 **HOL Blocking**이 생깁니다.
- **HTTP/2**: 메시지를 프레임으로 쪼개 Stream ID로 구분하고, 하나의 연결에서 섞어 보냅니다(다중화). 헤더는 HPACK으로 압축합니다.
- **HTTP/2에도 남는 문제**: TCP는 바이트 순서를 지켜야 해서 패킷 하나가 손실되면 **모든 스트림이 재전송을 기다립니다.**
- **HTTP/3**: UDP 위의 QUIC이 스트림별로 독립 전송해, 한 스트림의 손실이 다른 스트림을 막지 않습니다. TLS 1.3을 통합해 연결 설정이 빠릅니다.

| 비교 | HTTP/1.1 | HTTP/2 | HTTP/3 |
| :---: | :---: | :---: | :---: |
| 전송 기반 | TCP | TCP | UDP 기반 QUIC |
| 다중화 | 미지원 | 지원 | 지원 |
| 메시지 | 텍스트 | 이진 프레임 | QUIC 스트림 프레임 |
| 헤더 압축 | 없음 | HPACK | QPACK |
| HOL Blocking | 응답 순서 문제 | TCP 수준에서 발생 | 스트림 간 해결 |

> 💡 3회차(TCP vs UDP) → 4회차(TLS) → 5회차(HTTP 버전)가 한 줄로 이어집니다. HTTP/3은 "TCP를 고칠 수 없으니 UDP 위에 필요한 신뢰성만 직접 만든" 결과입니다.

</details>

### 🔜 6회차 준비 사항

> 📍 **11/20 (금) 19:00 · 최묘석 집**

| 구분 | 대상 | 할 일 | 마감 |
| :---: | :---: | :--- | :---: |
| **DS 발표** | 권혜강, 최나현, 김영웅 | **최단 경로 알고리즘 / MST** 정리 후 `DataStructure/Day6/` 폴더에 PR | 모임 시작 전 |
| **NW 발표** | 최묘석, 윤형섭, 최승우, 조수연 | **DNS 동작 원리 / 브라우저에 URL 입력 시 흐름** 정리 후 `Network/Day6/` 폴더에 PR | 모임 시작 전 |
| **이슈란 작성** | 전원 | 질문 답변 채우기. 아래 [이슈란 작성 안내](#-이슈란-작성-안내) 참고 | 6회차 시작 전 |
| **서기** | 미정 | 모임 기록 | 모임 당일 |

> 🗒️ 질문 Issue 템플릿: [Topics/expected-questions-issue-template.md](./Topics/expected-questions-issue-template.md)  
> 🗒️ 전체 스케줄과 역할 상세: [Topics/README.md](./Topics/README.md)

#### 📖 6회차 토픽 미리보기

**DS: 최단 경로 알고리즘 / MST**

- 5회차 BFS는 간선 비용이 모두 같을 때만 최단 거리를 보장합니다. 비용이 다르면 아래 알고리즘이 필요합니다.

| 알고리즘 | 용도 | 특징 | 시간 복잡도 |
| :---: | :--- | :--- | :---: |
| Dijkstra | 한 시작점 → 모든 정점 | 음수 간선 불가, 우선순위 큐(4회차 Heap) | O(E log V) |
| Bellman-Ford | 한 시작점 → 모든 정점 | 음수 간선 허용, 음수 사이클 탐지 | O(VE) |
| Floyd-Warshall | 모든 정점 쌍 | DP, 구현 단순 | O(V³) |

- **MST(최소 신장 트리)**: 모든 정점을 사이클 없이 V-1개 간선으로 잇되 가중치 합이 최소인 트리. **Kruskal**(간선 정렬 + Union-Find), **Prim**(한 정점에서 시작해 우선순위 큐로 확장)
- 생각해볼 질문: 다익스트라는 왜 음수 간선에서 틀릴까? Kruskal과 Prim은 각각 언제 유리할까?

**NW: DNS 동작 원리 / 브라우저에 URL 입력 시 흐름**

- DNS 조회 순서: 브라우저 캐시 → OS(hosts) → Local DNS 서버 → Root → TLD(.com) → Authoritative
- URL 입력 후 화면까지: DNS로 IP 획득 → TCP 연결(3회차) → TLS(4회차) → HTTP 요청·응답(5회차) → 렌더링
- 지금까지 배운 네트워크 내용을 한 흐름으로 묶는 회차입니다. (2회차 전체 흐름 개요와 연결)
- 생각해볼 질문: DNS는 왜 주로 UDP를 쓸까? 재귀 쿼리와 반복 쿼리는 어떻게 다를까?

### 📝 이슈란 작성 안내

지금 이슈에는 질문만 있고 **답변이 비어 있습니다.** 아래 순서로 각자 채워 주세요.

1. **내가 올린 질문의 답변 채우기**
2. **함께 보면 좋을 것들**: 도움이 된 블로그, 영상, 문서 링크 등
3. **질문에 대해 내가 생각하고 답해본 것들**: 모범 답안이 아니어도 괜찮고, 틀린 부분은 같이 고치면 공부가 됩니다.
4. 다른 사람의 질문에 의견을 남겨도 좋습니다.

> 길이나 형식은 자유롭게 적어 주세요.

---

## 🎯 스터디 운영 방식

### 1. 모임 일정 및 장소
- **주기**: 주 2회 
- **시간**: 일과 종료 후 (18:30 \~ 19:30 투표로 세부 조정 가능)
- **장소**: 근처 카페 (오프라인 모임) / 점심 시간 이용해 회의실 이용
- **진행 방식**:
  1. **사전 준비**: 모임 전날까지 본인 담당 주제 정리 마크다운 작성 후 PR 제출
     - 회차별 마감이 따로 공지되면 공지된 시간(예: 2회차 11/6 18:00)을 따릅니다.
     - 발표 외 주제는 **Issue**로 예상 질문을 모읍니다 (회차별 공지, 1인 2개).
  2. **오프라인 발표 (약 50\~60분)**:
     - 1인당 약 5\~10분 발표 + 5분 질의응답 (회당 3\~4명씩 순환 발표)
     - 다른 스터디원은 적극적으로 꼬리 질문 및 피드백 제시
  3. **회고 및 피드백 (약 10분)**:
     - 다음 회차 주제 확인 및 발표자 선정
     - PR 상호 코드 리뷰 및 승인(Approve) 후 Merge
  4. **역할**: 발표자 / 청중(질문·보충) / **서기**(모임 기록, 회차별 공지에 따라 조정)

### 2. 학습 로드맵
- **1단계**: [자료구조 (Data Structure)](./DataStructure/) & [네트워크 (Network)](./Network/) 병행 학습
- **참고 자료**:
  - [gyoogle 기술 면접 인터뷰 가이드](https://github.com/gyoogle/tech-interview-for-developer)
  - [Topics/ 주제 가이드 및 커리큘럼](./Topics/)

---

## 📂 저장소 디렉토리 구조

```plaintext
CS-Study/
├── .github/
│   ├── workflows/
│   │   └── auto-merge.yml            # 🤖 PR 자동 머지 GitHub Actions 봇
│   ├── ISSUE_TEMPLATE/
│   │   └── expected-questions.md     # 회차별 DS 예상 질문 Issue 템플릿
│   └── pull_request_template.md      # PR 생성 템플릿
├── DataStructure/                    # 자료구조 발표 아카이빙
│   ├── README.md                     # 자료구조 커리큘럼 및 체크리스트
│   └── Day[N](MMDD)/                 # 회차별 폴더 (예: Day1(1104))
│       └── [주제명]_[이름].md          # 개인별 정리 문서
├── Network/                          # 네트워킹 발표 아카이빙
│   ├── README.md                     # 네트워크 커리큘럼 및 체크리스트
│   └── Day[N](MMDD)/                 # 회차별 폴더 (예: Day2(1106))
│       └── [주제명]_[이름].md          # 개인별 정리 문서
├── Topics/                           # 전체 학습 주제 요약 및 발표 템플릿
│   ├── README.md                     # 토픽 한눈에 보기
│   ├── DataStructure-Curriculum.md   # 자료구조 핵심 키워드/질문 리스트
│   ├── Network-Curriculum.md         # 네트워크 핵심 키워드/질문 리스트
│   └── template.md                   # 스터디 발표 정리 마크다운 템플릿
└── README.md                         # 스터디 소개 및 룰북
```

---

## 🚀 Git & GitHub 협업 규칙 (Fork & PR 방식)

### 1. 작업 및 브랜치 흐름 (Fork Workflow)
1. 본 메인 저장소(`upstream`)를 각자의 GitHub 계정으로 **Fork**합니다.
2. Fork한 저장소를 로컬 PC로 `git clone` 합니다.
3. 새로운 브랜치를 생성하여 작업합니다.
   - 브랜치 네이밍: `[카테고리]/[주제명]-[이름]`
   - 예시: `network/tcp-udp-hong`, `datastructure/hash-table-kim`
4. 발표 자료 작성 후 Fork 저장소의 해당 브랜치로 `push` 합니다.
5. 원본 저장소(`upstream`)의 `main` 브랜치로 **Pull Request(PR)**를 생성합니다.

### 2. 파일 명명 규칙
- 각 카테고리 폴더 하위의 **회차 폴더(`Day[N](MMDD)`)** 안에 아래 형식으로 `.md` 파일을 생성합니다.
- `[주제영문or한글]_[이름].md`
  - 예: `Network/Day2(1106)/네트워크_전체_흐름_홍길동.md`
  - 예: `DataStructure/Day1(1104)/Array_LinkedList_이순신.md`

### 3. Commit Message 규칙
Angular / Gitmoji 컨벤션을 따릅니다.

| 태그 | 설명 | 예시 |
| :---: | :--- | :--- |
| `docs` | 문서 작성 및 수정 | `docs: Network TCP/UDP 핸드셰이크 정리 - 홍길동` |
| `feat` | 새로운 기능/구조 추가 | `feat: PR 템플릿 추가` |
| `refactor` | 기존 정리 내용 보완/수정 | `refactor: B-Tree 설명 보완 - 김철수` |
| `fix` | 오탈자 또는 잘못된 지식 수정 | `fix: OSI 7계층 오탈자 수정` |

### 4. Pull Request & 자동 머지 봇 (Auto-Merge Bot 🤖)
1. **PR 제목**: `[카테고리] 주제명 - 발표자 이름`
   - 예: `[Network] TCP 3-way & 4-way Handshake - 홍길동`
2. **PR 내용**: [PR 템플릿](./.github/pull_request_template.md) 양식을 준수하여 작성
3. **자동 머지(Auto-Merge)**:
   - PR이 열리면 GitHub Actions **Auto Merge Bot**이 안내 댓글을 남기고 충돌이 없을 시 `main` 브랜치로 **자동 머지**를 수행합니다.
   - 발표 후 오프라인 카페 모임에서 나눈 질문/답변이나 피드백은 머지된 후에도 자유롭게 추가 커밋 및 코멘트로 남길 수 있습니다.

---

## ⚖️ 스터디 페널티 (벌금 / 리워드)

스터디의 지속성과 책임감을 위해 가벼운 패널티 제도를 권장합니다 (투표로 금액 확정 가능).

| 구분 | 조건 | 패널티 |
| :---: | :--- | :---: |
| **지각** | 모임 시작 시간 기준 10분 이상 지각 시 | 1,000원 |
| **당일 노쇼** | 사전 연락 없이 불참 시 | 3,000원 |
| **PR 미제출** | 모임 당일 시작 전까지 PR 미작성 시 | 2,000원 |

> 💡 모인 벌금은 스터디 종료 후 회식비로 활용합니다!