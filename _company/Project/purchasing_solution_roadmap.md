# 🚀 구매대행 통합 솔루션 프로젝트 로드맵 (v1.0)
## ✨ 목표: MVP 출시 및 안정화된 운영 시스템 구축

### 🎯 핵심 원칙
1.  **데이터 우선:** 모든 기능은 'SourceLink' $\to$ 'Product' $\to$ 'SKU' $\to$ 'Inventory'의 데이터 흐름을 중심으로 설계되어야 함.
2.  **트랜잭션 무결성:** 주문(Order)과 재고(Inventory) 기록 시, 원본 에이전트의 데이터를 반드시 백업/추적해야 함.

### 🏗️ 프로젝트 단계별 목표 (Milestones)

#### Phase 1: 설계 완료 (현재 상태 - Done)
*   **산출물:** 데이터 모델 ERD 초안 및 최적화 가이드 완성.
*   **결과:** 시스템이 관리할 모든 데이터의 구조 정의.

#### Phase 2: 기술 스펙 확정 (Next Focus!)
*   **목표:** 구매대행 워크플로우(Workflow)를 단계별로 분해하고, 각 단계를 처리하는 **API 사양(Specification)**을 확정합니다.
*   **주요 작업:**
    1.  **구매 대행 흐름 도식화 (Flowchart):** [Agent Source] $\to$ [Scraping/API Call] $\to$ [Data Parsing/Normalization] $\to$ [DB Write: Product & Inventory] $\to$ [Admin Review].
    2.  **핵심 API 정의:** `GET /products/{product_id}/details` (실시간 가격 조회), `POST /order/create` (주문 생성).
*   **산출물:** 최종 API Endpoint 목록 및 요청/응답 데이터 스키마 명세서.

#### Phase 3: 백엔드 코어 개발
*   **목표:** 확정된 API 스펙을 바탕으로 핵심 비즈니스 로직(구매대행 원가 계산, 주문 상태 변화 등) 구현.
*   **주요 작업:** DB 연동 및 트랜잭션 관리 모듈 개발.

#### Phase 4: 사용자 인터페이스 (UI/UX) 구축 및 통합 테스트
*   **목표:** 내부 관리자 페이지(Dashboard)와 외부 쇼핑몰 판매 채널의 연결 완성.
*   **주요 작업:** 시각화된 데이터 대시보드, 알림 시스템 구현 등.

---
**[다음 행동 계획]**
1.  Developer: Phase 2 목표 달성을 위해 '구매대행 워크플로우 Flowchart' 초안을 작성해 주세요. (기술적 관점)
2.  영숙: Flowchart를 받아 비즈니스/사용자 시나리오 측면에서 검토하고, 개발 우선순위를 재조정하여 다음 주까지 최종 보고서 형태로 정리하겠습니다.