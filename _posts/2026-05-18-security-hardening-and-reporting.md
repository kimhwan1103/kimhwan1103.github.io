---
title: 웹 보안 기본기 4 - 보안 헤더와 리포트 작성
date: 2026-05-18 21:30:00 +0900
categories: [Security, Web]
tags: [web-security, security-headers, cookies, hardening, vulnerability-report]
---

# 웹 보안 기본기 4 - 보안 헤더와 리포트 작성

취약점 공부는 공격 기법을 아는 것에서 끝나지 않는다. 실제로는 어떤 방어선이 피해를 줄이는지, 어떤 운영 체계가 공격을 탐지하는지, 취약점을 발견했을 때 어떻게 설명하고 고치게 만들 것인지까지 다뤄야 한다.

## 1. 보안 헤더와 쿠키 보안 속성

보안 헤더와 쿠키 속성은 취약점을 근본적으로 없애지는 못하지만, XSS·클릭재킹·세션 탈취·다운그레이드 공격의 영향을 줄이는 중요한 방어선이다.

### CSP(Content-Security-Policy)

CSP는 허용된 스크립트 출처와 실행 방식을 제한해 XSS의 영향을 줄인다.

- `script-src`로 실행 가능한 script 출처를 제한한다.
- inline script를 줄이고 nonce/hash 기반 정책을 적용할 수 있다.
- `object-src 'none'`, `base-uri 'self'` 같은 정책으로 오래된 공격 표면을 줄일 수 있다.
- CSP는 XSS를 완전히 제거하는 장치가 아니라, XSS가 발생했을 때 실행 가능한 행동을 줄이는 방어선이다.

### HSTS(Strict-Transport-Security)

HSTS는 브라우저가 해당 도메인에 HTTPS로만 접속하도록 강제한다.

- HTTP downgrade 공격을 줄인다.
- `includeSubDomains`와 `preload`는 영향 범위가 크므로 도메인 구조를 확인한 뒤 적용해야 한다.

### X-Frame-Options / frame-ancestors

클릭재킹 방지를 위해 다른 사이트의 iframe 삽입을 제한한다.

- 오래된 방식은 `X-Frame-Options: DENY` 또는 `SAMEORIGIN`이다.
- CSP를 사용한다면 `frame-ancestors`가 더 유연하다.

### X-Content-Type-Options

브라우저의 MIME sniffing을 제한해 의도하지 않은 스크립트 실행을 줄인다.

```http
X-Content-Type-Options: nosniff
```

### Cookie 속성

쿠키는 인증 상태와 직접 연결되므로 속성을 상황에 맞게 설정해야 한다.

- `HttpOnly`: JavaScript에서 쿠키를 읽지 못하게 해 XSS 상황의 쿠키 탈취를 어렵게 한다.
- `Secure`: HTTPS 연결에서만 쿠키를 전송한다.
- `SameSite`: 교차 사이트 요청에서 쿠키가 자동 첨부되는 범위를 제한한다.
- `Domain`, `Path`: 쿠키가 전송되는 범위를 최소화한다.
- 만료시간: access token과 session cookie의 만료 정책을 명확히 정한다.

## 2. 기본 방어 원칙

- 입력 검증: 입력이 기대한 형식, 범위, 길이인지 검증한다.
- 출력 인코딩: HTML, attribute, JavaScript, URL 등 출력 문맥에 맞게 인코딩한다.
- 파라미터 바인딩: SQL, shell, template 같은 해석 문맥에 사용자 입력을 문자열 결합으로 넣지 않는다.
- 최소 권한: DB 계정, 파일 시스템 권한, 클라우드 IAM 권한을 필요한 만큼만 준다.
- 안전한 기본값: 인증 필요, 외부 공개 안 함, 위험 기능 비활성화 같은 기본값을 택한다.
- 비밀정보 분리: secret, API key, token을 코드와 로그에 남기지 않는다.
- 에러 메시지 제한: 내부 경로, SQL, stack trace가 사용자에게 노출되지 않게 한다.

## 3. 운영 방어

개발 단계의 방어만으로는 충분하지 않다. 실제 서비스에서는 공격을 탐지하고, 영향을 줄이고, 복구할 수 있는 운영 체계가 필요하다.

- 로깅: 인증 실패, 권한 거부, 관리자 기능 사용, 비정상 요청을 기록한다.
- 감사 추적: 누가 어떤 리소스를 언제 변경했는지 추적할 수 있어야 한다.
- Rate limiting: 로그인, 비밀번호 재설정, 검색, 파일 업로드 같은 기능에 요청 제한을 둔다.
- 알림: 반복 실패, 권한 상승 시도, SSRF 의심 요청, 대량 다운로드 같은 이벤트를 감지한다.
- 백업: 랜섬웨어나 데이터 삭제 사고에 대비해 복구 가능한 백업을 유지한다.
- 패치 관리: 프레임워크, 라이브러리, OS 패키지의 보안 업데이트를 추적한다.
- 의존성 취약점 점검: Dependabot, npm audit, bundler-audit, Trivy 같은 도구로 알려진 취약점을 확인한다.

## 4. 취약점 리포트 작성

취약점 리포트는 단순히 "뚫린다"를 말하는 문서가 아니다. 재현 조건, 영향도, 원인, 패치 방향을 설명해 개발자가 실제로 고칠 수 있게 만드는 문서다.

좋은 리포트는 보통 다음 순서로 정리한다.

1. 요약: 어떤 취약점인지 한 문단으로 설명한다.
2. 영향도: 어떤 데이터나 기능이 영향을 받는지 설명한다.
3. 재현 조건: 필요한 계정, 권한, 환경, URL을 적는다.
4. 재현 절차: 요청/응답, 파라미터, 화면 흐름을 단계별로 적는다.
5. 원인 분석: 어떤 검증이 누락됐는지, 어떤 설계가 문제인지 설명한다.
6. 패치 제안: 서버 측 권한 검증, 입력 검증, 인코딩, 설정 변경 같은 방향을 제안한다.
7. 참고 자료: OWASP, MDN, 벤더 문서 등 신뢰 가능한 자료를 붙인다.

## 5. 학습 기준

취약점을 발견하는 것만으로는 부족하다. 왜 발생했는지, 어떤 코드나 설계가 원인인지, 어떻게 막을 수 있는지까지 설명할 수 있어야 실무적인 의미가 생긴다.

공부할 때는 다음 질문을 계속 붙이면 좋다.

- 이 취약점은 어떤 신뢰 경계가 깨져서 발생했는가?
- 사용자 입력이 서버 내부에서 어떤 문맥으로 해석되는가?
- 인증과 인가 중 어느 검증이 빠졌는가?
- 이 취약점의 영향은 데이터 노출인가, 상태 변경인가, 코드 실행인가?
- 근본 패치와 완화 조치는 각각 무엇인가?

## 참고 자료

- [MDN - Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Same-origin_policy)
- [MDN - CORS configuration](https://developer.mozilla.org/en-US/docs/Web/Security/Practical_implementation_guides/CORS)
- [OWASP - Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)
- [OWASP - JSON Web Token Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.html)
- [OWASP - Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [OWASP - Cross-Site Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
- [OWASP - Server-Side Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
- [OWASP - File Upload Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)
