# 함께 모으기

마틴 파울러는 객체지향 설계 안에 존재하는 세 가지 상호 연관된 관점에 관해 설명한다.  
파울러는 세 가지 관점을 각각 개념 관점, 명세 관점, 구현 관점이라고 부른다.

`개념 관점(Conceptual Perspective)`에서 설계는 도메인 안에 존재하는 개념과 개념들 사이의 관계를 표현한다.  
이 관점은 사용자가 도메인을 바라보는 관점을 반영한다.

`명세 관점(Specification Perspective)`에 이르면 사용자의 영역인 도메인을 벗어나 개발자의 영역인 소프트웨어로 초점이 옮겨진다.  
프로그래머는 객체가 협력을 위해 `무엇`을 할 수 있는가에 초점을 맞춘다.  
인터페이스와 구현을 분리하는 것은 훌륭한 객체지향 설계를 낳는 가장 기본적인 원칙이다.

`구현 관점(Implementation Perspective)`은 프로그래머인 우리에게 가장 익숙한 관점으로, 실제 작업을 수행하는 코드와 연관돼 있다.  
구현 관점의 초점은 객체들이 책임을 수행하는 데 필요한 동작하는 코드를 작성하는 것이다.  
프로그래머는 객체의 책임을 `어떻게` 수행할 것인가에 초점을 맞추면 인터페이스를 구현하는 데 필요한 속성과 메서드를 클래스에 추가한다.

클래스는 세 가지 관점을 모두 수용할 수 있도록 개념, 인터페이스, 구현을 함께 드러내야 하는 동시에,  
코드 안에서 세 가지 관점을 쉽게 식별할 수 있도록 깔끔하게 분리해야 한다.

## 커피 전문점 도메인

### 커피 전문점이라는 세상

개발에 들어가기 전 먼저 커피 전문점을 구성하는 요소들에 관해 고민해 보는 것이 도움될 것이다.  
객체지향 패러다임의 가장 중요한 도구는 객체이므로 커피 전문정을 객체들로 구성된 작은 세상으로 바라보자.

#### 메뉴판

메뉴판은 아메리카노, 카푸치노, 카라멜 마끼아또, 에스프레소 네 개의 메뉴 항목 객체들을 포함하는 객체라고 볼 수 있다.

#### 손님

손님 객체는 메뉴판 객체 안에 적힌 메뉴 항목 객체들 중에서 자신이 원하는 메뉴 항목 객체 하나를 선택해 바리스타 객체에게 전달한다.

#### 바리스타

바리스타는 주문을 받은 메뉴에 따라 적절한 커피를 제조하고,  
제조할 수 있는 커피의 종류는 아메리카노, 카푸치노, 카라멜 마끼아또, 에스프레소 네 가지다.

바리스타는 자율적으로 커피를 제조하는 객체로 볼 수 있고,  
바리스타가 제조하는 커피 역시 메뉴판, 메뉴 항목, 바리스타와 구별되는 자신만의 경계를 가지므로 객체로 볼 수 있다.

#### 도메인

객체지향의 관점에서 커피 전문점이라는 도메인은 다음과 같이 구성된다.
- 손님 객체
- 메뉴 항목 객체
- 메뉴판 객체
- 바리스타 객체
- 커피 객체

#### 객체들 간의 관계

- 손님은 메뉴판에서 주문할 거피를 선택할 수 있어야 한다.
- 손님은 바리스타에게 주문을 해야 한다.
- 바리스타는 커피를 제조한다.

#### 타입

- 손님 타입
- 바리스타 타입
- 커피 타입
- 메뉴판 타입
- 메뉴 항목 타입

#### 타입 간의 관계

- 메뉴 항목은 메뉴판에 포함된다.
- 손님 타입은 메뉴판 타입을 알고 있어야 한다.
- 바리스타 타입은 커피 타입을 알고 있어야 한다.

## 설계하고 구현하기

### 커피를 주문하기 위한 협력 찾기

협력을 설계할 때는 객체가 메시지를 선택하는 것이 아니라 메시지가 객체를 선택하게 해야한다.  
메시지를 먼저 선택하고 그 후에 메시지를 수신하기에 적절한 객체를 선택해야 한다는 것이다.

#### 커피를 주문하라

커피를 주문하라는 메시지는 메뉴 이름이라는 인자를 포함하는 형식으로 구현된다.

해당 메시지를 처리할 객체는 손님 타입의 인스턴스다.  
손님 객체는 커피를 주문 할 책임을 할당 받았다.

#### 메뉴 항목을 찾아라

메뉴 항목을 찾으라는 메시지는 메뉴 이름이라는 인자를 포함하는 형식으로 구현되고,  
해당 메시지를 수신한 객체는 메뉴 이름에 대응되는 메뉴 항목을 반환해야 한다.

메뉴 항목을 찾을 책임은 메뉴판 타입의 인스턴스에 있다.

#### 커피를 제조하라

커피를 제조하라는 메시지는 메뉴 항목을 인자로 포함하는 형식으로 구현되고,  
해당 메시지를 수신한 객체는 제조된 커피를 반환해야 한다.

바리스타 객체는 커피를 제조할 책임을 할당 받았다.

### 인터페이스 정리하기

객체가 수신한 메시지가 객체의 인터페이스를 결정한다.  
메시지가 객체를 선택했고, 선택된 객체는 메시지를 자신의 인터페이스로 받아들인다.

객체가 어떤 메시지를 수신할 수 있다는 것은 그 객체의 인터페이스 안에 메시지에 해당하는 오퍼레이션이 존재한다는 것을 의미한다.

손님 객체의 인터페이스 안에는 '커피를 주문하라' 라는 오퍼레이션이 포함돼야 한다.  
메뉴판 객체의 인터페이스는 '메뉴 항목을 찾아라' 라는 오퍼레이션을 제공하며,  
바리스타 객체의 인터페이스는 '커피를 제조하라' 라는 오퍼레이션을,  
커피 객체는 '생성하라' 라는 오퍼레이션을 제공한다.

실제로 소프트웨어의 구현은 동적인 객체가 아닌 정적인 타입을 이용해 이뤄진다.  
따라서 객체들을 포괄하는 타입을 정의한 후 식별된 오퍼레이션을 타입의 인터페이스에 추가해야 한다.

```java
class Customer {
    public void order(String menuName) {}
}

class MenuItem {
}

class Menu {
    public MenuItem choose(String name) {}
}

class Barista {
    public Coffee makeCoffee(MenuItem menuItem) {}
}

class Coffee {
    public Coffee(MenuItem menuItem) {}
}
```

### 구현하기

클래스의 인터페이스를 식별했으므로 이제 오퍼레이션을 수행하는 방법을 메서드로 구현한다.  

- `Customer`는 `Menu`에게 `menuName`에 해당하는 `MenuItem`을 찾아달라고 요청해야 한다.
- `MenuItem`을 받아 이를 `Barista`에게 전달해서 원하는 커피를 제조하도록 요청해야 한다.

```java
class Customer {
    public void order(String menuName, Menu menu, Barista barista) {
        MenuItem menuItem = menu.choose(menuName);
        Coffee coffee = barista.makeCoffee(menuItem);
        ...
    }
}
```

- `Menu`는 `menuName`에 해당하는 `MenuItem`을 찾아야 하는 책임이 있다.

```java
class Menu {
    private List<MenuItem> items;
    
    public Menu(List<MenuItem> items) {
        this.items = items;
    }
    
    public MenuItem choose(String name) {
        for (MenuItem each : items) {
            if (each.getName().equals(name)) {
                return each;
            }
        }
        return null;
    }
}
```

- `Barista`는 `MenuItem`을 이용해서 커피를 제조한다.

```java
class Barista {
    public Coffee makeCoffee(MenuItem menuItem) {
        Coffee coffee = new Coffee(menuItem);
        return coffee;
    }
}
```

- `Coffee`는 커피 이름과 가격을 속성으로 가지고 생성자 안에서 `MenuItem`에 요청을 보내 커피 이름과 가격을 얻은 후 `Coffee` 속성에 저장한다.

```java
class Coffee {
    private String name;
    private int price;
    
    public Coffee(MenuItem menuItem) {
        this.name = menuItem.getName();
        this.price = menuItem.cost();
    }
}
```

- `MenuItem`은 `getName()` 과 `cost()` 메시지에 응답할 수 있도록 메서드를 구현해야 한다.

```java
public class MenuItem {
    private String name;
    private int price;
    
    public MenuItem(String name, int price) {
        this.name = name;
        this.price = price;
    }
    
    public int cost() {
        return price;
    }
    
    public String getName() {
        return name;
    }
}
```

## 코드와 세 가지 관점

### 코드는 세 가지 관점을 모두 제공해야 한다.

앞에서 작성한 코드는 개념 관점, 명세 관점, 구현 관점에서 각기 다른 사항들을 설명해준다.

#### 개념 관점

`Customer`, `Menu`, `MenuItem`, `Barista`, `Coffee` 클래스들을 자세히 살펴보면  
커피 전문점 도메인을 구성하는 중요한 개념과 관계를 반영한다는 사실을 알 수 있다.  
소프트웨어 클래스가 도메인 개념의 특성을 최대한 수용하면 변경을 관리하기 쉽고 유지보수성을 향상시킬 수 있다.  
소프트웨어 클래스와 도메인 클래스 사이의 간격이 좁으면 좁을수록 기능을 변경하기 위해 뒤적거려야 하는 코드의 양도 점점 줄어든다.

#### 명세 관점

클래스의 `public` 메서드는 다른 클래스가 협력할 수 있는 공용 인터페이스를 드러낸다.  
공용 인터페이스는 외부의 객체가 해당 객체에 접근할 수 있는 유일한 부분이다.  
최대한 변화에 안정적인 인터페이스를 만들기 위해서는 인터페이스를 통해 구현과 관련된 세부 사항이 드러나지 않게 해야한다.  

#### 구현 관점

클래스의 메서드와 속성은 구현에 속하며 공용 인터페이스의 일부가 아니다.  
따라서 메서드의 구현과 속성의 변경은 원칙적으로 외부의 객체에게 영향을 미쳐서는 안 된다.  
이것은 메서드와 속성이 철저하게 클래스 내부로 캡슐화돼야 한다는 것을 의미한다.

### 도메인 개념을 참조하는 이유

도메인 개념 안에서 적절한 객체를 선택하는 것은 도메인에 대한 지식을 기반으로 코드의 구조와 의미를 쉽게 유추할 수 있게한다.

여러 개의 클래스로 기능을 분할하고 클래스 안에서 인터페이스와 구현을 분리하는 이유는 변경이 발생했을 때 코드를 좀 더 수월하게 수정하길 원하기 때문이다.  
소프트웨어 클래스가 도메인 개념을 따르면 변화에 쉽게 대응할 수 있다.

### 인터페이스와 구현을 분리하라

명세 관점과 구현 관점이 뒤섞여 머릿속을 함부로 어지럽히지 못하게 하라.  
명세 관점은 클래스의 안정적인 측면을 드러내야 한다.  
구현 관점은 클래스의 불안정한 측면을 드러내야 한다.  
인터페이스가 구현 세부 사항을 노출하기 시작하면 아주 작은 변동에도 전체 협력이 요동치는 취약한 설계를 얻을 수밖에 없다.

중요한 건 클래스를 봤을 때 클래스를 명세 관점과 구현 관점으로 나눠볼 수 있어야 한다는 것이다.  
캡슐화를 위반해서 구현을 인터페이스 밖으로 노출해서도 안 되고, 인터페이스와 구현을 명확하게 분리하지 않고 흐릿하게 섞어놓아서도 안 된다.  
결국 세 가지 관점 모두에서 클래스를 바라볼 수 있으려면 훌륭한 설계가 뒷받침 돼야 하는 것이다.