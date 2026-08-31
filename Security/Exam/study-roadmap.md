# 정보보안기사 공부 로드맵

시험까지 이 문서의 체크리스트를 위에서 아래로 따라간다.

## 공부 방식

각 주제는 다음 순서로 공부한다.

1. 개념을 쉬운 말로 이해하기
2. 왜 필요한지 이해하기
3. 공격/사고 상황과 연결하기
4. 시험에서 어떻게 묻는지 정리하기
5. 관련 내용을 TIL 문서에 누적하기

---

## 1. 보안 기본 개념

- [x] 정보보안이 무엇인지
- [x] CIA 3요소
  - [x] 기밀성 Confidentiality
  - [x] 무결성 Integrity
  - [x] 가용성 Availability
- [x] 일반 장애와 보안 사고의 차이
- [x] 인증 Authentication
- [x] 인가 Authorization
- [x] 인증성 Authenticity
- [x] 추적가능성 Accountability
- [x] 부인방지 Non-repudiation
- [x] 감사로그 Audit Log
- [ ] 위협 Threat / 취약점 Vulnerability / 위험 Risk / 공격 Attack 구분
- [ ] 보안 통제의 종류: 예방 / 탐지 / 교정
- [ ] 최소권한의 원칙
- [ ] 직무분리와 권한분리

관련 노트: `Security/Basics/security-basics.md`

---

## 2. 네트워크 기초 복습

보안 공격을 이해하기 위한 최소 네트워크 지식만 복습한다.

- [ ] OSI 7계층과 TCP/IP 모델
- [ ] Ethernet과 MAC 주소
- [ ] ARP 동작 원리
- [ ] IP와 라우팅
- [ ] ICMP
- [ ] TCP 3-way handshake
- [ ] TCP 연결 종료
- [ ] UDP
- [ ] 주요 포트 번호
- [ ] DNS 기본 동작
- [ ] NAT

---

## 3. 네트워크 공격

- [ ] Sniffing
- [ ] Promiscuous Mode
- [ ] ARP Spoofing / ARP Poisoning
- [ ] IP Spoofing
- [ ] ICMP Redirect 공격
- [ ] Smurf 공격
- [ ] Ping of Death
- [ ] Land 공격
- [ ] SYN Flooding
- [ ] TCP Session Hijacking
- [ ] DNS Spoofing / DNS Cache Poisoning
- [ ] DoS와 DDoS 차이
- [ ] DRDoS / 반사·증폭 공격

공격마다 다음 네 가지를 정리한다.

`공격 원리 → 무엇이 침해되는가 → 어떻게 탐지하는가 → 어떻게 막는가`

---

## 4. 네트워크 보안 장비와 기술

- [ ] Firewall
- [ ] Packet Filtering
- [ ] Stateful Inspection
- [ ] Proxy Firewall / Application Gateway
- [ ] IDS와 IPS 차이
- [ ] HIDS와 NIDS
- [ ] 오용탐지와 이상탐지
- [ ] False Positive / False Negative
- [ ] WAF
- [ ] VPN
- [ ] IPsec
- [ ] AH와 ESP
- [ ] 터널 모드와 전송 모드
- [ ] NAC

---

## 5. 시스템 보안

### Linux

- [ ] 사용자 / 그룹 / UID / GID
- [ ] 파일 권한 rwx
- [ ] chmod / chown / chgrp
- [ ] 특수 권한 SUID / SGID / Sticky Bit
- [ ] umask
- [ ] root와 최소권한
- [ ] PAM
- [ ] 주요 로그 파일
- [ ] cron / at
- [ ] 프로세스와 서비스
- [ ] 불필요 서비스 제거

### Windows

- [ ] SID
- [ ] NTFS 권한
- [ ] 공유 권한
- [ ] 레지스트리
- [ ] 이벤트 로그
- [ ] 계정 정책

---

## 6. 악성코드와 시스템 공격

- [ ] Virus
- [ ] Worm
- [ ] Trojan Horse
- [ ] Ransomware
- [ ] Rootkit
- [ ] Backdoor
- [ ] Logic Bomb
- [ ] Bot / Botnet
- [ ] Keylogger
- [ ] Buffer Overflow
- [ ] Format String
- [ ] Race Condition
- [ ] Privilege Escalation

---

## 7. 웹 / 애플리케이션 보안

웹 공격은 반드시 예시 요청과 함께 이해한다.

- [ ] HTTP 기본 구조
- [ ] Cookie와 Session
- [ ] Same-Origin Policy
- [ ] SQL Injection
- [ ] XSS
  - [ ] Stored XSS
  - [ ] Reflected XSS
  - [ ] DOM XSS
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

---

## 8. 암호학 기초

- [ ] 평문 / 암호문 / 키
- [ ] Kerckhoffs's Principle
- [ ] 대칭키 암호
- [ ] 비대칭키 암호
- [ ] 대칭키와 공개키 방식 비교
- [ ] 블록암호와 스트림암호
- [ ] DES / 3DES / AES
- [ ] RSA
- [ ] Diffie-Hellman
- [ ] ECC
- [ ] 해시 함수
- [ ] MD5 / SHA 계열
- [ ] Salt
- [ ] HMAC

---

## 9. 전자서명과 PKI

- [ ] 전자서명의 목적
- [ ] 무결성 / 인증 / 부인방지와의 관계
- [ ] 공개키와 개인키 사용 방향
- [ ] 인증서 Certificate
- [ ] CA / RA
- [ ] PKI
- [ ] CRL
- [ ] OCSP
- [ ] 인증서 체인
- [ ] TLS / HTTPS 기본 흐름

---

## 10. 접근통제

- [ ] 식별 Identification
- [ ] 인증 Authentication
- [ ] 인가 Authorization
- [ ] 책임추적성 Accountability
- [ ] DAC
- [ ] MAC (Mandatory Access Control)
- [ ] RBAC
- [ ] ABAC
- [ ] Bell-LaPadula
- [ ] Biba
- [ ] Clark-Wilson

주의: `MAC`은 문맥에 따라 MAC Address, Message Authentication Code, Mandatory Access Control이 모두 될 수 있다.

---

## 11. 보안 관리

- [ ] 자산 / 위협 / 취약점 / 위험
- [ ] 위험 분석
- [ ] 정성적 / 정량적 위험분석
- [ ] 위험 회피 / 감소 / 전가 / 수용
- [ ] 보안 정책 / 지침 / 절차
- [ ] BCP
- [ ] DRP
- [ ] RTO / RPO
- [ ] 백업 종류
- [ ] 사고 대응 절차
- [ ] 디지털 포렌식 기본
- [ ] Chain of Custody

---

## 12. 법규 / 개인정보보호

이 영역은 이해보다 반복 암기가 중요하다.

- [ ] 개인정보의 개념
- [ ] 개인정보 처리 원칙
- [ ] 개인정보 수집 / 이용 / 제공
- [ ] 민감정보 / 고유식별정보
- [ ] 개인정보 파기
- [ ] 개인정보 유출 대응
- [ ] 정보보호 관련 주요 법령
- [ ] ISMS-P 기본 개념

---

## 13. 시험 직전 정리

- [ ] 자주 헷갈리는 약어 모음
- [ ] 공격기법 이름 ↔ 원리 매칭
- [ ] 암호 알고리즘 비교표
- [ ] 접근통제 모델 비교
- [ ] 주요 포트 번호
- [ ] 법규 숫자 / 기간 / 기준
- [ ] 틀린 문제만 모은 오답노트
- [ ] 실전 기출 반복

---

## 지금 다음 진도

다음 공부는 아래 순서로 진행한다.

1. **위협 / 취약점 / 위험 / 공격의 차이**
2. **보안 통제: 예방 / 탐지 / 교정**
3. **최소권한과 직무분리**
4. 이후 **네트워크 공격의 시작: Sniffing과 ARP Spoofing**

한 항목을 공부할 때마다 이 체크리스트를 체크하고, 관련 개념 노트를 별도 파일에 누적한다.
