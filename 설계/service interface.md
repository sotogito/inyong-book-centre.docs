
- SalesManagementS
	- select주문조회
	- cancleOrder
	- confiremOrder

- CancleManagementS
	- select 주문조회
	- cancleOrder
	- cancelReject

- OrderStatusChangeManager
	- cancel
	- confirm

근데 그ㅑㄴㅇ OrderManageService 하나만 두고 다 처리하는게 나을수도


- OrderManageService
	- 주문조회
	- 주문완료 -> 배송완료
	- 주문완료 -> 취소완료
	- 취소요청 -> 배송완료(거절)
	- 취소요청 -> 취소완료
