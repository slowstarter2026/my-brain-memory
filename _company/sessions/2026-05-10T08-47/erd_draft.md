# 구매대행 통합 솔루션 ERD 초안

## 1. 엔티티 정의 (Entities)

### A. Agent (에이전트)
*   `agent_id` (PK): 에이전트 고유 ID
*   `name`: 에이전트 이름
*   `contact_info`: 연락처 정보
*   `status`: 활성화/비활성화 상태
*   `integration_key`: 외부 API 키 또는 인증 토큰 (보안 처리 필수)

### B. Product (상품)
*   `product_id` (PK): 상품 고유 ID
*   `name`: 상품명
*   `description`: 상세 설명
*   `base_cost`: 원가 (Agent로부터 받은 비용 기준)
*   `selling_price`: 판매 가격 (쇼핑몰 등록 가격)
*   `status`: 활성/비활성

### C. SourceLink (소스 링크)
*   `link_id` (PK): 링크 고유 ID
*   `product_id` (FK): 연결된 상품 (Product 테이블 참조)
*   `agent_id` (FK): 소스 에이전트 (Agent 테이블 참조)
*   `source_url`: 실제 상품 URL
*   `scraper_config`: 스크래핑/API 호출 설정 정보

### D. Order (주문)
*   `order_id` (PK): 주문 고유 ID
*   `product_id` (FK): 주문된 상품
*   `agent_id` (FK): 해당 주문의 원천 에이전트
*   `quantity`: 주문 수량
*   `total_amount`: 총 결제 금액
*   `status`: 주문 상태 (Pending, Paid, Shipped, Canceled)
*   `created_at`: 생성 시간

### E. TransactionLog (거래 로그)
*   `log_id` (PK): 로그 고유 ID
*   `order_id` (FK): 연결된 주문 (Order 테이블 참조)
*   `timestamp`: 발생 시점
*   `action`: 수행된 작업 (e.g., 'API_FETCH', 'PRICE_UPDATE', 'ORDER_CREATE')
*   `details`: 상세 결과 또는 에러 메시지

### F. PricingRule (가격 규칙)
*   `rule_id` (PK): 규칙 고유 ID
*   `product_id` (FK): 적용 대상 상품
*   `agent_id` (FK): 적용된 에이전트
*   `markup_rate`: 마진율 (%)
*   `fee_structure`: 수수료 구조 정의

## 2. 관계 요약 (Relationship Summary)

1.  **Agent** $\leftrightarrow$ **SourceLink**: 일대다
2.  **Product** $\leftrightarrow$ **SourceLink**: 일대다
3.  **Order** $\leftrightarrow$ **Product**: 일대다
4.  **Order** $\leftrightarrow$ **Agent**: 일대다
5.  **Order** $\rightarrow$ **TransactionLog**: 일대다
6.  **Product** $\leftrightarrow$ **PricingRule**: 일대다

**다음 단계:** 데이터 모델 정의가 완료되었으니, 다음 단계에서는 이 모델을 기반으로 각 엔티티에 대한 상세 스키마(PostgreSQL DDL 또는 MongoDB Schema)를 설계하고, MVP 기능 목록과 매핑하여 초기 API 엔드포인트를 구상하는 작업을 진행하겠습니다.