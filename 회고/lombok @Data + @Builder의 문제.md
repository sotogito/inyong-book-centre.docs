주문 관리 기능에서 주문하나를 수락하게되면 주문 상태를 업데이트하고, 정산에 데이터를 추가해야한다.

그래서 정산쪽과 같이 해야하는 로직이었다.
내가 사용해야할 처음 DTO의 형태는 아래와 같았다.
```java
@Data
public class SettlementDto {

    private int stId; // 정산 ID
    private int orderId; // 주문 ID
    private LocalDate stDate; // 정산기준일
    private LocalDate exDate; // 정산예정일
    private LocalDate compDate; // 정산완료일
    private int stPrice; // 정산금
    private String stStatus; // 정산상태 (VARCHAR(15))
    private int tax; // 결제수수료
}
```
사용해야할 필드가 성택적이라 빌더가 필요하여 @Builder 어노테이션을 추가하였다.

로직을 완성하고 커밋푸시를하고 dev에서 pull을 받고 merge를 했다.
헌데,..........정산로직에서 데이터가 출력되지 않는 문제가 발생하였다.

문제는!!!!!!!!!!!!!!!!!! 데이터+빌더를 동시에 사용했기 때문이다.

@Data가 자동으로 만들어주는 메서드는 다음과 같다
- getter/setter
- toString()
- equals()hashCode()


헌데 빌더패턴을 보면, 마지막에 .Build()메서드를 호출하면서 매개변수 생성자를 필요로한다.
하지만 생성자를 어노테이션을 생성하지 않아서 오류가 났던것이다.

생성자 어노테이션을 추가하고 문제는 해결되었다.
```
@Data
@NoArgsConstructor
@AllArgsConstructor
@Builder
```