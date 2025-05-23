```
@Getter
@Setter
public class OrderResponseDto {

    private Long orderId;
    private CustomerDto customer;
    private int orderTotalCount;
    private int orderTotalPrice;
    private String payment;
    private LocalDateTime orderDate;
    private String orderStatus;
    private List<OrderDetailResponseDto> orderDetails;

    @Getter
    @Setter
    public static class CustomerDto {
        private Long id;
        private String name;
        private String phoneNumber;
        private int age;
        private String address;
        private String gender;
    }

    @Getter
    @Setter
    public static class OrderDetailResponseDto {
        private Long orderDetailId;
        private Long bookId;
        private String bookName;
        private int orderDetailTotalCount;
        private int orderDetailTotalPrice;
    }
}
```