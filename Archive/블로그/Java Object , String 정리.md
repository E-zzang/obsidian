## Object

### 기본 클래스, 클래스의 부모

- clone() : `객체의 복사본을 반환` / `protected 이기 때문에 public 으로 오버라이딩`
- equals() : `같은 객체 비교`
- ~~finalize() : `특정 객체에 대한 참조가 더 이상 없다고 판단할 때 가비지 컬렉션이 객체의 finalize를 호출한다`~~ (API Decreted 되어, cleaner가 대안이 되었지만, 이 또한 사용되지 않음)
- getClass() : `클래스 정보를 담고있는 class 인스턴스를 반환`
- hashCode() : `객체 자신의 해시코드 반환`
- toString() : `객체 자신의 정보를 문자열로 반환`
- notfy() / notifyAll() / wait() : `쓰레드 관련 메서드`

## Objects
### Java 7에서 추가된 유틸리티 클래스
Objects 클래스는 null-safe한 메서드들을 제공하여, 객체 비교, null 처리 등에 편리하게 사용할 수 있도록 합니다.

Objects 클래스에서 제공하는 메서드에는 requireNonNull(), equals(), hash(), toString() 등이 있습니다.

## String

### 사용 빈도가 높은 10가지 메소드

| **리턴 타입** | **메소드 이름(매개 변수)**                             | **설명**                                                               |
| ------------- | ------------------------------------------------------ | ---------------------------------------------------------------------- |
| char          | charAt(int index)                                      | 특정 위치의 문자를 리턴합니다.                                         |
| boolean       | equals(Object anObject)                                | 두 문자열을 비교합니다.                                                |
| byte[]        | getBytes()                                             | byte[]로 리턴합니다.                                                   |
| byte[]        | getBytes(Charset charset)                              | 주어진 문자셋으로 인코딩한 byte[]로 리턴합니다.                        |
| int           | indexOf(String str)                                    | 문자열 내에서 주어진 문자열의 위치를 리턴합니다.                       |
| int           | length()                                               | 총 문자의 수를 리턴합니다.                                             |
| String        | replace(CharSequence target, CharSequence replacement) | target 부분을 replacement로 대치한 새로운 문자열을 리턴합니다.         |
| String        | substring(int beginIndex)                              | beginIndex 위치에서 끝까지 잘라낸 새로운 문자열을 리턴합니다.          |
| String        | substring(int beginIndex, int endIndex)                | beginIndex 위치에서 endIndex 전까지 잘라낸 새로운 문자열을 리턴합니다. |
| String        | toLowerCase()                                          | 알파벳 소문자로 변환한 새로운 문자열을 리턴합니다.                     |
| String        | toUpperCase()                                          | 알파벳 대문자로 변환한 새로운 문자열을 리턴합니다.                     |
| String        | trim()                                                 | 앞뒤 공백을 제거한 새로운 문자열을 리턴합니다.                         |
| String        | valueOf(int i)  <br>valueOf(double d)                  | 기본 타입 값을 문자열로 리턴합니다.                                    |


기본적으로 Java 에서 String 으로 선언을 할 때, 문자열 리터럴이 동일하다면 동일한 String 객체를 참조합니다.

하지만, new 연산자로 생성할 경우, 다른 객체를 참조합니다.

```java
	String s1 = "비교";
	String s2 = "비교";
	
	System.out.println(s1 == s2); // true

	String s3 = new String("비교");
	String s4 = new String("비교");

	System.out.println(s3 == s4); // false
	System.out.println(s3.equlas(s4)); // true

```

[기본 타입 참고](https://log-back.tistory.com/16)



## 참고한 블로그

[finalize 참고](https://camel-context.tistory.com/43)
[String 메서드 참고](https://hongong.hanbit.co.kr/java-%EC%9E%90%EB%B0%94-%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%84-%EB%8B%A4%EB%A3%A8%EB%8A%94-string-%ED%81%B4%EB%9E%98%EC%8A%A4-%EB%A9%94%EC%86%8C%EB%93%9C-%EC%B4%9D%EC%A0%95%EB%A6%AC/)