# 네트워크 보안 공격, IDS/IPS, 방화벽, VPN, IPsec

## 1. 네트워크 공격 기본

네트워크 보안 공격은 크게 다음처럼 생각하면 이해하기 쉽다.

- 패킷을 몰래 본다: Sniffing
- 주소 정보를 속인다: ARP/IP Spoofing
- 경로를 속인다: ICMP Redirect
- 서버 자원을 고갈시킨다: SYN Flooding, DoS/DDoS
- 세션을 가로챈다: TCP Session Hijacking
- 이름 해석을 속인다: DNS Spoofing / Cache Poisoning

---

## 2. Sniffing

Sniffing은 네트워크에 흐르는 패킷을 몰래 수집하거나 읽는 행위다.

주로 기밀성을 침해한다.

### Promiscuous Mode

일반적인 NIC는 자신에게 온 프레임을 중심으로 처리하지만, Promiscuous Mode에서는 자신에게 직접 온 것이 아닌 프레임도 받아볼 수 있다.

패킷 분석이나 스니핑과 함께 자주 등장한다.

한 줄 정리:

`Sniffing = 패킷 엿보기`

---

## 3. ARP Spoofing

ARP는 IP 주소에 해당하는 MAC 주소를 알아내는 프로토콜이다.

공격자가 잘못된 IP-MAC 매핑 정보를 피해자에게 전달하면 다음과 같은 일이 가능하다.

```text
정상
Gateway IP → Gateway MAC

공격 후
Gateway IP → Attacker MAC
```

피해자가 게이트웨이로 보내려던 트래픽이 공격자에게 향할 수 있다.

이를 통해 MITM이나 Sniffing으로 이어질 수 있다.

한 줄 정리:

`ARP Spoofing = IP-MAC 매핑을 속여 트래픽을 공격자 쪽으로 유도`

---

## 4. IP Spoofing

IP Spoofing은 패킷의 출발지(Source) IP 주소를 위조하는 것이다.

예:

```text
실제 공격자 IP: 1.1.1.1
패킷의 Source IP: 10.0.0.5
```

활용 목적:

- 신뢰 기반 IP 정책 우회
- 실제 공격자 IP 은폐
- 반사 공격에서 응답을 피해자에게 보내기
- 일부 세션 공격의 보조 수단

중요한 특징은 출발지 주소를 위조하면 응답은 보통 위조한 주소로 돌아간다는 점이다.

따라서 공격자가 응답을 직접 받아야 하는 일반적인 양방향 통신에는 한계가 있다.

한 줄 정리:

`IP Spoofing = 출발지 IP 위조`

---

## 5. ICMP Redirect 공격

ICMP Redirect 자체는 라우터가 호스트에게 더 적절한 경로를 알려주는 정상 기능이다.

공격자는 가짜 Redirect 메시지를 이용해 피해자의 라우팅 경로를 바꾸려고 할 수 있다.

예:

```text
원래 경로
Victim → Gateway

공격 후
Victim → Attacker → Gateway
```

한 줄 정리:

`ICMP Redirect 공격 = 잘못된 라우팅 경로를 믿게 만드는 공격`

---

## 6. Smurf Attack

Smurf Attack은 ICMP Echo Request와 Broadcast, IP Spoofing을 함께 악용하는 공격이다.

공격자가 출발지 IP를 피해자의 IP로 위조한 뒤 브로드캐스트 주소로 Ping 요청을 보낸다.

여러 호스트가 응답하면 응답이 피해자에게 몰린다.

```text
Attacker
  ↓ Source IP = Victim
Broadcast Network
  ↓↓↓
여러 Host
  ↓↓↓
Victim
```

한 줄 정리:

`Smurf = ICMP + Broadcast + IP Spoofing`

---

## 7. Ping of Death

비정상적으로 큰 IP/ICMP 패킷을 여러 조각으로 나누어 전송한 뒤, 피해 시스템이 이를 재조립하는 과정에서 오류나 장애를 일으키게 하는 고전적인 DoS 공격이다.

현대 운영체제에서는 대부분 방어되어 있지만 시험에는 자주 등장한다.

한 줄 정리:

`Ping of Death = 비정상적으로 큰 ICMP 패킷`

---

## 8. Land Attack

출발지 IP와 목적지 IP를 모두 피해자의 IP로 설정하는 고전적인 DoS 공격이다.

```text
Source IP      = Victim
Destination IP = Victim
```

피해 시스템이 자기 자신과 통신하는 비정상 상태를 만들려는 공격이다.

한 줄 정리:

`Land Attack = Source IP와 Destination IP가 모두 피해자`

---

## 9. TCP 3-Way Handshake와 SYN Flooding

### TCP 3-Way Handshake

TCP 연결은 다음 순서로 만들어진다.

```text
Client → Server : SYN
Server → Client : SYN + ACK
Client → Server : ACK
```

- SYN: 연결을 시작하고 순서번호를 맞추자는 의미
- ACK: 상대방이 보낸 내용을 받았다는 확인

보통 발음은 다음처럼 한다.

- SYN: 신
- ACK: 액
- SYN-ACK: 신액

### SYN Flooding

공격자가 SYN을 대량으로 보내고 마지막 ACK를 보내지 않는 방식이다.

```text
Attacker → Server : SYN
Server → Attacker : SYN + ACK
Attacker : 응답하지 않음
```

서버는 아직 연결이 완료되지 않은 Half-Open Connection을 일정 시간 유지한다.

이 상태가 대량으로 쌓이면 연결 대기 큐나 서버 자원이 고갈될 수 있다.

대표 대응 기술:

- SYN Cookie

SYN Cookie는 정상적으로 마지막 ACK까지 보내는 클라이언트에 대해서만 실제 연결 상태를 할당하는 데 도움을 준다.

한 줄 정리:

`SYN Flooding = SYN만 대량으로 보내고 ACK를 완료하지 않아 Half-Open 상태를 쌓는 공격`

---

## 10. TCP Session Hijacking

이미 만들어진 TCP 세션을 공격자가 가로채는 공격이다.

TCP는 Sequence Number를 이용해 패킷의 순서를 관리한다.

공격자가 해당 값을 알아내거나 예측해 정상 사용자인 것처럼 패킷을 만들면 세션 탈취 공격에 활용될 수 있다.

한 줄 정리:

`TCP Session Hijacking = 기존 TCP 세션의 Sequence Number 등을 악용해 세션을 탈취`

---

## 11. DNS Spoofing과 DNS Cache Poisoning

### DNS Spoofing

DNS 질의에 가짜 응답을 보내 사용자를 잘못된 IP 주소로 유도하는 공격이다.

```text
bank.com → 정상 IP

공격자가 위조
bank.com → 공격자 IP
```

### DNS Cache Poisoning

DNS 서버가 저장하고 있는 캐시 자체에 잘못된 정보를 주입하는 공격이다.

캐시가 오염되면 해당 DNS 서버를 사용하는 여러 사용자가 동시에 잘못된 주소로 연결될 수 있다.

차이:

- DNS Spoofing = DNS 응답을 속임
- DNS Cache Poisoning = DNS 서버의 저장된 캐시를 오염시킴

대표 대응 기술:

- DNSSEC

DNSSEC은 DNS 응답의 전자서명을 검증해 응답의 신뢰성을 높인다.

---

## 12. DoS / DDoS / DRDoS

### DoS

한 공격원이 피해 시스템을 직접 공격한다.

```text
공격자 1개 → 피해 서버
```

예:

- SYN Flooding

### DDoS

여러 공격원이 동시에 하나의 피해 시스템을 공격한다.

```text
여러 공격자 → 피해 서버
```

봇넷이 자주 이용된다.

### DRDoS

Distributed Reflection Denial of Service.

공격자가 제3의 정상 서버들을 반사체(Reflector)로 이용한다.

출발지 IP를 피해자의 IP로 위조해 요청하면 정상 서버들의 응답이 피해자에게 전달된다.

```text
Attacker
   ↓ Source IP = Victim
여러 정상 서버
   ↓↓↓
Victim
```

응답 크기가 요청보다 큰 프로토콜을 이용하면 Amplification 효과도 발생할 수 있다.

핵심 비교:

- DoS = 혼자 직접 공격
- DDoS = 여러 공격자가 동시에 직접 공격
- DRDoS = 제3의 정상 서버가 대신 공격하도록 만듦

---

# IDS / IPS

## 13. IDS

IDS는 Intrusion Detection System, 침입탐지시스템이다.

공격이나 이상 행위를 발견하고 관리자에게 알려주는 것이 핵심이다.

```text
IDS = 탐지 + 알림
```

일반적으로 트래픽 경로 옆에서 관찰하는 구조로 많이 배운다.

쉽게 비유하면 CCTV에 가깝다.

---

## 14. IPS

IPS는 Intrusion Prevention System, 침입방지시스템이다.

공격을 탐지하는 데서 끝나지 않고 직접 패킷을 차단하거나 세션을 종료할 수 있다.

```text
IPS = 탐지 + 차단
```

트래픽 경로에 Inline으로 배치되는 경우가 많다.

쉽게 비유하면 경비원에 가깝다.

### IDS와 IPS 차이

- IDS = 보면 신고
- IPS = 보면 막음

IPS는 정상 트래픽을 공격으로 오판하면 실제 서비스 트래픽을 차단할 수 있기 때문에 오탐의 영향이 더 클 수 있다.

---

## 15. HIDS / NIDS

### HIDS

Host-based IDS.

특정 서버나 PC 내부를 감시한다.

예:

- 로그
- 파일 변경
- 프로세스
- 시스템 이벤트

### NIDS

Network-based IDS.

네트워크 구간의 패킷이나 세션을 감시한다.

예:

- 패킷
- 네트워크 공격 패턴
- 비정상 세션

한 줄 정리:

- HIDS = 호스트 내부 감시
- NIDS = 네트워크 구간 감시

---

## 16. 오용탐지와 이상탐지

### 오용탐지 Misuse Detection

이미 알려진 공격 패턴이나 Signature를 기준으로 탐지한다.

비유:

`수배 전단을 보고 범인을 찾는 방식`

장점:

- 알려진 공격 탐지에 강함
- 비교적 오탐이 적음
- 탐지 원인을 설명하기 쉬움

단점:

- 새로운 공격에 약함
- Signature 업데이트가 필요함

### 이상탐지 Anomaly Detection

정상적인 행동 Baseline을 기준으로 평소와 다른 행위를 탐지한다.

예:

- 평소보다 비정상적으로 많은 트래픽
- 평소와 다른 시간대 로그인
- 갑작스러운 대량 파일 접근

비유:

`평소 행동과 너무 다른 사람을 찾는 방식`

장점:

- 알려지지 않은 공격을 발견할 가능성이 있음
- 신종 공격이나 Zero-day 탐지에 유리할 수 있음

단점:

- 정상 행동도 이상으로 판단할 수 있어 오탐이 많아질 수 있음

핵심 비교:

- 오용탐지 = 아는 공격 찾기
- 이상탐지 = 평소와 다른 행동 찾기

---

## 17. Zero-day

Zero-day 취약점은 아직 패치가 제공되지 않았거나 방어 측이 충분한 대응 준비를 하지 못한 새로운 취약점을 의미한다.

관련 용어:

- Zero-day Vulnerability = 새로운 미패치 취약점
- Zero-day Exploit = 해당 취약점을 악용하는 기법
- Zero-day Attack = 이를 이용한 실제 공격

오용탐지는 Signature가 없는 신종 공격에 약할 수 있지만, 이상탐지는 행동 변화 자체를 기준으로 탐지할 가능성이 있다.

---

## 18. FP / FN

탐지 시스템에서 Positive는 공격으로 판단했다는 뜻이고 Negative는 정상이라고 판단했다는 뜻이다.

| 실제 상태 | 탐지 결과 | 이름 |
| --- | --- | --- |
| 공격 | 공격 | TP (True Positive) |
| 정상 | 정상 | TN (True Negative) |
| 정상 | 공격 | FP (False Positive) |
| 공격 | 정상 | FN (False Negative) |

### FP

False Positive, 오탐.

정상인데 공격이라고 판단한 경우다.

### FN

False Negative, 미탐.

실제 공격인데 정상이라고 판단해 놓친 경우다.

암기:

- FP = 괜히 잡음
- FN = 잡아야 하는데 놓침

보안 관점에서는 일반적으로 FN을 줄이는 것이 매우 중요하지만, IPS처럼 실제 차단을 수행하는 시스템에서는 FP 역시 서비스 장애로 이어질 수 있다.

---

# Firewall

## 19. 방화벽이란?

Firewall은 네트워크 트래픽을 정책에 따라 허용하거나 차단하는 장비 또는 기능이다.

주로 확인하는 정보:

- Source IP
- Destination IP
- Source Port
- Destination Port
- Protocol
- Inbound / Outbound 방향

예:

```text
사내망 → Web Server TCP 443 : ALLOW
외부망 → Server TCP 22      : DENY
```

방화벽 정책은 Rule, Policy, ACL 등으로 표현할 수 있다.

### Rule 순서

방화벽은 위에서부터 규칙을 평가하는 구조가 많기 때문에 Rule 순서가 중요하다.

예:

```text
1. ANY → ANY ALLOW
2. 특정 IP DENY
```

이면 1번에서 이미 모두 허용되기 때문에 2번 규칙이 의미가 없어질 수 있다.

---

## 20. Packet Filtering Firewall

패킷 헤더의 정보를 중심으로 허용/차단 여부를 판단한다.

주로 보는 값:

- IP
- Port
- Protocol

장점:

- 빠름
- 구조가 단순함

단점:

- 패킷의 애플리케이션 내용까지 깊게 확인하기 어려움

비유:

`신분증 겉정보만 보고 출입 판단`

---

## 21. Stateful Inspection Firewall

개별 패킷뿐 아니라 현재 연결 상태를 기억하고 추적한다.

예를 들어 TCP의 SYN, SYN/ACK, ACK 흐름을 보고 정상적으로 만들어진 세션인지 확인할 수 있다.

비유:

`출입기록까지 확인하는 경비 시스템`

Packet Filtering보다 연결의 문맥을 더 많이 이해한다.

---

## 22. Proxy Firewall / Application Gateway

클라이언트와 서버가 직접 통신하지 않고 프록시가 중간에서 대신 통신하는 형태다.

```text
Client → Proxy Firewall → Server
```

애플리케이션 계층의 정보를 더 자세히 검사할 수 있다.

예:

- HTTP 요청
- URL
- Method
- Header
- FTP 명령

장점:

- 세밀한 제어 가능

단점:

- 자원 사용량과 처리 비용이 증가할 수 있음

---

## 23. NGFW

Next-Generation Firewall.

전통적인 방화벽 기능에 다양한 보안 기능을 통합한 형태다.

예:

- Application Control
- IDS/IPS
- URL Filtering
- 사용자 기반 정책
- TLS 검사
- 악성코드 탐지

---

## 24. Default Deny

보안상 기본적인 원칙은 명시적으로 허용한 것만 통과시키고 나머지는 차단하는 것이다.

```text
ALLOW: 필요한 통신
DENY : 나머지 전체
```

이를 Default Deny 또는 Whitelist 중심 정책으로 이해할 수 있다.

---

## 25. Firewall / IDS / IPS / WAF 비교

### Firewall

`이 IP/Port/Protocol 통신을 허용할 것인가?`

### IDS

`이 통신이 공격처럼 보이는가?`

### IPS

`공격처럼 보이면 직접 차단할 것인가?`

### WAF

HTTP/HTTPS 요청의 애플리케이션 내용을 중심으로 웹 공격을 탐지/차단한다.

예:

- SQL Injection
- XSS

짧게 정리:

- Firewall = 네트워크 접근 통제
- IDS = 공격 탐지
- IPS = 공격 탐지 + 차단
- WAF = 웹 요청 내용 보호

---

# DMZ

## 26. DMZ란?

DMZ는 외부에 공개해야 하는 서버를 내부망과 분리해 놓는 완충 구역이다.

예:

- Web Server
- Mail Server
- DNS Server
- Proxy Server

기본 구조:

```text
Internet
   ↓
  DMZ
   ↓
Internal Network
```

외부에 노출된 서버가 침해되더라도 공격자가 내부망으로 바로 이동하기 어렵게 만드는 것이 목적이다.

한 줄 정리:

`DMZ = 외부망과 내부망 사이의 완충지대`

### 실무 예시: 폐쇄망의 DMZ Proxy

폐쇄망 서버가 인터넷의 외부 서비스와 직접 통신할 수 없을 때 DMZ에 Proxy 서버를 둘 수 있다.

```text
폐쇄망 서버
   ↓
DMZ Proxy
   ↓ 공인 IP
외부 서비스
```

이 경우 폐쇄망 전체에 인터넷 연결을 열지 않고 필요한 통신만 DMZ Proxy를 통해 외부로 전달할 수 있다.

내부 클라이언트가 외부로 접근하기 위한 중계이므로 Forward Proxy 성격으로 이해할 수 있다.

---

# VPN / IPsec

## 27. VPN

VPN은 Virtual Private Network, 가상 사설망이다.

인터넷과 같은 공용망 위에 안전한 가상 전용 통로를 만드는 기술/개념이다.

```text
본사 → [암호화된 VPN 터널] → 지사
```

대표 형태:

### Site-to-Site VPN

네트워크와 네트워크를 연결한다.

예:

`본사 ↔ 지사`

### Remote Access VPN

개인 사용자 단말이 회사 네트워크에 접속한다.

예:

`재택근무 PC ↔ 회사망`

---

## 28. 전용회선과 VPN 차이

### 전용회선

통신사 등을 통해 특정 조직 전용의 물리적/논리적 통신 경로를 확보하는 방식이다.

```text
본사 ===== 전용 경로 ===== 지사
```

### VPN

공용 인터넷을 이용하지만 암호화와 인증을 통해 전용망처럼 사용한다.

```text
본사 → 인터넷 위의 VPN 터널 → 지사
```

비유:

- 전용회선 = 회사 전용 도로
- VPN = 공용도로 위에 만든 안전한 전용 터널

---

## 29. IPsec

IPsec은 Internet Protocol Security의 약자다.

IP 계층에서 IP 패킷을 보호하기 위한 보안 기술 묶음이다.

제공할 수 있는 기능:

- 기밀성
- 무결성
- 인증
- Replay 공격 방지

VPN과의 관계:

- VPN = 안전한 가상 통로라는 개념
- IPsec = 해당 VPN을 구현할 때 사용할 수 있는 대표적인 보안 기술

즉 `IPsec VPN`은 IPsec으로 보호되는 VPN을 의미한다.

---

## 30. AH와 ESP

### AH

Authentication Header.

주요 기능:

- 인증
- 무결성
- 출처 확인

하지만 암호화는 제공하지 않는다.

```text
AH = 인증 + 무결성 / 암호화 X
```

### ESP

Encapsulating Security Payload.

주요 기능:

- 암호화
- 인증
- 무결성

```text
ESP = 암호화 + 인증 + 무결성
```

실무에서는 ESP가 더 널리 사용된다.

시험 포인트:

`AH는 암호화하지 않고 ESP는 암호화한다.`

---

## 31. Transport Mode와 Tunnel Mode

### Transport Mode

원래 IP Header는 두고 Payload를 중심으로 보호한다.

```text
[IP Header][Protected Payload]
```

주로 Host ↔ Host 통신과 연결해 이해한다.

### Tunnel Mode

원래 IP 패킷 전체를 내부에 넣고 새로운 외부 IP Header를 추가한다.

```text
[New IP Header][Original IP Header + Payload]
```

주로 Gateway ↔ Gateway, Site-to-Site VPN과 연결해서 이해한다.

암기:

- Transport = 내용물만 포장
- Tunnel = 원래 택배 상자 전체를 더 큰 상자에 넣음

---

## 32. IKE

IKE는 Internet Key Exchange다.

IPsec 통신을 시작하기 전에 상대방 인증, 키 교환, 암호 알고리즘 등 보안 조건을 협상한다.

쉽게 보면 TLS Handshake와 비슷하게 통신 전 조건을 맞추는 역할이다.

전체 흐름:

```text
IKE 협상
→ IPsec SA 생성
→ ESP/AH로 패킷 보호
→ 안전한 통신
```

---

## 33. IPsec과 TLS의 차이

둘 다 통신 보안을 제공하지만 적용되는 계층과 보호 범위가 다르다.

### TLS

HTTP 같은 애플리케이션 통신을 보호한다.

예:

```text
HTTP
↓
TLS
↓
TCP
↓
IP
```

HTTPS가 대표적이다.

### IPsec

더 아래인 IP 계층에서 IP 패킷 자체를 보호한다.

따라서 특정 애플리케이션 하나가 아니라 네트워크 경로 전체를 보호하는 용도로 활용하기 좋다.

둘을 동시에 사용할 수도 있다.

예:

```text
HTTPS(TLS)
↓
IPsec VPN
↓
Network
```

즉 TLS로 보호된 HTTPS 데이터가 다시 IPsec VPN 터널 안을 통과할 수도 있다.

한 줄 정리:

- TLS = 서비스/애플리케이션 통신 보호
- IPsec = 네트워크/IP 패킷 보호

---

# 핵심 암기

```text
Sniffing = 패킷 엿보기
ARP Spoofing = IP-MAC 매핑 속이기
IP Spoofing = Source IP 위조
Smurf = ICMP + Broadcast + IP Spoofing
SYN Flooding = Half-Open Connection 쌓기
DNS Spoofing = DNS 응답 속이기
DNS Cache Poisoning = DNS 캐시 오염

DoS = 혼자 공격
DDoS = 여러 공격자가 공격
DRDoS = 정상 서버들을 반사체로 이용

IDS = 탐지
IPS = 탐지 + 차단
오용탐지 = 알려진 Signature
이상탐지 = 정상 Baseline에서 벗어난 행동
FP = 정상인데 공격이라고 오탐
FN = 공격인데 정상이라고 미탐

Firewall = 정책 기반 접근 통제
Stateful = 세션 상태까지 추적
DMZ = 외부와 내부 사이 완충지대

VPN = 공용망 위 가상 사설망
IPsec = IP 계층 보안
AH = 인증/무결성, 암호화 X
ESP = 암호화 + 인증/무결성
Transport = Payload 중심 보호
Tunnel = 원래 IP 패킷 전체를 감쌈
IKE = IPsec 연결 전 인증/키/조건 협상
```
