### 열거형
- Java 1.5 버전부터 도입되었다.
- 연관된 상수들의 집합. Java 에서는 **final** 과 다름 없음. (고정값 == 상수)
- 고정된 상수값으로, 타입 안정성이 보장됨. ( new 인스턴스 생성 불가. )
- 싱글톤(singleton) 방식

```java

public class a {
	public static void main(String[] args){
		
		System.out.println(3 * Ex02Enum.UK.getRefundTax());  // 3.6
  
		Ex02Enum a = Ex02Enum.KOREA;  
		
		System.out.println(a.getTax());  // 1.1
		System.out.println(a.getRefundTax()); // 1.0
	}

}

public enum Ex02Enum {  
    KOREA(82,1.1f),  
    USA(1,1.2f),  
    UK(44,1.3f),  
    ETC(0,.15f);  
  
    private final int code;  
    private final float tax;  
  
    Ex02Enum (int code , float tax) {  
        this.code = code;  
        this.tax = tax;  
    }  
    public float getRefundTax() {  
        float refundTax = tax;  
  
        if(code != 0) refundTax = tax - 0.1f;  
  
        return refundTax;  
    }  
    public float getTax(){  
        return tax;  
    }  
}


```