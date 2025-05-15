- 데이터의 구조보다, 목적에 맞게 생성하기
- DTO의 공유란, 테이블의 구조나 엔티티가 아닌, 특정 행동의 응답 구조를 재사용하는 것이다.
---
- **CustomerDto**
	- id
	- name
	- phoneNumber
	- age
	- address
	- gender

- **OrderRequestFilterDto** : 주문 조회를 위한 필터(동적 쿼리)
	- orderId
	- userId
	- orderStatus
	- startDate
	- endDate

- **OrderStatusUpdateRequestDto**(record)
	- orderId
	- orderStatus
	
- **OrderSimpleResponseDto** : 주문 조회
	- orderId
	- userId
	- orderTotalCount
	- orderTotalPrice
	- payment
	- orderDate
	- orderStatus

- **OrderResponseDto** : 주문 상세페이지 결과 - 주문 1개
	- orderId
	- **CustomerDto**
	- orderTotalCount
	- orderTotalPrice
	- payment
	- orderDate
	- orderStatus
	- List\<**OrderDetailResponseDto**\> 
	
- **OrderDetailResponseDto**
	- orderDetailId
	- bookId
	- bookName
	- orderDetailTotalCount
	- orderDetailTotalPrice

- BookInventoryupdateRequestDto
	- bookId
	- updateQuantity

---
```
#### ❌ 잘못된 예시:
`OrderDto` 하나로 아래 모든 기능에 사용함
- 주문 생성 요청 (`POST /orders`)
- 주문 목록 조회 (`GET /admin/orders`)
- 월별 주문 통계 응답 (`GET /stats/orders`)
    

→ 구조는 같을 수 있지만, **용도와 맥락이 다름**, 불필요한 필드 포함되거나 누락될 가능성 큼

#### ✅ 바른 예시:
- `OrderCreateRequestDto` → 주문 등록 요청용
- `OrderResponseDto` → 주문 단건 조회 응답용
- `OrderStatsDto` → 통계용 응답
```

```
#### ✅ 올바른 공유 예시:

`OrderDetailResponseDto`는 "주문 상세 정보를 화면에 보여주기 위한" 목적의 DTO
- 관리자 주문관리 페이지에서 `주문 상세 보기
- 사용자 마이페이지에서 `내 주문 상세 보기`
    

→ **기능은 다르지만, 보여주는 목적은 동일**하므로 같은 DTO를 공유해도 무방함

#### ❌ 잘못된 공유 개념:
"어차피 주문 관련이니까 OrderDto 하나로 다 쓰자"
```


---
# 의문
목적성에 따라서 dto를 너무 만들면 dto각 너무 많이 생성되는 것이 아닌가?