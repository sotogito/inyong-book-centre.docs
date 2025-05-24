예를들어 인용문고 프로젝트 상세보기 기능을 보면
주문 리스트가 뜨고 사용자 특정 주문의 row를 클릭하면 상세보기를 Ajax방식으로 띄워준다.

- SalesContoller
```java
    @ResponseBody
    @GetMapping("/orderDetail.page")
    public OrderResponseDto orderDetail(String orderId) {
        return salesService.getOrderDetailByOrderId(Integer.parseInt(orderId));
    }
```

- jsp
```html
<td class="order-detail-btn" data-id="${order.orderId}" style="text-align: center; cursor: pointer;">
    👁
</td>
```

- js
```javascript
const res = await fetch(`${contextPath}/sales/orderDetail.page?orderId=${orderId}`);
```

REST가 아닌 방식으로 구현했기 떄문에 선택된 orderId는 ?뒤에 orderId의 값으로 들어가게 된다.

다른 스프링 프로젝트를 훔쳐보면서 이 처리 방법이 다르다는 걸 느꼈는데 그 이유는 REST 처리 방식이 아니었기 때문이다.

#### REST 방식으로 바꿔보겠다

- controller
```java
@GetMapping("/orders/{orderId}")
@ResponseBody
public OrderResponseDto orderDetail(@PathVariable int orderId) {
    return salesService.getOrderDetailByOrderId(orderId);
}
```

- js
```js
const res = await fetch(`${contextPath}/sales/orders/${orderId}`);
```



즉 url의 형태는 
- REST❌ : <mark style="background: #FFF3A3A6;">`GET /sales/orderDetail.page?orderId=123`</mark>
- REST⭕️ : <mark style="background: #FFF3A3A6;">`GET /sales/orders/123`</mark>
`
