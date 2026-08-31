# 정보보안기사 공부 로드맵

시험까지 이 문서의 체크리스트를 위에서 아래로 따라간다.

> 기준: 정보보안기사 교재 목차(SECTION 01~43)를 빠짐없이 포함하되, 실제 공부하기 편한 순서로 재배열한다.

## 공부 방식

각 주제는 다음 순서로 공부한다.

1. 개념을 쉬운 말로 이해하기
2. 왜 필요한지 이해하기
3. 공격/사고 상황과 연결하기
4. 시험에서 어떻게 묻는지 정리하기
5. 공부한 날마다 별도 TIL 문서 작성하기

---

## 1. 정보보호 기본 개념

교재: SECTION 01 정보보호관리의 개념

- [x] 정보보안이 무엇인지
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
- [x] 자산 / 위협 / 취약점 / 위험의 기본 관계
- [x] 위험 회피 / 감소 / 전가 / 수용
- [ ] OSI 보안 구조: 보안공격 / 보안메커니즘 / 보안서비스
- [ ] 위협 Threat / 취약점 Vulnerability / 위험 Risk / 공격 Attack 정확히 구분
- [ ] 보안 통제: 예방 / 탐지 / 교정
- [ ] 최소권한 / 직무분리

관련 노트: `Security/Basics/security-basics.md`

---

## 2. 접근통제와 사용자 인증

교재: SECTION 08~11

### 접근통제 기본

- [x] 접근통제의 목적과 기본 개념
- [x] 식별 Identification
- [x] 인증 Authentication
- [x] 인가 Authorization
- [x] 책임추적성 Accountability
- [ ] 최소권한 원칙
- [ ] Need-to-Know
- [ ] 직무분리 Separation of Duties

### 사용자 인증

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

### 비밀번호 저장 ⭐ 현재 공부 중

- [x] Hash 기본 개념
- [x] 암호화와 Hash의 차이
- [x] Salt
- [x] Rainbow Table
- [ ] Key Stretching
- [ ] PBKDF2 / bcrypt / scrypt / Argon2 개념

### 접근통제 모델

- [ ] DAC
- [ ] MAC (Mandatory Access Control)
- [ ] RBAC
- [ ] ABAC
- [ ] Bell-LaPadula
- [ ] Biba
- [ ] Clark-Wilson
- [ ] 접근통제 관련 보안위협 및 대응책

> 주의: `MAC`은 문맥에 따라 MAC Address / Message Authentication Code / Mandatory Access Control을 뜻할 수 있다.

---

## 3. 암호학

교재: SECTION 02~07

### 암호학 개요

- [ ] 평문 / 암호문 / 암호화 / 복호화 / 키
- [ ] Kerckhoffs's Principle
- [ ] 치환 / 전치
- [ ] 대칭키 / 비대칭키 / 해시 분류
- [ ] 암호 분석: 암호문 단독 / 알려진 평문 / 선택 평문 / 선택 암호문 공격
- [ ] 암호 알고리즘 안전성 평가

### 대칭키 암호

- [ ] 블록 암호와 스트림 암호
- [ ] DES / 3DES
- [ ] AES
- [ ] 기타 대칭키 알고리즘
- [ ] 블록 암호 운용모드: ECB / CBC / CFB / OFB / CTR

### 비대칭키 암호

- [ ] 공개키 / 개인키 기본 원리
- [ ] RSA
- [ ] Diffie-Hellman
- [ ] ECC
- [ ] 대칭키와 비대칭키 비교
- [ ] 하이브리드 암호시스템

### 해시와 메시지 인증

교재: SECTION 05

- [x] 일방향 Hash의 기본 개념
- [ ] 암호학적 해시함수의 조건
- [ ] MD5
- [ ] SHA 계열
- [ ] 충돌 Collision / 생일 공격 Birthday Attack
- [ ] MAC(Message Authentication Code)
- [ ] HMAC

### 전자서명과 PKI

교재: SECTION 06

- [ ] 전자서명의 목적
- [ ] 무결성 / 인증 / 부인방지
- [ ] 전자서명 생성·검증 흐름
- [ ] 공개키와 개인키 사용 방향
- [ ] 인증서 Certificate
- [ ] CA / RA
- [ ] PKI
- [ ] CRL / OCSP
- [ ] 인증서 체인

### 키와 난수

교재: SECTION 07

- [ ] 키 생성 / 분배 / 저장 / 폐기
- [ ] 세션키 / 마스터키
- [ ] 난수와 의사난수
- [ ] CSPRNG 개념

---

## 4. 시스템 보안

교재: SECTION 12~18

### 보안 운영체제

- [ ] 보안 운영체제 개념
- [ ] 참조 모니터 Reference Monitor
- [ ] 보안 커널 Security Kernel
- [ ] TCB
- [ ] TPM

### 클라이언트 / 악성코드

- [ ] Virus
- [ ] Worm
- [ ] Trojan Horse
- [ ] Ransomware
- [ ] Rootkit
- [ ] Backdoor
- [ ] Logic Bomb
- [ ] Bot / Botnet
- [ ] Keylogger
- [ ] 악성코드 탐지 및 대응

### Windows 서버 보안

- [ ] SID
- [ ] NTFS 권한
- [ ] 공유 권한
- [ ] 레지스트리
- [ ] 이벤트 로그
- [ ] 계정 정책
- [ ] Windows 서버 주요 보안 설정

### UNIX / Linux 서버 보안

- [ ] 사용자 / 그룹 / UID / GID
- [ ] 파일 권한 rwx
- [ ] chmod / chown / chgrp
- [ ] SUID / SGID / Sticky Bit
- [ ] umask
- [ ] PAM
- [ ] 주요 로그 파일
- [ ] cron / at
- [ ] 프로세스와 서비스
- [ ] 불필요 서비스 제거
- [ ] UNIX/Linux 취약점 분석·평가

### 서버 보안 관리

- [ ] 서버관리자의 주요 업무
- [ ] 로그 설정과 관리
- [ ] 공개 해킹도구 이해와 대응
- [ ] 서버 보안 S/W

### 시스템 공격

- [ ] Buffer Overflow
- [ ] Format String
- [ ] Race Condition
- [ ] Backdoor
- [ ] 시스템 자원 고갈 공격
- [ ] Privilege Escalation
- [ ] Reverse Engineering

### 최신 시스템 보안 주제

- [ ] Blockchain
- [ ] IoT 보안
- [ ] Cloud 보안
- [ ] Ransomware
- [ ] APT

---

## 5. 네트워크 보안

교재: SECTION 19~30

### 네트워크 기초

- [ ] OSI 7계층과 TCP/IP 모델 정리
- [x] Ethernet과 MAC 주소 기본
- [x] ARP 동작 원리
- [x] IP 기본 동작과 최선형 전달
- [x] ICMP 기본
- [ ] TCP 3-way handshake
- [ ] TCP 연결 종료
- [ ] UDP
- [ ] 주요 포트 번호
- [ ] DNS 기본 동작
- [ ] NAT
- [ ] 물리 / 데이터링크 / 네트워크 / 전송 / 응용 계층 주요 프로토콜

### 라우팅 / 네트워크 장비

- [ ] 라우팅 기본
- [ ] 정적 / 동적 라우팅
- [ ] 주요 라우팅 프로토콜
- [ ] Router / Switch / Hub / Bridge / Gateway
- [ ] VLAN 구성과 보안
- [ ] 라우터 보안

### 무선 / 모바일 보안

- [ ] 무선통신 기본
- [ ] WEP / WPA / WPA2 / WPA3
- [ ] 무선랜 공격과 대응
- [ ] WAP
- [ ] 디바이스 인증
- [ ] RFID
- [ ] 모바일 보안

### 네트워크 관리

- [ ] SNMP
- [ ] Telnet / SSH 등 원격접속 서비스
- [ ] 네트워크 관리 기본
- [ ] 네트워크 기반 프로그램 활용

### 네트워크 공격

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

### IDS / IPS

- [ ] IDS와 IPS 차이
- [ ] HIDS / NIDS
- [ ] 오용탐지 / 이상탐지
- [ ] False Positive / False Negative

### Firewall

- [ ] Firewall 기본
- [ ] Packet Filtering
- [ ] Stateful Inspection
- [ ] Proxy Firewall / Application Gateway
- [ ] 구축 형태
- [ ] iptables

### VPN / IPsec

- [ ] VPN
- [ ] IPsec
- [ ] AH / ESP
- [ ] 전송 모드 / 터널 모드
- [ ] IKE

### 최신 네트워크 보안기술

- [ ] NAC
- [ ] WAF와 네트워크 보안 장비의 차이
- [ ] Zero Trust 기본 개념

---

## 6. 애플리케이션 보안

교재: SECTION 31~38

### FTP / 이메일

- [ ] FTP / TFTP / SFTP
- [ ] FTP 보안 위협과 대응
- [ ] SMTP / POP3 / IMAP
- [ ] PGP / S/MIME
- [ ] 스팸 대응 기술
- [ ] Sendmail 보안

### Web Security

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

### DHCP / DNS 보안

- [ ] DHCP 동작
- [ ] DHCP Spoofing / Starvation
- [ ] DNS 동작
- [ ] DNS Spoofing / Cache Poisoning
- [ ] DNSSEC
- [ ] DNS 서버 보안 설정

### DB 보안

- [ ] 데이터베이스 보안 요구사항
- [ ] DB 접근통제
- [ ] DB 암호화
- [ ] DB 감사 / 로그
- [ ] DBMS 보안 관리

### 전자상거래 보안

- [ ] 전자상거래 정보보호
- [ ] SET
- [ ] 전자상거래 응용 보안

### 침해사고 대응 / 디지털 포렌식

- [ ] 침해사고 대응 절차
- [ ] 증거 수집 / 보존 / 분석
- [ ] Chain of Custody
- [ ] 디지털 포렌식 기본 원칙

### 기타 애플리케이션 보안

- [ ] 각종 애플리케이션 보안위협과 대응
- [ ] Java 보안

---

## 7. 정보보호 관리 및 법규

교재: SECTION 39~43

### 정보보호 거버넌스 / 관리체계

- [ ] 정보보호 거버넌스
- [ ] IT 보안 관리
- [ ] 정책 / 절차 / 표준 / 지침 / 기준선 차이
- [ ] 인적 자원 보안

### 위험관리

- [x] 위험관리 기본 개념
- [x] 위험 회피 / 감소 / 전가 / 수용
- [ ] 위험분석 Risk Analysis
- [ ] 정성적 / 정량적 위험분석
- [ ] 자산가치 / 노출계수 / SLE / ARO / ALE

### BCP / DRP

- [ ] BCP
- [ ] DRP
- [ ] BIA
- [ ] RTO / RPO
- [ ] 백업 종류와 복구전략
- [ ] Hot / Warm / Cold Site

### 인증제도

- [ ] 보안제품 평가방법과 기준
- [ ] Common Criteria(CC)
- [ ] ISMS
- [ ] ISMS-P
- [ ] 기타 정보보호 인증제도

### 정보보호 관련 법규

> 법규는 시험 준비 시점의 최신 개정 내용을 다시 확인한다.

- [ ] 개인정보보호법
- [ ] 정보통신망 이용촉진 및 정보보호 등에 관한 법률
- [ ] 정보통신기반 보호법
- [ ] 개인정보 처리 원칙
- [ ] 수집 / 이용 / 제공
- [ ] 민감정보 / 고유식별정보
- [ ] 개인정보 파기
- [ ] 개인정보 유출 대응
- [ ] 법규의 주요 숫자 / 기간 / 의무사항

---

## 8. 시험 직전 정리

- [ ] 자주 헷갈리는 약어 모음
- [ ] 공격기법 이름 ↔ 원리 매칭
- [ ] 암호 알고리즘 비교표
- [ ] 접근통제 모델 비교표
- [ ] 주요 포트 번호
- [ ] Linux / Windows 주요 보안 설정
- [ ] IDS / IPS / Firewall / WAF 비교
- [ ] 법규 숫자 / 기간 / 기준
- [ ] 틀린 문제만 모은 오답노트
- [ ] 실전 기출 반복

---

## 지금 위치 및 다음 진도

현재 위치:

`접근통제 → 사용자 인증 → 비밀번호 공격 → Hash / Salt / Rainbow Table`

다음 순서:

1. **Key Stretching**
2. **PBKDF2 / bcrypt / scrypt / Argon2**
3. **암호학적 해시함수 조건과 MD5 / SHA**
4. **MAC / HMAC**
5. 이후 **대칭키 암호 → 비대칭키 암호 → 전자서명 / PKI**

한 항목을 공부할 때마다 체크리스트를 갱신하고, 공부 내용은 날짜별 별도 TIL 파일로 작성한다.
