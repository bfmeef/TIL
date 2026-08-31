# 정보보안기사 공부 로드맵

시험까지 이 문서의 체크리스트를 **교재 목차 순서 그대로** 위에서 아래로 따라간다.

> 기준: 사용 중인 정보보안기사 교재의 PART / SECTION 순서를 그대로 따른다. 임의로 재배열하지 않는다.

## 공부 방식

각 주제는 다음 순서로 공부한다.

1. 개념을 쉬운 말로 이해하기
2. 왜 필요한지 이해하기
3. 공격/사고 상황과 연결하기
4. 시험에서 어떻게 묻는지 정리하기
5. 공부한 날마다 별도 TIL 문서 작성하기

---

# PART 1 정보보호 개요

## SECTION 01 정보보호관리의 개념

- [x] 정보화 사회의 정보보호
- [x] 정보보호 관리의 기본 개념
- [x] CIA 3요소
  - [x] 기밀성 Confidentiality
  - [x] 무결성 Integrity
  - [x] 가용성 Availability
- [x] 일반 장애와 보안 사고의 차이
- [x] 인증 Authentication / 인가 Authorization
- [x] 인증성 Authenticity
- [x] 추적가능성 Accountability
- [x] 부인방지 Non-repudiation
- [x] 감사로그 Audit Log
- [ ] OSI 보안 구조
  - [ ] 보안 공격
  - [ ] 보안 서비스
  - [ ] 보안 메커니즘
- [x] 자산 / 위협 / 취약점 / 위험의 기본 관계
- [ ] 위협 Threat / 취약점 Vulnerability / 위험 Risk / 공격 Attack 정확히 구분
- [ ] 예방 / 탐지 / 교정 통제
- [ ] 최소권한 / 직무분리

관련 노트: `Security/Basics/security-basics.md`

---

# PART 2 암호학

## SECTION 02 암호학 개요

- [ ] 암호학의 기본 개념
  - [ ] 평문 / 암호문 / 암호화 / 복호화 / 키
  - [ ] Kerckhoffs's Principle
- [ ] 암호기법의 분류
  - [ ] 치환 / 전치
  - [ ] 대칭키 / 비대칭키 / 해시
  - [ ] 블록암호 / 스트림암호
- [ ] 주요 암호기술 개괄
- [ ] 암호 분석
  - [ ] 암호문 단독 공격
  - [ ] 알려진 평문 공격
  - [ ] 선택 평문 공격
  - [ ] 선택 암호문 공격
- [ ] 암호 알고리즘의 안전성 평가
- [ ] 지적 재산권 보호 관련 암호기술

## SECTION 03 대칭키 암호

- [ ] 현대 대칭키 암호의 기본 구조
- [ ] DES
- [ ] 3DES
- [ ] AES
- [ ] 기타 대칭키 암호 알고리즘
- [ ] 블록 암호 운용모드
  - [ ] ECB
  - [ ] CBC
  - [ ] CFB
  - [ ] OFB
  - [ ] CTR

## SECTION 04 비대칭키 암호

- [ ] 비대칭키 암호의 기본 원리
- [ ] 공개키 / 개인키
- [ ] RSA
- [ ] Diffie-Hellman
- [ ] ECC
- [ ] 대칭키와 비대칭키 방식 비교
- [ ] 하이브리드 암호시스템

## SECTION 05 해시함수와 응용 ⭐ 현재 공부 중

- [x] 일방향 해시함수 기본 개념
- [x] 암호화와 Hash의 차이
- [x] Salt
- [x] Rainbow Table
- [ ] 암호학적 해시함수의 조건
- [ ] MD5
- [ ] SHA 계열
- [ ] 충돌 Collision
- [ ] 생일 공격 Birthday Attack
- [ ] Key Stretching
- [ ] PBKDF2 / bcrypt / scrypt / Argon2 개념
- [ ] 메시지 인증코드 MAC
- [ ] HMAC

## SECTION 06 전자서명과 PKI

- [ ] 전자서명
  - [ ] 목적과 요구사항
  - [ ] 생성 / 검증 흐름
  - [ ] 무결성 / 인증 / 부인방지와의 관계
- [ ] PKI
- [ ] 인증서 Certificate
- [ ] CA / RA
- [ ] CRL
- [ ] OCSP
- [ ] 인증서 체인

## SECTION 07 키, 난수

- [ ] 키 생성 / 분배 / 저장 / 폐기
- [ ] 세션키 / 마스터키
- [ ] 난수 / 의사난수
- [ ] CSPRNG

---

# PART 3 접근통제

## SECTION 08 접근통제 개요

- [x] 접근통제의 목적과 기본 개념
- [x] 식별 Identification
- [x] 인증 Authentication
- [x] 인가 Authorization
- [x] 책임추적성 Accountability
- [ ] 최소권한 원칙
- [ ] Need-to-Know
- [ ] 직무분리 Separation of Duties

## SECTION 09 사용자 인증

- [ ] 지식 기반 인증: 비밀번호 / PIN
- [ ] 소유 기반 인증: OTP / 토큰 / 스마트카드
- [ ] 생체 기반 인증
- [ ] MFA / 2FA
- [x] Brute Force
- [x] Dictionary Attack
- [x] Credential Stuffing
- [x] Password Spraying
- [ ] Replay Attack
- [ ] Session Hijacking
- [ ] SSO / Single Sign-On

## SECTION 10 접근통제 보안 모델

- [ ] DAC
- [ ] MAC (Mandatory Access Control)
- [ ] RBAC
- [ ] ABAC
- [ ] Bell-LaPadula
- [ ] Biba
- [ ] Clark-Wilson

> 주의: `MAC`은 문맥에 따라 MAC Address / Message Authentication Code / Mandatory Access Control을 뜻할 수 있다.

## SECTION 11 접근통제 보안위협 및 대응책

- [ ] 접근통제 우회
- [ ] 인증정보 탈취
- [ ] 권한 상승
- [ ] 세션 관련 위협
- [ ] 접근통제 보안위협별 대응책

---

# PART 4 시스템 보안

## SECTION 12 보안 운영체제

- [ ] 보안 운영체제 개념
- [ ] 주요 제공 기능
- [ ] 참조 모니터 Reference Monitor
- [ ] 보안 커널 Security Kernel
- [ ] TCB
- [ ] TPM

## SECTION 13 클라이언트 보안

- [ ] 악성코드 개요
- [ ] Virus
- [ ] Worm
- [ ] Trojan Horse
- [ ] Rootkit
- [ ] Backdoor
- [ ] Logic Bomb
- [ ] Bot / Botnet
- [ ] Keylogger
- [ ] 인터넷 활용 보안

## SECTION 14 윈도우 서버 보안

- [ ] Windows 기본 구조
- [ ] SID
- [ ] NTFS 권한
- [ ] 공유 권한
- [ ] 레지스트리
- [ ] 이벤트 로그
- [ ] 계정 정책
- [ ] Windows 서버 주요 보안 설정

## SECTION 15 유닉스/리눅스 서버 보안

- [ ] UNIX 기본 개념 / 사용법
- [ ] 사용자 / 그룹 / UID / GID
- [ ] 파일 권한 rwx
- [ ] chmod / chown / chgrp
- [ ] SUID / SGID / Sticky Bit
- [ ] umask
- [ ] PAM
- [ ] 주요 로그 파일
- [ ] cron / at
- [ ] 프로세스 / 서비스 관리
- [ ] 불필요 서비스 제거
- [ ] Linux 기본
- [ ] UNIX/Linux 취약점 분석·평가

## SECTION 16 서버 보안 관리

- [ ] 서버관리자의 주요 업무
- [ ] 로그 설정과 관리
- [ ] 공개 해킹도구 이해와 대응
- [ ] 서버 보안 S/W 설치 및 운영

## SECTION 17 각종 시스템 보안위협 및 대응책

- [ ] Buffer Overflow
- [ ] Format String
- [ ] Race Condition
- [ ] Backdoor
- [ ] 시스템 자원 고갈 공격
- [ ] Privilege Escalation
- [ ] Reverse Engineering
- [ ] 기타 시스템 보안위협 및 대응책

## SECTION 18 최신 보안 주제들

- [ ] Blockchain
- [ ] IoT 보안
- [ ] Cloud 보안
- [ ] Ransomware
- [ ] APT
- [ ] 기타 최신 보안주제

---

# PART 5 네트워크 보안

## SECTION 19 네트워크 개요

- [ ] 네트워크 기본 개요
- [ ] OSI 7계층
- [ ] TCP/IP 모델

## SECTION 20 TCP/IP

- [ ] 물리 계층
- [x] 데이터링크 계층 기본
- [x] Ethernet / MAC 주소 기본
- [x] ARP 동작 원리
- [x] 네트워크 계층 / IP 기본 동작
- [x] 최선형 전달
- [x] ICMP 기본
- [ ] 전송 계층
- [ ] TCP 3-way handshake
- [ ] TCP 연결 종료
- [ ] UDP
- [ ] 응용 계층 주요 프로토콜
- [ ] 주요 포트 번호
- [ ] DNS 기본 동작
- [ ] NAT

## SECTION 21 라우팅

- [ ] 라우팅 개요
- [ ] 정적 / 동적 라우팅
- [ ] 유니캐스트 라우팅
- [ ] 주요 라우팅 프로토콜
- [ ] 라우터 보안

## SECTION 22 네트워크 장비의 이해

- [ ] Hub / Bridge / Switch / Router / Gateway
- [ ] 네트워크 장비별 동작 계층
- [ ] VLAN 구성과 관리

## SECTION 23 무선통신 보안

- [ ] 무선통신 기본
- [ ] WEP / WPA / WPA2 / WPA3
- [ ] 무선랜 공격과 대응
- [ ] WAP
- [ ] 디바이스 인증
- [ ] RFID
- [ ] 모바일 보안

## SECTION 24 네트워크 관리

- [ ] 네트워크 관리 기본
- [ ] SNMP
- [ ] Telnet / SSH 등 원격접속 서비스

## SECTION 25 네트워크 기반 프로그램 활용

- [ ] ping
- [ ] traceroute / tracert
- [ ] netstat / ss
- [ ] nslookup / dig
- [ ] arp
- [ ] tcpdump / Wireshark 기본
- [ ] 기타 네트워크 기반 프로그램 활용

## SECTION 26 네트워크 기반 공격의 이해

- [ ] Sniffing
- [ ] Promiscuous Mode
- [ ] ARP Spoofing / ARP Poisoning
- [ ] IP Spoofing
- [ ] ICMP Redirect 공격
- [ ] Smurf 공격
- [ ] Ping of Death
- [ ] Land Attack
- [ ] SYN Flooding
- [ ] TCP Session Hijacking
- [ ] DNS Spoofing / DNS Cache Poisoning
- [ ] DoS / DDoS
- [ ] DRDoS / 반사·증폭 공격

공격마다 다음을 정리한다.

`공격 원리 → 침해되는 보안 속성 → 탐지 → 대응`

## SECTION 27 IDS/IPS

- [ ] IDS와 IPS 차이
- [ ] HIDS / NIDS
- [ ] 오용탐지 / 이상탐지
- [ ] False Positive / False Negative

## SECTION 28 침입차단시스템(Firewall)

- [ ] Firewall 기본
- [ ] Packet Filtering
- [ ] Stateful Inspection
- [ ] Proxy Firewall / Application Gateway
- [ ] Firewall 유형 / 구축 형태
- [ ] iptables

## SECTION 29 VPN

- [ ] VPN
- [ ] IPsec
- [ ] AH / ESP
- [ ] 전송 모드 / 터널 모드
- [ ] IKE

## SECTION 30 최신 네트워크 보안기술

- [ ] NAC
- [ ] Zero Trust 기본
- [ ] 기타 최신 네트워크 보안기술

---

# PART 6 애플리케이션 보안

## SECTION 31 FTP 보안

- [ ] FTP / TFTP / SFTP
- [ ] FTP 보안 위협과 대응
- [ ] FTP 서비스 운영

## SECTION 32 이메일 보안

- [ ] SMTP / POP3 / IMAP
- [ ] 이메일 콘텐츠 보안
- [ ] PGP / S/MIME
- [ ] 스팸 대응 기술
- [ ] Sendmail 보안

## SECTION 33 웹 보안(Web Security)

- [ ] 웹 보안 개요
- [ ] HTTP 기본 구조
- [ ] Cookie / Session
- [ ] Same-Origin Policy
- [ ] SSL/TLS
- [ ] 웹서버 보안
- [ ] SQL Injection
- [ ] XSS: Stored / Reflected / DOM
- [ ] CSRF
- [ ] Command Injection
- [ ] File Upload 취약점
- [ ] Directory Traversal
- [ ] File Inclusion
- [ ] SSRF
- [ ] 인증 / 세션 취약점
- [ ] 접근통제 취약점
- [ ] 입력값 검증
- [ ] Prepared Statement
- [ ] 소프트웨어 개발보안 / Secure Coding

## SECTION 34 DHCP와 DNS 보안

- [ ] DHCP 동작
- [ ] DHCP Spoofing / Starvation
- [ ] DNS 동작
- [ ] DNS Spoofing / Cache Poisoning
- [ ] DNSSEC
- [ ] DNS 서버 보안 설정

## SECTION 35 데이터베이스 보안

- [ ] 데이터베이스 기본 개념
- [ ] 데이터베이스 보안 요구사항
- [ ] DB 접근통제
- [ ] DB 암호화
- [ ] DB 감사 / 로그
- [ ] DBMS 보안 관리

## SECTION 36 전자상거래 보안

- [ ] 전자상거래 정보보호
- [ ] SET
- [ ] 전자상거래 응용 보안

## SECTION 37 침해사고 대응(디지털 포렌식)

- [ ] 해킹 개요
- [ ] 침해사고 대응 절차
- [ ] 증거 수집 / 보존 / 분석
- [ ] Chain of Custody
- [ ] 디지털 포렌식 기본 원칙

## SECTION 38 각종 애플리케이션 보안위협 및 대응책

- [ ] 각종 애플리케이션 보안위협과 대응
- [ ] Java 보안

---

# PART 7 정보보호 관리 및 법규

## SECTION 39 정보보호 거버넌스와 관리 체계 수립

- [ ] 정보보호 거버넌스
- [ ] IT 보안 관리
- [ ] 정책 / 절차 / 표준 / 지침 / 기준선 차이
- [ ] 인적 자원 보안

## SECTION 40 정보보호 위험 관리

- [x] 위험관리 기본 개념
- [x] 자산 / 위협 / 취약점 / 위험 관계
- [x] 위험 회피 / 감소 / 전가 / 수용
- [ ] 위험분석
- [ ] 정성적 위험분석
- [ ] 정량적 위험분석
- [ ] ALE / SLE / ARO

## SECTION 41 BCP/DRP

- [ ] BCP
- [ ] DRP
- [ ] BIA
- [ ] RTO
- [ ] RPO
- [ ] 백업 종류
- [ ] 복구 전략

## SECTION 42 정부부처 인증제도

- [ ] 보안제품 평가방법 및 기준
- [ ] CC / EAL
- [ ] 정보보호관리체계 인증
- [ ] ISMS-P
- [ ] 기타 인증제도 및 정보보호 활동

## SECTION 43 정보보호 관련 법규

- [ ] 개인정보보호법
- [ ] 정보통신망 이용촉진 및 정보보호 등에 관한 법률 관련 범위
- [ ] 정보통신기반 보호법
- [ ] 개인정보 수집 / 이용 / 제공
- [ ] 민감정보 / 고유식별정보
- [ ] 개인정보 파기
- [ ] 개인정보 유출 대응
- [ ] 시험에 나오는 숫자 / 기간 / 신고 기준 정리

---

# 시험 직전 정리

- [ ] 자주 헷갈리는 약어 모음
- [ ] 공격기법 이름 ↔ 원리 매칭
- [ ] 암호 알고리즘 비교표
- [ ] 접근통제 모델 비교
- [ ] 주요 포트 번호
- [ ] 법규 숫자 / 기간 / 기준
- [ ] 틀린 문제만 모은 오답노트
- [ ] 실전 기출 반복

---

# 지금 다음 진도

교재 순서상 현재는 **PART 2 암호학 → SECTION 05 해시함수와 응용**을 공부 중이다.

다음 순서:

1. **암호학적 해시함수의 조건**
2. **MD5 / SHA 계열**
3. **충돌 Collision / 생일 공격 Birthday Attack**
4. **Key Stretching**
5. **PBKDF2 / bcrypt / scrypt / Argon2**
6. **MAC / HMAC**
7. 이후 **SECTION 06 전자서명과 PKI**로 이동

한 항목을 공부할 때마다 이 체크리스트를 체크하고, 공부한 내용은 해당 날짜의 별도 TIL 문서로 작성한다.
