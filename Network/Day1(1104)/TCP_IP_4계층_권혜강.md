# 📑 TCP/IP 4 계층 정리

> **발표자**: 권혜강  
> **날짜**: 2026-11-04  
> **카테고리**: Network  
> **참고 링크**: [gyoogle 기술인터뷰 - Network](https://github.com/gyoogle/tech-interview-for-developer#network) · [RFC 1122 – Requirements for Internet Hosts (Communication Layers)](https://www.rfc-editor.org/rfc/rfc1122) · [Cloudflare - What is the OSI model?](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)

---

## 1. 개요 및 정의
> 이 기술/개념이 무엇이고 왜 등장했는지 간략히 서술합니다.

- 개념 정의:
  - **TCP/IP 4 계층 모델 (인터넷 프로토콜 스위트)**: 인터넷에서 실제로 사용되는 프로토콜들을 **4개 계층**으로 묶어 설명한 모델.
  - RFC 1122는 인터넷 아키텍처의 프로토콜 계층을 **Application(응용) / Transport(전송) / Internet(인터넷) / Link(링크)** 4개로 제시한다. (교재에 따라 Link 계층을 *네트워크 인터페이스(Network Interface)* 또는 *네트워크 액세스(Network Access)* 계층이라 부르기도 한다.)
  - 이름은 대표 프로토콜 **TCP**(전송)와 **IP**(인터넷)에서 유래했다.
- 등장 배경 및 해결하고자 한 문제:
  - 서로 다른 네트워크(이종 망)를 **연결(Internetworking)** 해 하나의 인터넷처럼 쓰기 위해 설계된 **실용 중심** 프로토콜 모음이다. RFC 1122도 *"The Internet is a network of networks."* 를 아키텍처 전제로 둔다.
  - OSI가 이론적 표준 모델이라면, TCP/IP는 **먼저 구현·보급되어 사실상(de facto) 표준**이 되었다. Cloudflare도 *현대 인터넷은 OSI보다 더 단순한 인터넷 프로토콜 스위트를 더 가깝게 따른다*고 설명한다.

---

## 2. 핵심 동작 원리 및 특징
> 개념의 핵심 로직, 구조, 동작 흐름을 시각 자료나 표, 불릿 포인트로 정리합니다.

### 2-1. 4계층 구조 (위 → 아래)

| 계층 (RFC 1122 명칭) | 한글 | 역할 | PDU | 대표 프로토콜 |
| :--- | :--- | :--- | :---: | :--- |
| **Application** | 응용 계층 | 사용자 앱이 쓰는 서비스·데이터 형식 규정. OSI 5·6·7 통합 | Data / Message | HTTP, HTTPS, FTP, SMTP, DNS, SSH, Telnet |
| **Transport** | 전송 계층 | **종단 간(end-to-end)** 통신. 포트로 프로세스 구분, 신뢰성(TCP) 또는 단순·빠른 전달(UDP) | Segment (TCP) / Datagram (UDP) | TCP, UDP |
| **Internet** | 인터넷 계층 | **IP 주소**로 호스트 식별, 네트워크 간 **라우팅**(출발 → 목적지 호스트 전달) | Packet (IP Datagram) | IP, ICMP, IGMP (ARP는 링크·인터넷 사이) |
| **Link** (= Network Interface / Network Access) | 링크(네트워크 인터페이스) 계층 | **직접 연결된 네트워크** 안에서 프레임 전달, MAC 주소, 물리 전송. OSI 1·2 통합 | Frame (+ Bit) | Ethernet, Wi-Fi(802.11), PPP |

#### RFC 1122가 설명하는 각 계층 (원문 근거)
- **Application**: *"The application layer is the top layer of the Internet protocol suite."* — 사용자 프로토콜로 Telnet, FTP, SMTP, 지원 프로토콜로 DNS 등을 예시.
- **Transport**: *"The transport layer provides end-to-end communication services for applications."* — 주 프로토콜은 **TCP**(*"a reliable connection-oriented transport service"*)와 **UDP**(*"a connectionless ("datagram") transport service"*).
- **Internet**: *"All Internet transport protocols use the Internet Protocol (IP) to carry data from source host to destination host."* — IP는 *"a connectionless or datagram internetwork service, providing no end-to-end delivery guarantees."* (즉 IP 자체는 **신뢰성을 보장하지 않으며**, 신뢰성은 TCP가 담당)
- **Link**: 직접 연결된 네트워크에서 통신하려면 해당 네트워크의 프로토콜을 구현해야 하며, *"We call this a link layer or media-access layer protocol."*

### 2-2. 핵심 원리
- **원리 1 – 캡슐화**: 데이터가 위에서 아래로 내려가며 계층별 헤더가 붙는다. **Data → Segment(TCP 헤더) → Packet(IP 헤더) → Frame(Ethernet 헤더·트레일러) → Bit**. 수신 측은 역순으로 헤더를 벗긴다(역캡슐화).

```text
 [ HTTP 요청 Data ]                                  ← 응용 계층
 [ TCP Header | HTTP Data ]                          ← 전송 계층  : Segment
 [ IP Header | TCP Header | HTTP Data ]              ← 인터넷 계층: Packet
 [ Eth Header | IP Header | TCP Header | Data | FCS ]← 링크 계층  : Frame → 0101… (Bit)
```

- **원리 2 – 계층별 역할 분담(End-to-End 원칙과 연결)**
  - **IP(인터넷 계층)** 는 *최선 노력(Best-Effort), 비연결형*으로 패킷을 목적지까지 **전달만** 시도한다. 손실·중복·순서 뒤바뀜을 보장하지 않는다.
  - **TCP(전송 계층)** 가 종단(양 끝 호스트)에서 **재전송·순서 보장·흐름 제어·혼잡 제어**로 신뢰성을 책임진다. → "네트워크 내부(라우터)는 단순하게, 복잡함은 끝단에서" 라는 인터넷 설계 철학.
- **원리 3 – 식별자**: 링크 = **MAC 주소**(같은 링크 내), 인터넷 = **IP 주소**(네트워크 간), 전송 = **포트 번호**(프로세스).
- **원리 4 – 엄격하지 않은 계층화**: RFC 1122는 문서 구성을 위해 계층을 쓰지만 *"strict layering is an imperfect model, both for the protocol suite and for recommended implementation approaches."* 라고 명시한다. (예: ICMP는 IP의 일부이면서 IP 위에 올라타 있고, ARP는 링크와 인터넷 사이에 걸쳐 있음)
- **원리 5 – 호스트 요구사항**: RFC 1122는 *"A host typically must implement at least one protocol from each layer."* 라고 한다. 호스트는 각 계층별로 프로토콜을 하나 이상 구현한다.

### 2-3. 비교 분석 표 (OSI 7계층 ↔ TCP/IP 4계층 매핑)

| OSI 7 계층 | TCP/IP 4 계층 | PDU | 대표 프로토콜/장비 |
| :--- | :--- | :---: | :--- |
| 7 응용 | **응용 (Application)** | Data | HTTP, FTP, SMTP, DNS |
| 6 표현 | ↑ (통합) | Data | 인코딩·암호화·압축은 앱/라이브러리가 처리 |
| 5 세션 | ↑ (통합) | Data | 세션 관리는 앱/라이브러리가 처리 |
| 4 전송 | **전송 (Transport)** | Segment / Datagram | TCP, UDP / L4 스위치 |
| 3 네트워크 | **인터넷 (Internet)** | Packet | IP, ICMP / 라우터 |
| 2 데이터링크 | **링크 (Network Interface)** | Frame | Ethernet, Wi-Fi / 스위치 |
| 1 물리 | ↑ (통합) | Bit | 케이블, 허브 |

| 구분 | OSI 7 계층 | TCP/IP 4 계층 |
| :--- | :--- | :--- |
| 성격 | 이론적 **참조 모델** (ISO/IEC 7498-1) | 실제 인터넷에서 쓰이는 **프로토콜 스위트** (RFC) |
| 계층 수 | 7 | 4 |
| 장점 | 역할이 세분화되어 **설명·장애 진단·장비 분류**에 용이 | **실제 구현과 일치**, 단순함 |
| 단점 | 실제 구현과 거리 있음, 세션/표현 계층 경계가 모호 | 링크 계층 안에 물리/데이터링크가 섞여 세부 설명엔 부족 |

> 참고: 일부 교재(예: Kurose & Ross 계열)는 TCP/IP를 **5계층(응용/전송/네트워크/링크/물리)** 으로 나눠 설명하기도 한다. 면접에서는 "**RFC 1122 기준 4계층**, 교재에 따라 링크를 링크+물리로 나눠 5계층으로도 설명한다"고 답하면 안전하다.

### 2-4. 통신 흐름 예시 (웹 요청)
1. **응용**: 브라우저가 DNS로 도메인 → IP 조회, HTTP 요청 메시지 생성
2. **전송**: TCP가 포트(예: 443)와 함께 세그먼트로 분할, 연결(3-way handshake)·재전송·흐름 제어
3. **인터넷**: IP 헤더(출발/목적 IP) 부착 → **라우터**가 IP 기준으로 홉-바이-홉 전달
4. **링크**: 다음 홉의 MAC 주소로 프레임 생성(ARP) → 전기/광/전파 신호로 전송
5. 서버에서 역순으로 올라가 HTTP 응답 생성 → 같은 과정을 거꾸로 수행

---

## 3. 실무 / 면접 핵심 포인트
> 면접관이 자주 묻는 꼬리 질문과 이에 대한 명쾌한 답변을 정리합니다.

### Q1. OSI 7 계층과 TCP/IP 4 계층의 차이는 무엇인가요?
- **A**: OSI는 ISO가 만든 **이론적 참조 모델(7계층)** 이고, TCP/IP는 인터넷에서 **실제로 쓰이는 프로토콜 스위트(4계층)** 입니다. TCP/IP는 OSI의 **세션·표현·응용(5~7)을 응용 계층 하나로**, **물리·데이터링크(1~2)를 링크 계층 하나로** 묶고, 전송(4)은 전송, 네트워크(3)는 인터넷 계층에 대응합니다. OSI는 설명·장애 분석용 공용어로, TCP/IP는 실제 구현 기준으로 쓰입니다.

### Q2. 각 계층별 대표적인 프로토콜과 전송 단위(PDU)는 무엇인가요?
- **A**: 응용 – HTTP/FTP/SMTP/DNS (Data), 전송 – TCP/UDP (Segment / Datagram), 인터넷 – IP/ICMP (Packet), 링크 – Ethernet/Wi-Fi (Frame, 물리적으로는 Bit).

### Q3. 계층화의 장점은?
- **A**: ① 각 계층이 **독립적**이라 한 계층의 구현을 바꿔도 다른 계층에 영향이 적고(예: IPv4→IPv6, 이더넷→Wi-Fi), ② 문제가 생기면 **계층별로 분리해 진단**할 수 있고, ③ 프로토콜을 **표준화**해 서로 다른 장비·OS 간 호환이 가능합니다. 단점으로는 계층마다 헤더가 붙는 **오버헤드**와, 계층 간 최적화가 어려운 점이 있습니다.

### Q4. IP는 신뢰성을 보장하지 않는데 어떻게 인터넷이 동작하나요?
- **A**: IP는 비연결형·최선 노력(Best-Effort) 전달 서비스로, RFC 1122도 *"providing no end-to-end delivery guarantees"* 라고 설명합니다. 신뢰성이 필요하면 **종단의 전송 계층(TCP)** 이 시퀀스 번호/ACK/재전송/흐름·혼잡 제어로 보장하고, 필요 없거나 직접 처리하는 앱(DNS, 스트리밍, 게임)은 **UDP**를 씁니다.

### Q5. ARP나 ICMP는 어느 계층인가요?
- **A**: **ICMP**는 IP의 일부이면서 IP 위에 올라타 동작하는 제어 프로토콜로 인터넷 계층으로 분류합니다(RFC 1122가 그렇게 설명). **ARP**는 IP 주소를 MAC 주소로 바꾸는 프로토콜로 **링크와 인터넷 계층 사이**에 걸쳐 있어 교재마다 분류가 다릅니다. 계층 분류가 딱 떨어지지 않는다는 점은 *"strict layering is an imperfect model"* 이라는 RFC의 언급과도 맞닿아 있습니다.

### Q6. 주소창에 URL을 입력했을 때 TCP/IP 4계층 관점에서 설명해보세요.
- **A**: 응용 계층에서 DNS 조회·HTTP 요청 생성 → 전송 계층에서 TCP 연결(3-way handshake)·세그먼트화 → 인터넷 계층에서 IP 헤더를 붙여 라우터가 목적지까지 라우팅 → 링크 계층에서 프레임(MAC)으로 전송. 서버는 역순으로 올라가 응답합니다. (자세한 흐름은 "웹 브라우저에 URL을 입력하면 일어나는 일" 회차에서 확장)

### Q7. (꼬리) TCP/IP를 5계층으로 설명하는 책도 있던데요?
- **A**: 링크 계층을 **데이터링크 + 물리**로 나눠 5계층(응용/전송/네트워크/데이터링크/물리)으로 설명하는 교재도 있습니다. 관점의 차이이며, RFC 1122의 원래 정의는 4계층(Application, Transport, Internet, Link)입니다.

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
| 인터넷 아키텍처 4계층(Application / Transport / Internet / Link) 정의, TCP·UDP·IP·링크 계층 설명, 호스트는 각 계층 프로토콜 구현 | [RFC 1122 §1.1.3](https://www.rfc-editor.org/rfc/rfc1122) |
| "strict layering is an imperfect model", "The Internet is a network of networks" | [RFC 1122 §1.1.2, §1.3.1](https://www.rfc-editor.org/rfc/rfc1122) |
| OSI 7계층 역할·데이터 단위·현대 인터넷은 OSI보다 인터넷 프로토콜 스위트에 가까움 | [Cloudflare Learning – What is the OSI model?](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/) |
| OSI 기본 참조 모델 표준 (구현 명세서가 아님) | [ISO/IEC 7498-1:1994](https://www.iso.org/standard/20269.html) |
| 서비스–OSI 계층 매핑 | [Cloudflare Docs – Network layers](https://developers.cloudflare.com/fundamentals/reference/network-layers) |
| 스터디 기준 자료 | [gyoogle/tech-interview-for-developer](https://github.com/gyoogle/tech-interview-for-developer) |
