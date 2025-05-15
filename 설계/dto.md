- **OrderRequestFilterDto** : 주문 조회를 위한 필터(동적 쿼리)
	- orderId
	- userId
	- orderStatus
	- startDate
	- endDate

- **OrderResponseDto**
	- orderId
	- userId
	- orderTotalCount
	- orderTotalPrice
	- payment
	- orderDate
	- orderStatus

- **OrderDto**
	- orderId
	- **CustomerDto**
	- orderTotalCount
	- orderTotalPrice
	- payment
	- orderDate
	- orderStatus
	- List\<**OrderDetailDto**\>

- **OrderDetailDto**
	- orderDetailId
	- orderId
	- **BookDto** (얘는...그냥 필요한 필드만?)
	- orderDetailTotalCount
	- orderDetailTotalPrice
- **CustomerDto**
	- id
	- name
	- phoneNumber
	- age
	- address
	- gender
---
아니면 상세 조회시 따로 가져오기
- OrderDetailRsponseDto
	- orderDetailId
	- cutomerId
	- cutomerName
	- cutomerPhone
	- cutomerAddress
	- orderStatus
	- payment
	- orderTotalCount
	- orderTotalPrice
	- List<

	- bookId
	- bookName


	- OrderDto > List\<OtderDetailDto\>
	- 
	- cutomerId
	- cutomerName
	- cutomerPhone
	- cutomerAddress
	- bookId
	- bookName

그니까 조회와 등록을 한번에 생각한 DTO를 설계해야할지 - OrderDto
response만 생각할지 - OrderDetailRsponseDto