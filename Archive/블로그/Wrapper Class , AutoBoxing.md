## wrapper

### Wrapper Class 란?

`기본 타입에 해당하는 데이터를 객체(참조형)로 포장해 주는 클래스를 래퍼 클래스(Wrapper class)라고 합니다. 각각의 타입에 해당하는 데이터를 인수로 전달받아, 해당 값을 가지는 객체로 만들어 줍니다. 래퍼 클래스는 모두 java.lang 패키지에 포함되어 있습니다.`

[기본 타입 참고](https://log-back.tistory.com/16)

|기본 타입|래퍼 클래스|
|---|---|
|byte|Byte|
|short|Short|
|int|**Integer**|
|long|Long|
|float|Float|
|double|Double|
|char|**Character**|
|boolean|Boolean|

Wrapper 로 생성된 인스턴스에 경우, == (동등 연산자) 를 통해 비교를 하게 될 경우 저장 된 값이 아닌 주소 값에 대해서 비교를 하게 되어 원하는 결과가 나오지 않는다. 

해당 값을 비교하려고 할 경우  o1.**equals**(o2) 메소드를 사용하여 비교하도록 한다.

### 사용 이유

1. 객체 또는 클래스가 제공하는 메소드 사용 ( Null 값 사용 )
2. 숫자 , 문자로서의 형 변환


## AutoBoxing / AutoUnBoxing

### AutoBoxing 이란?

`Java Compiler 가 연산 시 기본 자료형에 대해서, 래퍼클래스로 변형해주는 것`

`JDK 1.5부터는 자바 컴파일러가 박싱과 언박싱이 필요한 상황에 자동으로 처리를 해준다.`

```java
Integer num = new Integer(17); // 박싱
// new 메소드 보다는 , Integer.valueOf(17)  을 선호한다.

int n = num.intValue();        // 언박싱

System.out.println(n);         // 17


Character ch = 'X'; // Character ch = new Character('X'); : 오토박싱

char c = ch;        // char c = ch.charValue();           : 오토언박싱

System.out.println(c);  // X
```



## 참고 자료
[tcp_school](http://www.tcpschool.com/java/java_api_wrapper)
