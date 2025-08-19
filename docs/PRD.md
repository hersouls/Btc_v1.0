📄 Moonwave BTC PRD v1.0 (Cursor AI + Claude CLI + Firebase/Vercel 호환성)

1. 개요

프로젝트명: Moonwave BTCs 매도지표 & 자산관리 웹서비스 (btc.moonwave.kr)

목표: 온체인 지표 기반 BTCs 점수를 활용한 분할매도 전략과 함께, 사용자의 전체 자산(코인, 주식, 금 등)을 통합 관리하고, 비중 분석·리밸런싱/자동 알림까지 지원하는 PWA 기반 앱 개발.

배포환경: Vercel + Firebase (백엔드), PWA 100% 도입

AI 분석: Claude CLI 100% 활용 (분할매도 추천, 리포트 자동화)

개발 환경: Cursor AI (IDE 기반 AI 개발 파트너), Claude CLI (분석/자동화), Firebase/Vercel 완전 호환



---

2. 주요 기능 정의

A. 온체인 분석

BTCs 점수 산출: Z-score → CDF → 백분위 변환 → 가중치 합산.

주요 지표: Realized Price, MVRV Z, SOPR, Puell Multiple, HODL Waves 등 10대 핵심 온체인 메트릭.

분석 리포트: Claude CLI를 통해 주간 시그널·위험요인·매도 전략 제안.


B. 분할매도 전략

사용자 정의 테이블: 범위별 매도 비율 직접 입력.

AI 추천 테이블: Claude CLI 분석 기반 자동 생성.

저장 옵션: LocalStorage + Firestore (멀티디바이스 동기화).


C. 자산관리 기능

보유 자산 통합 관리

암호화폐: BTC, ETH, SOL, BNB, XRP 등.

주식: 국내 (KT, CJ ENM 등), 해외 (TSLA, NFLX, SBUX 등).

원자재: 금(골드바 단위).


자산 등록/수정

수동 입력 (보유 수량, 매입가, 계좌 메모 등).

업비트 API 가격 연동 (실시간 평가액 갱신).


자산 평가/분석

총 평가액, 총 수익, 총 수익률.

일간/주간/월간 수익 차트.

종목별 상세 거래내역 (수익률, 매입가, 평가액).


비중 분석

유형별(코인/주식/현금/금) 비율 시각화.

종목별 비중 분석.



📊 첨부자료 반영 (비중 분석 화면)

코인 89.96%, 주식 6.15%, 현금 2.41%, 금 1.48% ([첨부 이미지 1])

비트코인 79.77%, 이더리움 3.46%, 아발란체 2.63%, KT 2.45%, 갈라코인 2.10%, 달러 1.90%, 금 1.48% ([첨부 이미지 2])


D. 리밸런싱 및 알림

리밸런싱 기준: BTCs 점수, 자산 비중, 목표 포트폴리오 대비 괴리율.

알림 기능 (PWA Push)

BTCs 90 진입 시 → “20% 매도 권고”

특정 자산 수익률 100% 돌파 시 → “차익 실현 권고”

포트폴리오 리스크 지수 상승 시 → “리밸런싱 필요”


자동화 확장: Webhook/텔레그램 Bot 연결 → 실시간 알림.


E. 백테스트/시뮬레이션

기간: 2012~2025 (온체인/시세 데이터 기반).

전략 테스트:

정적 분할매도 (규칙 기반).

Claude CLI 추천 전략.


결과 지표: CAGR, MDD, 샤프지수.



---

3. 기술 구조

클라이언트

Next.js (App Router)

Tailwind + Recharts 시각화

PWA 100% 지원 (오프라인 모드 + Push 알림)

LocalStorage + Firestore 동기화


서버/분석

Firebase Firestore (자산/거래/지표 데이터)

Claude CLI (AI 분석/추천)

업비트 Open API (실시간 시세)

Vercel Serverless Functions (주간 BTSs 계산, Cron 스케줄러)


DB 스키마 예시

btc_metrics_weekly: 주간 온체인 지표

btc_scores: BTCs 점수 + 리포트

user_assets: 사용자별 자산 포트폴리오

btc_sell_rules: 사용자 매도 전략 테이블

alerts: 알림 로그



---

4. 사용자 흐름 (User Flow)

1. 유저 로그인(PWA 설치)


2. 보유 자산 등록 (BTC, ETH, 금, 주식 등)


3. 대시보드에서 평가액/수익률/자산 비중 확인 (첨부 이미지 반영)


4. BTSs 점수 확인 → 알림 수신 (임계치 진입)


5. 분할매도 전략 테이블 확인 (사용자 정의 or AI 추천)


6. 필요 시 리밸런싱 실행 → 알림/보고서 저장


7. 주간 Claude CLI 리포트 확인




---

5. 확장 계획

자동 거래: 거래소 API(업비트/바이낸스) 연동 → 자동 매도

거시 지표 연동: 금리, ETF 자금 유입, 달러인덱스 추가

멀티 포트폴리오: 가족 계정/기업 계정 분리 관리



---

✅ v3.2는 Cursor AI + Claude CLI를 메인 개발/분석 워크플로로 설정하고, Firebase와 Vercel 호환성을 최적화한 실전 배포 설계입니다.

