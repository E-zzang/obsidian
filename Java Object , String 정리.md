## Object

### 기본 클래스, 클래스의 부모

- clone() : `객체의 복사본을 반환` / `protected 이기 때문에 public 으로 오버라이딩`
- equals() : `같은 객체 비교`
- ~~finalize() : `특정 객체에 대한 참조가 더 이상 없다고 판단할 때 가비지 컬렉션이 객체의 finalize를 호출한다`~~ (사용을 권장하지 않음)
- getClass() : `클래스 정보를 담고있는 class 인스턴스를 반환`
- hashCode() : `객체 자신의 해시코드 반환`
- toString() : `객체 자신의 정보를 문자열로 반환`
- notfy() / notifyAll() / wait() : `쓰레드 관련 메서드`

## Objects
### Java 7에서 추가된 유틸리티 클래스
Objects 클래스는 null-safe한 메서드들을 제공하여, 객체 비교, null 처리 등에 편리하게 사용할 수 있도록 합니다.

Objects 클래스에서 제공하는 메서드에는 requireNonNull(), equals(), hash(), toString() 등이 있습니다.


[finalize 참고](https://camel-context.tistory.com/43)