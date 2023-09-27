## 기본 정의

### Error 와 Exception

##### Error

-   에러는 프로그램 레벨에서 대비할 수 없거나 복구 불가능한 치명적인 오류를 의미
-   java.lang.Error 클래스와 그 Error 클래스를 상속받은 서브 클래스들을 말하며 주로 JVM이 발생시킴
-   에러는 JVM의 메모리가 꽉 차서 발생하는 OOM(Out Of MemoryError) 이나 스레드가 죽어서 발생하는 ThreadDeath 에러같이 try catch로 잡아도 대응할 수 없기 때문에 코드 레벨에서 처리가 불가능(개발자가 미리 예측하고 처리할 수 없음)   
##### Exception
   
-   오류가 발생했지만 대처 가능한 경우
-   Exception 클래스 및 Exception 클래스의 하위 클래스를 의미.
-   **일반 예외**(checked exception)와 **실행 예외**(runtime exception)로 나뉨

### 프로그램 오류(Error)

일반적으로 Error는 프로그램이 어떤 상황에서 예기치 못한 상황이나 원인에 의해 오작동하거나 비정상적으로 종료되는 경우를 의미하며 크게 3가지로 분리된다.

1.  **컴파일 에러**

-   소스코드의 잘못된 문법 구문이나 오타, 잘못된 자료형 사용 등에 의해 컴파일 시점에 발생하는 에러

2.  **런타임 에러**

-   컴파일이 제대로 된 이후 프로그램이 실행 중 발생하는 에러(ex. NullPointerException)

3.  **논리적 에러**

-   소스코드 레벨에서 발생하는 에러가 아닌 컴파일과 프로그램 실행상에도 문제가 없지만 개발자가 의도한 것과 다르게 동작하는 경우

### Exception Handling

##### 예외 복구

-   예외가 발생하면, 다른 작업으로 흐름 유도 **(정상 동작 유지)**
    
    ##### 예외처리 회피 (method)
    
-   예외 처리를 하지 않고, 예외를 호출한 쪽으로 던져버리는 회피방식 ( throws )
-   **주의사항** : 메소드 오버라이딩 시, Downcasting 하여 예외를 던질수 없음

##### 예외 전환 (throw new {Exception})

-   예외를 처리하지 않고 단순하게 만들기 위해 포장(wrap)하는 방법

## 프로그래밍 전략

### 예외는 정말 예외 상황에만 사용해라

-   예외를 제대로 활용한다면 가독성, 신뢰성, 유지보수성이 높아지지만 잘못 사용한다면 반대의 효과만 나타남. 그러기 때문에 예외를 효과적으로 사용해야 한다.
-   예외는 예외 상황에서만 써야 한다. **일반적인 제어 흐름용**으로 사용할 경우 **문제가 발생**한다.

### 복구할 수 있는 상황에서는 검사 예외(checked exception)를, 프로그래밍 오류에는 runtime exception을 사용하라

> 문제 상황을 알리는 타입(throwable)으로 **검사 예외**, **런타임 예외**, **에러** 를제공한다.

-   호출하는 사용자가 exception 상황을 벗어나는데 필요한 정보를 알려주는 메소드를 함께 제공하는 것이 좋음
-   구현하는 unchecked throwable은 모두 runtime exception의 하위 클래스여야 한다.
-   Error 클래스를 상속해 하위 클래스를 만드는 일은 자제(업계에 널리 퍼진 규약)
-   Exception, RuntimeException, Error를 상속하지 않는 throwable을 만들 수도 있지만 이로울 게 없으니 절대 사용 X

### 필요 없는 검사 예외(checked exception) 사용은 피하라

-   참고 : checked exception을 던지는 메소드는 스트림 안에서 직접 사용할 수 없다. 이 때문에 자바 8부터는 부담이 더 크다고 한다.
-   그렇다면 검사 예외(checked exception)와 비검사 예외(unchecked exception) 중에서 어떤 것을 선택해야 할까?

API를 제대로 사용해도 발생할 수 있거나 **개발자가 의미 있는 조치**를 할 수 있다면 **검사 예외**(checked exception)를 사용하는 것이 좋다.  
그렇지 않은 경우는 **대부분 비검사 예외**(unchecked exception)를 사용하는 게 좋다.

### checked exception을 회피하는 방법

-   이미 다른 검사 예외(checked exception)를 던지는 상황에서 또 다른 검사 예외(checked exception)를 추가할 때는 catch 문 하나만 추가하면 되지만, 새롭게 추가하거나 단 하나의 검사 예외(checked exception)를 던질 때는 고민이 된다.
-   사용자가 try 블록을 추가해야 하고, 스트림에서도 직접 사용하지 못하게 되기 때문이다.
-   그러니 검사 예외(checked exception)를 안 던지는 방법도 고민해보자.

#### 1. 적절한 결과 타입을 담은 옵셔널을 반환하라

검사 예외(checked exception)를 던지는 대신에 빈 옵셔널을 반환해보는 것이다. 단점이라면 exception이 발생한 이유를 알려주는 부가 정보를 담을 수 없다. 반면에 exception을 사용하면 구체적인 exception 타입과 그 타입에 제공하는 메소드를 활용해 부가 정보를 제공할 수 있다

-   Optional 클래스는 Java8에서 도입된 Integer나 Double 클래스처럼 'T'타입의 객체를 포장해 주는 래퍼 클래스(Wrapper class)이다. 따라서 Optional 인스턴스는 모든 타입의 참조 변수를 저장할 수 있다. 일반적으로 NullPointerException 문제를 해결하는 방법을 제공한다.
-   간단 설명 : optional 객체는 null값을 받을 수 있다.

#### 2. 검사 예외(checked exception)를 던지는 메소드를 2개로 쪼개 비검사 예외(unchecked exception)로 바꾼다.

```
//변경 전
try {
    obj.action(args);
} catch (TheCheckedException e) {
    // 예외 핸들링
}
```

```
//변경 후
if (obj.actionPermitted(args)) {
    obj.action(args);
} else {
    // 예외 핸들링
}
```

예외가 던져질지 여부를 boolean 값을 반환하는 메서드를 통해 결정하는 것이다. 조건문이 생기긴 하지만 예외에 대해 조금 더 유연하게 대처할 수 있다.

한편 변경한 코드에서 상태 검사 메서드(actionPemitted)와 상태 의존적 메서드(action) 호출 사이에서 객체의 상태가 변할 수 있기 때문에 외부 동기화 없이 **여러 스레드가 동시에 접근하는 경우**에서는 **위와 같은 리팩토링은 적절하지 않다.**

-   요약 : 우선 Optional 로 상황을 처리하려 시도하고 그것이 불가능할 때만 검사 예외(checked exception)을 사용하도록 하자

출처 :  
[자바 예외 처리](https://butter-shower.tistory.com/87)  
[자바에서 예외란?](https://dololak.tistory.com/53)  
[자바 예외 처리에 대한 작은 생각](https://www.nextree.co.kr/p3239/)  
[자바의 예외 처리](https://kingpodo.tistory.com/57)  
[자바 예외 처리 방법](https://blog.cornsworld.co.kr/m/117)