#### 주문 관리
- **OrderRequestFilterDto** : 주문 조회를 위한 필터 (동적 쿼리)
	- startDate
	- endDate
	- orderStatus
	- orderId
	- userId
	
- **OrderResponseDto** : 주문
	- orderId
	- userId
	- orderDate
	- orderStatus
	- payment
	- orderTotalCount
	- orderTotalPrice
	
- **OrderDto**
	- orderId
	- **CustomerDto**
	- orderDate
	- orderStatus
	- payment
	- orderTotalCount
	- orderTotalPrice
	- List\<**OrderDetailDto**\>
- **OrderDetailDto**
	- orderDetailId
	- orderId
	- bookId
	- orderDetailTotalCount
	- orderDetailTotalPrice
- **CustomerDto**







- ~~count(Response)Dto

#### 취소 관리
- ~~CancelOrderRequestFilterDto (그냥 OrderRequestFilterDto도 ㄱㅊ을듯)~~
---
주문에 대하여 상태를 변경하는 로직은 Enum을 사용하여 모듈로. 변경하고싶은 Enum과 같이 넘겨서 그거에 따라서 처리 update.enum.getValue
- orderId + enum.getValue()

#### 주문 상세 조회 - SELECT
OrderResponseDto -> 선택된orderId -> OrderDto

#### 주문 상태 변경 - UPDATE
OrderResponseDto -> 선택된 orderId + 변경값Enum -> 결과





 - 재고 차감은 언제? 주문완료가 되면 배송차감
 - 배송완료는 유지
 - 만약 취소일 경우 되돌리기?