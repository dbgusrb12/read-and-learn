# 02. 객체지향 프로그래밍 패러다임

## 2.1 객체지향이란 무엇인가?

객체지향 프로그래밍은 프로그래밍 패러다임 또는 프로그래밍 스타일을 의미한다.  
코드를 구성하는 기본 단위로 클래스 또는 객체를 사용하고, 코드 설계와 구현의 초석으로 캡슐화, 추상화, 상속, 다형성의 4가지 특성을 사용한다.

객체지향 프로그래밍 언어는 클래스 또는 객체 문법을 지원하며, 이 문법은 객체지향 프로그래밍의 4가지 특성을 쉽게 구현할 수 있다.

## 2.2 캡슐화, 추상화, 상속, 다형성이 등장한 이유

### 캡슐화

`캡슐화 (encapsulation)`는 정보 은닉 또는 데이터 액세스 보호라고도 하는데,  
접근 가능한 인터페이스를 제한하여 클래스가 제공하는 메서드를 통해서만 내부 정보나 데이터에 대한 외부 접근을 허가 하는 것을 뜻한다.

금융 시스템에서 사용자의 가상 통화 금액을 기록하기 위해 사용자마다 가상 지갑을 생성한다고 가정해보자.

```java
public class Wallet {

    private String id;
    private long createTime;
    private BigDecimal balance;
    private long balanceLastModifiedTime;


    public Wallet() {
        this.id = IdGenerator.getInstance().generate();
        this.createTime = System.currentMillis();
        this.balance = BigDecimal.ZERO;
        this.balanceLastModifiedTime = System.currentMillis();
    }

    public String getId() {
        return this.id;
    }

    public long getCreateTime() {
        return this.createTime;
    }

    public BigDecimal getBalance() {
        return this.balance;
    }

    public long getBalanceLastModifiedTime() {
        return this.balanceLastModifiedTime;
    }

    public void increaseBalance(BigDecimal increasedAmount) {
        if (increasedAmount.compareTo(BigDecimal.ZERO) < 0) {
            throw new InvalidAmountException("...");
        }
        this.balance.add(increasedAmount);
        this.balanceLastModifiedTime = System.currentMillis();
    }

    public void decreaseBalance(BigDecimal decreasedAmount) {
        if (decreasedAmount.compareTo(BigDecimal.ZERO) < 0) {
            throw new InvalidAmountException("...");
        }
        if (decreasedAmount.compareTo(this.balance) > 0) {
            throw new InsufficientAmountException("...");
        }
        this.balance.subtract(decreasedAmount);
        this.balanceLastModifiedTime = System.currentMillis();
    }
}
```

Wallet 클래스는 멤버 변수로 다음과 같은 데이터를 가지고 있다.

- `id`: 지갑의 고유 번호
- `createTime`: 지갑이 생성된 시간
- `balance`: 지갑의 잔액
- `balanceLastModifiedTime`: 지갑의 잔액이 마지막으로 변경된 시간

캡슐화 특성을 통해 Wallet 클래스는 위의 데이터에 직접 접근하는 것을 제한하고, 다음과 같은 메서드를 통해 데이터에 접근하거나 값을 변경 할 수 있다.

- `String getId()`
- `long getCreateTime()`
- `BigDecimal getBalance()`
- `long getBalanceLastModifiedTime()`
- `void increaseBalance(BigDecimal increasedAmount)`
- `void decreaseBalance(BigDecimal decreasedAmount)`

비즈니스 관점에서 `id`, `createTime` 속성은 지갑 생성 시 결정되며 그 이후에는 변경하지 않아야 하기 때문에 Wallet 클래스에서 `id`, `createTime` 을 변경하는 어떠한 메서드도 제공하지 않는다.  
또한, Wallet 클래스를 호출하는 입장에서는 `id`와 `createTime` 속성의 초기화는 투명하게 진행되어야 하므로, 생성자에서 초기화를 위한 어떠한 매개변수나 할당 없이 Wallet 클래스 생성자 내부에서 초기화한다.

`balance` 속성은 증가/감소하는 경우만 존재하며, 재설정 되어서는 안되기 때문에 `increaseBalance()`, `decreaseBalance()` 외의 어떤 setter 메서드도 제공하지 않는다.  

`balanceLastModifiedTime` 속성은 잔액이 수정될 때만 함께 변경되기 때문에 해당 속성의 변경을 `increaseBalance()`, `decreaseBalance()` 메서드로 캡슐화 하고,  
이 속성을 수정하기 위한 방법과 비즈니스 세부 정보를 노출하지 않음으로써 `balance`, `balanceLastModifiedTime` 속성이 같은 시기에 변경되었음을 보장할 수 있게된다.

클래스의 속성에 대한 접근을 제한하지 않으면 속성이 여러 이상한 방식으로 수정될 수 있고, 수정 논리가 코드의 모든 구석에 흩어져 코드의 가독성과 유지 관리 용이성에 영향을 줄 수 있다.  
예를 들어 비즈니스 논리를 이해하지 못한 채 특정 코드에서 지갑의 `balanceLastModifiedTime` 속성을 변경하고 `balance` 속성을 변경하지 않는다면,  
결국 `balance`와 `balanceLastModifiedTime` 속성이 가지는 의미가 일치하지 않게 된다.

속성을 캡슐화하고 몇 가지 필요한 메서드만 노출하면 모든 비즈니스 세부 정보를 완벽하게 이해하지 않아도 잘못 사용할 가능성이 크게 줄어든다.  
기능을 단순화하고 정리하는 것만으로도 학습 비용이 많이 줄어들고 오류 확률도 낮아진다.

### 추상화

캡슐화가 정보를 숨기고 데이터를 보호하는 반면, `추상화 (abstraction)`는 메서드의 내부 구현을 숨기는 것을 의미한다.  
따라서 클래스를 사용할 때 기능의 구현 방식에 대해 고민하지 않고, 메서드가 제공하는 기능에만 집중할 수 있다.

Java 에서는 `interface` 키워드와 `abstract` 키워드 두가지 문법으로 추상화 특성을 구현한다.

다음은 Java 의 인터페이스 구문을 활용하여 추상화 속성을 구현한 코드다.

```java
public interface PictureStorage {
    
    void savePicture(Picture picture);
    
    Image getPicture(String pictureId);
    
    void deletePicture(String pictureId);
    
    void modifyMetaInfo(String pictureId, PictureMetaInfo metaInfo);
}

public class DefaultPictureStorage implements PictureStorage {
    
    // 생략

    @Override
    public void savePicture(Picture picture) {...}

    @Override
    public Image getPicture(String pictureId) {...}

    @Override
    public void deletePicture(String pictureId) {...}

    @Override
    public void modifyMetaInfo(String pictureId, PictureMetaInfo metaInfo) {...}
}
```

이미지 저장 기능을 사용할 때는 인터페이스 클래스인 `PictureStorage` 클래스에 의해 노출되는 메서드만 알면 되며, `PictureStorage` 클래스의 구현에 대해서 확인할 필요가 없게 된다.

함수를 사용할 때 해당 함수가 내부적으로 어떻게 동작하는지 굳이 알지 않아도 함수의 이름과 인자, 반환값 등을 주석 또는 문서를 통해 확인할 수 있다면 바로 사용할 수 있다.

추상화와 캡슐화는 더 높은 수준으로 올라가면 인간이 복잡한 시스템을 다룰 수 있게 해주는 효과적인 수단이다.  
복잡한 시스템에 직면했을 때 인간의 두뇌가 견딜 수 있는 한계가 제한적이기 때문에 중요하지 않은 세부 정보는 무시해야 한다.  
구현이 아닌 기능에만 초점을 맞춘 설계 사상인 추상화는 뇌가 불필요한 많은 정보를 걸러내는 데 도움이 된다.

클래스의 메서드를 정의하거나 이름을 붙일 때는 추상적인 사고가 필요하다.  
메서드의 정의를 수정할 필요가 없을 때 메서드의 정의를 변경해야 한다.

### 상속

`상속 (inheritance)`은 `고양이는 포유류의 일종이다` 처럼 클래스 사이의 `is-a` 관계를 나타내는데 사용된다.  

상속은 단일 상속과 다중 상속 두가지 방식으로 나눌 수 있는데,  
단일 상속은 하위 클래스가 단 하나의 상위 클래스만 상속하는 것을 말하며,  
다중 상속은 하위 클래스가 여러 상위 클래스를 동시에 상속할 수 있음을 의미한다.

상속의 가장 큰 역할은 코드의 재사용이라고 할 수 있다.  
만약 서로 다른 두 개의 클래스에 동일한 속성과 메서드가 있다면 이러한 부분을 상위 클래스로 추출하고, 하위 클래스가 상위 클래스를 상속하도록 하여  
코드를 재사용해서 동일한 코드를 불필요하게 반복적으로 작성하는 것을 방지할 수 있다.

그러나 과도하게 사용할 경우 코드의 가독성과 유지 관리성이 떨어진다.  
또, 하위 클래스와 상위 클래스가 밀접하게 결합되어 있는 경우에는 상위 클래스의 코드 수정이 하위 클래스에 직접적인 영향을 미칠 수 있다.

상속은 논란의 여지가 있는 특성이기도 해서 적게 사용해야 한다.  
심지어는 사용하면 안되는 안티 패턴으로 간주되기도 한다.

### 다형성

`다형성 (polymorphism)`이란 코드를 실행하는 과정에서 하위 클래스를 상위 클래스 대신 사용하고, 하위 클래스의 메서드를 호출할 수 있는 특성을 의미한다.

다음은 Java 의 클래스 상속 구문을 활용하여 다형성 속성을 구현한 코드다.

```java
public class DynamicArray {

    private static final int DEFAULT_CAPACITY = 10;
    protected int size = 0;
    protected int capacity = DEFAULT_CAPACITY;
    protected Integer[] elements = new Integer[DEFAULT_CAPACITY];

    public int size() {
        return this.size;
    }

    public Integer get(int index) {
        return this.elements[index];
    }

    public void add(Integer e) {
        ensureCapacity();
        elements[size++] = e;
    }

    protected void ensureCapacity() {
        // 배열이 가득 찼을 때 배열의 크기를 확장하는 메서드 (코드는 생략)
    }

    // 생략
}

public class SortedDynamicArray extends DynamicArray {

    @Override
    public void add(Integer e) {
        ensureCapacity();
        int i;
        for (i = size - 1; i >= 0; --i) { // 배열의 데이터가 순서대로 유지되는 것을 보장
            if (elements[i] > e) {
                elements[i + 1] = elements[i];
            } else {
                break;
            }
        }
        elements[i + 1] = e;
        ++size;
    }
}

public class Example {
    public static void test(DynamicArray dynamicArray) {
        dynamicArray.add(5);
        dynamicArray.add(1);
        dynamicArray.add(3);
        for (int i = 0; i < dynamicArray.size(); i++) {
            System.out.println(dynamicArray.get(i));
        }
    }
    
    public static void main(String[] args) {
        DynamicArray dynamicArray = new SortedDynamicArray();
        test(dynamicArray); // 출력 결과: 1, 3, 5
    }
}
```

다형성을 충족시키지 위해 다음과 같은 세가지 문법이 활용되었다.
- **상위 클래스의 객체가 하위 클래스 객체를 참조할 수 있어야 한다.** 즉, `SortedDynamicArray` 클래스 객체를 `DynamicArray` 클래스 객체에 전달할 수 있어야 한다.
- **상속을 지원해야 한다.** 즉, `SortedDynamicArray` 클래스는 `DynamicArray` 클래스를 상속받으므로, `SortedDynamicArray` 클래스 객체가 `DynamicArray` 클래스 객체에 전달될 수 있다.
- **상위 클래스의 메서드를 재정의하는 하위 클래스를 지원해야 한다.** 즉, `SortedDynamicArray` 클래스는 `DynamicArray` 클래스의 `add()` 메서드를 재정의한다.

이 세가지 문법 구조를 통해 `test()` 메서드에서 `DynamicArray` 클래스의 `add()` 메서드를 대체한 `SortedDynamicArray` 클래스의 `add()` 메서드를 실행하여 다형성을 실현하고 있다.

다음은 Java 의 인터페이스 구문을 활용하여 다형성 속성을 구현한 코드다.

```java
public interface Iterator {
    
    boolean hasNext();
    
    String next();
    
    String remove();
}

public class Array implements Iterator {
    
    private String[] data;

    @Override
    public boolean hasNext() {...}

    @Override
    public String next() {...}

    @Override
    public String remove() {...}
    
    // 생략
}

public class LinkedList implements Iterator {

    private LinkedListNode head;

    @Override
    public boolean hasNext() {...}

    @Override
    public String next() {...}

    @Override
    public String remove() {...}

    // 생략
}

public class Demo {
    
    private static void test(Iterator iterator) {
        while(iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
    
    public static void main(String[] args) {
        Iterator array = new Array();
        print(arrayIterator);
        Iterator linkedList = new LinkedList();
        print(linkedList);
    }
}
```

`Iterator`는 컬렉션 데이터를 순회할 수 있는 반복자를 정의하는 인터페이스이고,  
`Array`, `LinkedList` 모두 `Iterator` 인터페이스를 구현하고 있다.  
이 때 `Array`, `LinkedList` 클래스는 서로 다른 유형의 클래스임에도 `test(Iterator iterator)` 메서드에 클래스 객체를 전달하여 서로 다른 `next()`, `hasNext()` 메서드를 동적으로 호출할 수 있도록 지원한다.

다형성은 전략 패턴, 구현이 아닌 인터페이스 기반의 프로그래밍, 의존 역전 원칙, 리스코프 치환 원칙, 다형성을 이용하여 `if-else` 구문 제거하기와 같은  
많은 디자인 패턴, 설계 원칙, 프로그래밍 테크닉 코드 구현의 기초이다.

## 2.4 객체지향 프로그래밍, 절차적 프로그래밍, 함수형 프로그래밍의 차이

### 절차적 프로그래밍

절차적 프로그래밍은 프로그래밍 패러다임이기도 하다.  
코드를 구성하기 위한 기본 단위로 `메서드`, `기능`, `연산`처럼 절차가 필요하며, `멤버 변수`, `속성`과 같은 데이터가 메서드와 분리되어 있는 것이 특징이다.  
절차적 프로그래밍 스타일은 순서대로 실행되는 메서드들을 나열하여 데이터를 조작하고, 이를 통해 기능을 구현하는 프로그래밍 스타일이다.

절차적 프로그래밍 언어는 클래스와 객체를 지원하지 않기 때문에 상속, 다형성, 캡슐화 같은 객체지향 프로그래밍의 특성도 지원하지 않는다.

### 객체지향 프로그래밍과 절차적 프로그래밍의 비교

- 객체지향 프로그래밍은 대규모의 복잡한 프로그램 개발에 더 적합하다.
- 객체지향 프로그래밍 스타일의 코드는 재사용, 확장, 유지 관리가 쉽다.
- 객체지향 프로그래밍 언어는 더 사용자 친화적이고 고급 언어이며 지능적이다.

### 함수형 프로그래밍

함수형 프로그래밍은 프로그램이 일련의 수학적 함수 또는 표현식의 조합으로 표현될 수 있다고 생각한다.  
때문에 함수형 프로그래밍에는 컴퓨터 과학, 데이터 처리, 통계 분석과 같은 적절한 응용 시나리오가 있다.

## 2.5 객체지향 프로그래밍처럼 보이지만 실제로는 절차적 프로그래밍

### getter, setter 메서드 남용

무분별하게 `getter`, `setter` 메서드를 남용하는것은 캡슐화 특성을 위반하므로 권장하지 않는다.

`private` 속성으로 정의되어 있는 속성이라도 `getter` 와 `setter` 메서드를 제공하고 있다면 사실상 `public` 속성으로 정의한것과 다르지 않다.

캡슐화 특성에 대한 정의에 따르면, 내부 데이터는 접근 권한 제어를 통해 숨겨져야 하며, 외부에서는 클래스에서 제공하는 제한된 인터페이스를 통해서만 내부 데이터에 접근할 수 있어야 한다.  
따라서 노출해서는 안 되는 `setter` 메서드를 노출하는 것은 객체지향 프로그래밍의 캡슐화 특성을 명백하게 위반하고 있는것이다.

또한, `getter` 메서드만 노출한다고 하더라도 해당 `getter` 메서드가 컬렉션을 반환하거나, 특정 객체를 반환한다면 문제가 될 수 있다.  
`getter` 메서드로 컬렉션은 얻은 후 외부에서 값을 직접 수정하는 것이 가능하기 때문이다.

이러한 문제를 피하려면 어떻게 해야할까?  

Java 에서는 `Collections.unmodifiableList()` 메서드를 통해 `getter` 메서드가 수정 불가능한 `UnmodifiableList` 컬렉션을 반환하도록 할 수 있으며,  
`UnmodifiableList` 는 `add()`, `clear()` 와 같이 데이터 수정과 관련된 메서드를 호출할 경우 `UnsupportedOperationException` 예외를 발생시키기 때문에 컬렉션의 데이터가 수정되는 것을 방지할 수 있다.

하지만 이 경우도 컬렉션 자체는 수정 할 수 없지만, 컬렉션의 각 객체를 계속 수정 할 수 있다.  
이 경우는 `getter` 메서드로 객체를 반환하는 경우도 같은 문제가 날 수 있으며,  
이러한 문제는 6.6 절에서 해답을 찾을 수 있다.

클래스를 설계할 때 정말로 필요한 경우가 아니라면 속성에 대한 `setter` 메서드는 정의하지 않아야 한다.  
또한 `getter` 메서드의 반환값이 컬렉션이거나 객체일 경우 해당 내부 데이터가 수정될 가능성에도 대비해야한다.

### 전역 변수와 전역 메서드의 남용

전역 변수와 전역 메서드 중에서 가장 많이 사용되는 것은 `Constants` 클래스와 `Utils` 클래스이다.

#### Constants 클래스

상수는 일종의 전역 변수와 같이 취급되며, 일반적으로 `Constants` 클래스에서 정의된다.

`Constants` 클래스에 프로젝트에서 사용되는 모든 상수를 통합 할 경우 좋은 설계라고 할 수 없다.  
그 이유는 무엇일까?

1. **코드의 유지 보수성에 영향을 미친다.**  
=> 같은 프로젝트에 관련된 개발 엔지니어가 많다면 클래스에 새로운 상수를 추가하는 등 해당 클래스를 수정 할 수 있고, 그렇게 된다면 클래스가 점점 커진다.  
그 결과 시간이 많이 걸리고 노동 집약적인 코드 확인이 계속 늘어나 수정이 일어남에 따라, 코드가 충돌을 일으킬 가능성도 높아진다.
2. **코드의 컴파일 시간을 증가시킨다.**  
=> `Constants` 클래스에 포함된 상수가 많을수록 이 클래스에 더 많은 코드가 종속되며,  
클래스를 수정할 때마다 종속된 가른 클래스가 매번 다시 컴파일 되어 불필요한 컴파일 시간을 낭비한다.
3. **코드의 재사용 가능성에 영향을 미친다.**  
=> 이 프로젝트에서 개발한 클래스를 다른 프로젝트에서 재사용하려고 할 때, 이 클래스가 `Constants` 클래스에 종속되어 있다면 어떻게 될까?  
`Constants` 클래스의 일부 상수만 사용하더라도 전체를 도입해야한다. 실제로는 아무 관련도 없는 많은 상수들이 모듈에 포함되는 것이다.

그렇다면 `Constants` 클래스를 어떻게 개선할 수 있을까?

- 기능에 따라 `Constants` 클래스를 여러 개의 클래스로 분리한다.
- `Constants` 클래스를 별도로 설계하지 않고, 클래스가 자신이 사용할 상수를 직접 정의한다.

#### Utils 클래스

일반적으로 객체를 생성하지 않고 직접 사용할 수 있는 정적 메서드는 `Utils` 클래스에서 정의된다.  
아무런 관계가 없는 여러개의 클래스에서 같은 기능을 일부 공유하고 있다고 상위 클래스로 추상화하면 코드 가독성을 해치게 되기 때문에 `Utils` 클래스를 사용하게 되었다.

`Utils` 클래스를 정의하기 전에 다음과 같은 질문에 대해 생각해볼 필요가 있다.

- `Utils` 클래스를 별도로 정의해야 하는가?
- `Utils` 클래스의 일부 메서드를 다른 클래스로 정의할 수 있는가?

이러한 질문에 답한 후에도 여전히 `Utils` 클래스를 정의할 필요가 있다고 생각한다면 과감하게 정의하면 된다.  
또한, `Constants` 클래스와 유사하게 `Utils` 클래스를 설계할 때에도 기능에 따라 다른 여러 개의 클래스로 설계하는 것이 좋다.  
모든 기능을 하나의 큰 `Utils` 클래스에 넣지 않도록 유의해야한다.

### 데이터와 메서드 분리로 클래스 정의하기

기존의 MVC 구조는 Model 계층, View 계층, Controller 계층으로 나뉜다.  
그러나 프론트엔드와 백엔드가 분리되기 시작하면서 백엔드에서는 컨트롤러 계층, 서비스 계층, 저장소 계층으로 다시 나누는 경향이 생겼다.  

컨트롤러 계층은 인터페이스를 프론트엔드 호출에 노출시키는 역할을 하고,  
서비스 계층은 핵심 비즈니스 논리를 책임지며,  
저장소 계층은 데이터의 처리를 책임진다.

각각의 계층은 상응하는 `VO(view object)`, `BO(business object)`, `Entity` 를 정의 할 수 있다.  
일반적으로 VO, BO, Entity 에서는 데이터만 정의하는 대신 메서드는 정의하지 않으며,  
`Controller` 클래스, `Service` 클래스, `Repository` 클래스에서 메서드를 정의한다.  
이러한 방식은 전형적인 절차적 프로그래밍 스타일이다.

사실 이 개발 방식은 빈약한 도메인 모델 기반의 개발 방식이라고 하며,  
현재 우리가 일반적으로 사용하고 있는 웹 프로젝트의 백엔드 개발 방식이기도 하다.

이러한 개발 방식은 객체 지향 프로그래밍 방식에 위배되는데, 왜 대부분의 프로젝트가 이 개발 방식을 기반으로 개발되고 있는것일까?

