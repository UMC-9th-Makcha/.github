# Makcha (막차) - Project README

## 1. Overview
막차/첫차 상황에서 사용자가 놓치지 않도록 **서버 스케줄링 기반으로 카카오톡 알림톡을 발송**하고,
웹에서는 **알림 상세/경로/대기 장소/리포트**를 제공하는 서비스입니다.

- 진입: 카카오톡 로그인(원클릭)
- 알림 채널: 카카오톡 **알림톡(정보성 템플릿)**
- 웹 역할: 설정/확인/상세/대시보드

> 이 문서는 팀 온보딩을 위한 요약본입니다. 상세 정책/화면은 Notion/PRD를 기준으로 합니다.

---

## 2. MVP Scope (Must Have)
1) **카카오 로그인(원클릭 진입)**
- 로그인 성공 시 사용자 식별자 확보

2) **서버 스케줄링 + 알림톡 발송**
- 브라우저 종료와 무관하게 서버가 타이밍 관리
- CTA(버튼) 클릭 시 웹 상세로 이동

3) **첫차 대기 장소 대시보드**
- 카테고리: 카페/PC방/찜질방
- 필터: 가까운순 / 24시간
- 상세: 전화하기 / 도보 길찾기

4) **카카오T 호출(보조 옵션)**
- 막차 놓침/급한 상황에서 CTA로 제공

5) **세이브 리포트(MVP)**
- 알림 내역 기반 히스토리
- 절약액은 추정치(근거 문구 포함)

---

## 3. 알림톡 메시지 템플릿(초안)
알림톡은 템플릿 기반이며, 버튼 링크는 웹으로 이동합니다.

### (1) 알림 설정 완료
- Preview: "막차 알림 설정이 완료됐어요"
- Variables: #{NAME}, #{DESTINATION}, #{DEPART_TIME}, #{ALERT_ID}
- Button: 알림 확인하기 → https://makcha.app/alerts/#{ALERT_ID}

### (2) 출발 30분 전
- Preview: "출발까지 30분 남았어요"
- Variables: #{NAME}, #{DESTINATION}, #{DEPART_TIME}, #{ALERT_ID}
- Button: 알림 확인하기 → https://makcha.app/alerts/#{ALERT_ID}

### (3) 출발 n분 전 (10~1분)
- Preview: "출발까지 n분 남았어요"
- Variables: #{NAME}, #{DESTINATION}, #{DEPART_TIME}, #{ALERT_ID}, n
- Button: 알림 확인하기 → https://makcha.app/alerts/#{ALERT_ID}

### (4) 출발 알림 (T-0)
- Preview: "지금 출발할 시간이에요"
- Variables: #{NAME}, #{DESTINATION}, #{DEPART_TIME}, #{ALERT_ID}
- Buttons:
  - 경로 확인하기 → https://makcha.app/alerts/#{ALERT_ID}/route
  - 이미 늦어서 택시부르기 → https://makcha.app/taxi?kakaoT=1&from=alert&alertId=#{ALERT_ID}

### (5) 첫차 대기 장소 안내
- Preview: "첫차까지 대기 장소를 안내해요"
- Variables: #{NAME}, #{AREA_NAME}, #{AREA_CODE}
- Button: 주변 대기 장소 확인하기 → https://makcha.app/waiting-places?area=#{AREA_CODE}

### (6) 귀가 확인 메시지
- Preview: "집에 잘 들어가셨나요?"
- Variables: #{NAME}, #{ALERT_ID}
- Buttons:
  - 네 → https://makcha.app/arrive?alertId=#{ALERT_ID}&result=public
  - 택시타고 들어갔어요 → https://makcha.app/arrive?alertId=#{ALERT_ID}&result=taxi

---

## 4. 핵심 정책(요약)
- 메시지는 **정보성 안내** 톤 유지
- 과발송 금지(리마인드/반복 발송은 최소화)
- 모든 발송은 로그로 남겨 리포트/히스토리 근거로 사용

---

## 5. Repositories
- Frontend: https://github.com/paradiseseo/umc-9th-Makcha/tree/f1442e5bc777c5edd6ea3f0de0445eb628d8e19c/Frontend
- Backend: https://github.com/paradiseseo/umc-9th-Makcha/tree/f1442e5bc777c5edd6ea3f0de0445eb628d8e19c/Backend

---

## 6. Collaboration Rules
- Issues → feature 브랜치 → PR → 리뷰 후 merge
- PR은 최소 1명 리뷰 권장
- 비밀키/토큰은 절대 커밋 금지

---

## 7. Owners
- PM: 에단/서낙원
- FE Lead: 자이/백병재
- BE Lead: 조우/김수연
