# 🌐 네트워크 학습 주제별 요약 및 핵심 질문 가이드

> 참고: [gyoogle tech-interview-for-developer - Network](https://github.com/gyoogle/tech-interview-for-developer#network)

---

### 0. 네트워크 전체 흐름 (2회차 · 11/6)

> 📌 정해진 토픽 목록과 별개로, **클라이언트 요청이 서버에 닿고 응답이 돌아오기까지의 큰 그림**을 먼저 잡는 회차입니다.
> - **발표**: 최나현, 최승우 (발표 자료 PR: `Network/Day2(1106)/`, 11/6 18:00까지)
> - **청중**: 최묘석, 조수연, 김영웅, 윤형섭 — 흐름과 앞으로 공부할 내용을 미리 훑어오고, 발표 후 질문·보충
> - **서기**: 권혜강

- **흐름 한눈에 보기 (아래 번호는 이 문서의 해당 주제와 대응)**:
  1. 주소 입력 → **DNS**로 도메인을 IP로 변환 (7번)
  2. **TCP 3-way Handshake**로 연결 수립 (3번), 필요 시 **TLS 핸드셰이크** (5번)
  3. **HTTP** 요청 전송 (5, 6번) — 계층별 **캡슐화** (1번)
  4. 서버 처리 후 응답 → 클라이언트 렌더링, 상태 유지는 **Cookie/Session** (8번)
  5. 전송 과정의 안정성은 **TCP 흐름/혼잡/오류 제어** (4번), 신뢰성/속도 선택은 **TCP vs UDP** (2번)
- **빈출 면접 질문**:
  - Q. 브라우저에 URL을 입력하고 엔터를 쳤을 때부터 화면이 보이기까지의 과정을 설명해주세요.
  - Q. 이 과정에서 각 단계는 OSI/TCP-IP 어느 계층에서 일어나나요?

---

### 1. OSI 7 계층 & TCP/IP 4 계층
- **핵심 요약**:
  - OSI 7계층: 물리 → 데이터링크 → 네트워크 → 전송 → 세션 → 표현 → 응용
  - TCP/IP 4계층: 네트워크 인터페이스 → 인터넷(IP) → 전송(TCP/UDP) → 응용(HTTP, FTP 등)
  - 계층화 이유: 통신 흐름의 표준화 및 문제 발생 시 해당 계층만 독립적으로 수정/해결 가능.
- **빈출 면접 질문**:
  - Q. OSI 7 계층과 TCP/IP 4 계층의 차이는 무엇인가요?
  - Q. 각 계층별 대표적인 프로토콜과 전송 단위(PDU)는 무엇인가요?

---

### 2. TCP vs UDP
- **핵심 요약**:
  - **TCP**: 연결 지향(Connection-oriented), 3-way handshake로 연결 수립, 신뢰성 보장(패킷 재전송, 순서 보장, 흐름/혼잡 제어), 속도는 상대적으로 느림.
  - **UDP**: 비연결 지향, 신뢰성을 보장하지 않음, 헤더가 단순하여 오버헤드가 적고 전송 속도가 빠름(스트리밍, 실시간 게임, DNS 등).
- **빈출 면접 질문**:
  - Q. TCP와 UDP의 특징과 사용처 차이를 설명해주세요.
  - Q. UDP는 왜 신뢰성을 보장하지 않는데도 여전히 많이 쓰이나요?

---

### 3. TCP Handshake (3-way & 4-way)
- **핵심 요약**:
  - **3-way Handshake (연결 수립)**: Client(SYN) → Server(SYN+ACK) → Client(ACK)
  - **4-way Handshake (연결 종료)**: Client(FIN) → Server(ACK) → Server(FIN) → Client(ACK) (이후 TIME_WAIT 상태 유지)
- **빈출 면접 질문**:
  - Q. 왜 연결 수립은 3-way인데 연결 해제는 4-way인가요?
  - Q. TIME_WAIT 상태가 필요한 이유는 무엇인가요?

---

### 4. TCP 흐름 제어 / 혼잡 제어 / 오류 제어
- **핵심 요약**:
  - **흐름 제어**: 송신 측과 수신 측의 처리 속도 차이를 조절 (Stop and Wait, Sliding Window).
  - **혼잡 제어**: 네트워크 내의 패킷 수가 넘쳐 혼잡해지는 것을 방지 (AIMD, Slow Start, 혼잡 회피, 빠른 회복).
  - **오류 제어**: 손실되거나 훼손된 패킷을 재전송 (Go-Back-N, Selective Repeat).
- **빈출 면접 질문**:
  - Q. 슬라이딩 윈도우(Sliding Window)의 동작 원리를 설명해주세요.
  - Q. Slow Start와 AIMD 방식의 차이는 무엇인가요?

---

### 5. HTTP vs HTTPS & SSL/TLS
- **핵심 요약**:
  - **HTTP**: 평문(Plaintext) 통신으로 도청 및 변조 위험 존재 (기본 포트 80).
  - **HTTPS**: HTTP에 SSL/TLS 암호화 계층을 추가 (기본 포트 443). 대칭키(데이터 암호화)와 비대칭키(대칭키 교환 및 인증서 검증) 방식을 혼합 사용.
- **빈출 면접 질문**:
  - Q. HTTPS의 암호화 핸드셰이크 과정(대칭키, 공개키)을 설명해주세요.
  - Q. CA(인증기관)의 역할과 인증서의 검증 방식은 무엇인가요?

---

### 6. HTTP 버전별 진화 (HTTP 1.1 / 2.0 / 3.0)
- **핵심 요약**:
  - **HTTP 1.1**: Keep-Alive(지속 연결), 파이프라이닝 도입. 하지만 HOL Blocking(Head-Of-Line Blocking) 문제 존재.
  - **HTTP 2.0**: 하나의 TCP 연결에서 여러 요청을 동시에 처리하는 Multiplexing, Header 압축(HPACK), Server Push 지원.
  - **HTTP 3.0**: TCP 대신 UDP 기반의 **QUIC** 프로토콜 도입. 연결 설정 지연 단축 및 패킷 손실 시 HOLB 완전 해결.
- **빈출 면접 질문**:
  - Q. HTTP 1.1의 한계와 HTTP 2.0의 Multiplexing에 대해 설명해주세요.
  - Q. HTTP 3.0이 TCP가 아닌 UDP를 채택한 이유는 무엇인가요?

---

### 7. DNS 동작 과정 & 웹 브라우저 URL 입력 시 흐름
- **핵심 요약**:
  1. 브라우저 캐시 / OS Hosts / Local DNS 서버 조회
  2. Root DNS → TLD DNS (.com 등) → Authoritative DNS 순차적 재귀 쿼리 수행
  3. IP 획득 후 TCP 3-way Handshake 진행
  4. HTTP/HTTPS 요청 및 응답 수신
  5. 브라우저 렌더링 (DOM/CSSOM 파싱 → 렌더 트리 구축 → Layout → Paint)
- **빈출 면접 질문**:
  - Q. 주소창에 `www.google.com`을 입력하고 엔터를 쳤을 때 일어나는 전체 과정을 설명해주세요.

---

### 8. Cookie, Session, Web Storage
- **핵심 요약**:
  - **Cookie**: 클라이언트(브라우저)에 저장되는 키-값 쌍의 작은 텍스트 파일. 매 요청마다 헤더에 자동 포함.
  - **Session**: 서버 메모리/DB에 상태를 저장하고, 클라이언트에는 Session ID만 쿠키로 전달. 보안성은 높으나 서버 부하.
  - **Web Storage**: HTML5에서 도입. `LocalStorage`(영구 저장)와 `SessionStorage`(탭 종료 시 삭제). 네트워크 요청 시 자동 전송되지 않음.
- **빈출 면접 질문**:
  - Q. 쿠키와 세션의 차이 및 각각의 장단점은?
  - Q. JWT와 세션 기반 인증의 차이점은?
