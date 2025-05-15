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



---
# 의문????????
dto를 공유한다는 차원이 request와 response의 공유도 해당이 되는걸까? 각각의 dto를 각각 생성해서 사용하는 로직을 많이 보았는데 분리한 이유는 있지 않을깣
dto의 설계는 과연 table단위인가 아니면 로직에 필요한 데이터를 묶기 위함인가
후자가 아닌가?!
