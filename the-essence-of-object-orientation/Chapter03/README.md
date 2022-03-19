# 타입과 추상화

## 추상화를 통한 복잡성 극복

추상화란 어떤 양상, 세부 사항, 구조를 좀 더 명확하게 이해하기 위해 특정 절차나 물체를 의도적으로 생략하거나 감춤으로써 복잡도를 극복하는 방법이다.

복잡성을 다루기 위해 추상화는 두 차원에서 이뤄진다.
- 첫 번째 차원은 구체적인 사물들 간의 공통점은 취하고 차이점은 버리는 일반화를 통해 단순하게 만드는 것이다.
- 두 번째 차원은 중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거함으로써 단순하게 만드는 것이다.

모든 경우에 추상화의 목적은 복잡성을 이해하기 쉬운 수준으로 단순화하는 것이다.

객체지향 패러다임은 객체라는 추상화를 통해 현실의 복잡성을 극복한다.

## 객체지향과 추상화

### 모두 트럼프일 뿐

앨리스와 하트 여왕이 최초로 마주치는 순간, 앨리스는 수많은 객체들을 `트럼프` 라는 하나의 개념으로 단순화해서 바라본다.  
모든 차이점을 과감하게 무시한 채 공통점만을 취해 단순화 해 버렸다.

### 그룹으로 나누어 단순화하기

앨리스는 정원에 있는 인물들을 두 개의 그룹으로 나눴다.

- 토끼 : 회중시계를 가진 하얀 토끼
- 트럼프 : 정원사, 병사, 신하, 왕자, 공주, 하객, 하트 잭, 하트 왕, 하트 여왕 ...

비록 토끼 그룹에 속하는 인물이 단 하나뿐이라도 다수의 개별적인 인물이 아닌 `트럼프` 와 `토끼`라는 두 개의 렌즈를 통해 정원을 바라보는 것은  
정원에 내재된 복잡성을 효과적으로 감소시킨다.

### 개념

공통점을 기반으로 객체들을 묶기 위한 그릇을 `개념(concept)`이라고 한다.  
개념이란 일반적으로 우리가 인식하고 있는 다양한 사물이나 객체에 적용할 수 있는 아이디어나 관념을 뜻한다.

개념을 이용하면 객체를 여러 그룹으로 `분류(classification)`할 수 있다.  
개념은 공통점을 기반으로 객체를 분류할 수 있는 일종의 체라고 할 수 있다.

객체에 어떤 개념을 적용하는 것이 가능해서 개념 그룹의 일원이 될 때 객체를 그 개념의 `인스턴스(instance)`라고 한다.

위의 내용을 정리하면 다음과 같다.

객체란 특정한 개념을 적용할 수 있는 구체적인 사물을 의미한다. 개념이 객체에 적용됐을 때 객체를 개념의 인스턴스라고 한다.

### 개념의 세 가지 관점

- `심볼(symbol)` : 개녕을 가리키는 간략한 이름이나 명칭
- `내연(intension)` : 개념의 완전한 정의를 나타내며 내연의 의미를 이용해 객체가 개념에 속하는지 여부를 확인할 수 있다.
- `외연(extension)` : 개념에 속하는 모든 객체의 집합(set)

이 세가지 관점을 트럼프에 적용시켜 보면 다음과 같이 표현할 수 있다.

- `심볼(symbol)` : 트럼프
- `내연(intension)` : 몸이 납작하고 두 손과 두 발은 네모 귀퉁이에 달려 있는 등장인물
- `외연(extension)` : 정원사, 병사, 신하, 왕자와 공주, 하객으로 참석한 왕과 왕비들, 하트 잭, 하트 왕과 하트 여왕

객체지향의 세계에서 가장 널리 알려진 유명인사가 클래스(class) 라는 사실을 감안한다면 분류(classification) 라는 개념이 얼마나 중요한지 실감할 수 있을 것이다.

### 객체를 분류하기 위한 틀

분류란 객체에 특정한 개념을 적용하는 작업이다.  
객체에 특정한 개념을 적용하기로 결심했을 때 우리는 그 객체를 특정한 집합의 멤버로 분류하고 있는 것이다.

분류는 객체지향의 가장 중요한 개념 중 하나다. 어떤 객체를 어떤 개념으로 분류할지가 객체지향의 품질을 결정한다.

객체는 소중하므로 소중한 객체를 안전하고 적절한 장소에 보관할 수 있도록 인지능력을 발휘해 최대한 직관적으로 분류해야한다.

### 분류는 추상화를 위한 도구다.

개념은 객체들의 복잡성을 극복하기 위한 추상화 도구다.  
추상화를 사용함으로써 우리는 극도로 복잡한 이 세상을 그나마 제어 가능한 수준으로 단순화 할 수 있는 것이다.

## 타입

### 타입은 개념이다.

타입은 개념과 동일하다. 따라서 타입이란 우리가 인식하고 있는 다양한 사물이나 객체에 적용할 수 있는 아이디어나 관념을 의미한다.  
어떤 객체에 타입을 적용할 수 있을 때 그 객체를 다입의 인스턴스라고 한다.  
타입의 인스턴스는 타입을 구성하는 외연인 객체 집합의 일원이 된다.

### 데이터 타입

첫째, 타입은 데이터가 어떻게 사용되느냐에 관한 것이다. 숫자형 데이터가 숫자형인 이유는 데이터를 더하거나 빼거나 곱하거나 나눌 수 있기 때문이다.  
어떤 데이터가 문자열형인 이유는 두 데이터를 연결해 새로운 문자열을 만들 수 있고 데이터에 포함된 문자의 길이를 알 수 있기 때문이다.

둘째, 타입에 속한 데이터를 메모리에 어떻게 표현하는지는 외부로부터 철저하게 감춰진다.  
데이터 타입의 표현은 연산 작업을 수행하기에 가장 효과적인 형태가 선택되며,  
개발자는 해당 데이터 타입의 표현 방식을 몰라도 데이터를 사용하는데 지장이 없다.

데이터 타입은 메모리 안에 저장된 데이터의 종류를 분류하는 데 사용하는 메모리 집합에 관한 메타데이터다.  
데이터에 대한 분류는 암시적으로 어떤 종류의 연산이 해당 데이터에 대해 수행될 수 있는지를 결정한다.

### 객체와 타입

앞에서 데이터 타입에 관해 언급했던 두 가지는 객체의 타입을 이야기할 때도 동일하게 적용된다.

첫째, 어떤 객체가 어떤 타입에 속하는지를 결정하는 것은 객체가 수행하는 행동이다.  
어떤 객체들이 동일한 행동을 수행할 수 있다면 그 객체들은 동일한 타입으로 분류될 수 있다.

둘째, 객체의 내부적인 표현은 외부로부터 철저하게 감춰진다.  
객체의 행동을 가장 효과적으로 수행할 수만 있다면 객체 내부의 상태를 어떤 방식으로 표현하더라도 무방하다.

### 행동이 우선이다.

객체의 타입을 결정하는 것은 객체의 행동뿐이다. 객체가 어떤 데이터를 보유하고 있는지는 타입을 결정하는 데 아무런 영향도 미치지 않는다.

같은 타입에 속한 객체는 행동만 동일하다면 서로 다른 데이터를 가질 수 있다. 여기서 동일한 행동이란 동일한 책임을 의미하며,  
동일한 책임이란 동일한 메시지 수신을 의미한다.

따라서 동일한 타입에 속한 객체는 내부의 데이터 표현 방식이 다르더라도 동일한 메시지를 수신하고 이를 처리할 수 있다.  
다만 내부의 표현 방식이 다르기 때문에 동일한 메시지를 처리하는 방식은 서로 다를 수밖에 없다. 이것은 `다형성`에 의미를 부여한다.

다형성이란 동일한 요청에 대해 서로 다른 방식으로 응답할 수 있는 능력을 뜻한다.  
동일한 메시지를 서로 다른 방식으로 처리하기 위해 객체들은 동일한 메시지를 수신할 수 있어야 하기 때문에 결과적으로 다형적인 객체들은 동일한 타입(또는 타입 계층)에 속하게 된다.

외부에 행동만을 제공하고 데이터는 행동 뒤로 감춰야 한다는 원칙을 `캡슐화`라고 한다.

행동에 따라 객체를 분류하기 위해서는 객체가 내부적으로 관리해야 하는 데이터가 아니라 객체가 외부에 제공해야 하는 행동을 먼저 생각해야 한다.  
이를 위해서는 객체가 외부에 제공해야 하는 책임을 먼저 결정하고 그 책임을 수행하는 데 적합한 데이터를 나중에 결정한 후,  
데이터를 책임에 수행하는 데 필요한 외부 인터페이스 뒤로 캡슐화해야 한다.

객체를 결정하는 것은 행동이다. 데이터는 단지 행동을 따를 뿐이다. 이것이 객체를 객체답게 만드는 가장 핵심적인 원칙이다.

## 타입의 계층

### 일반화/특수화(generalization/specialization) 관계

타입과 타입 사이에는 일반화/특수화 관계가 존재할 수 있다.  
일반적이라는 말은 더 포괄적이라는 의미를 내포한다.

일반화와 특수화는 동시에 일어난다. 더 특수하다는 것은 일반적인 개념보다 범위가 더 좁다는 것을 의미한다.

일반적인 타입이란 특수한 타입이 가진 모든 행동들 중에서 일부 행동만을 가지는 타입을 가리킨다.  
특수한 타입이란 일반적인 타입이 가진 모든 행동을 포함하지만 거기에 더해 자신만의 행동을 추가하는 타입을 가리킨다.  
따라서 일반적인 타입은 특수한 타입보다 더 적은 수의 행동을 가지고 특수한 타입은 일반적인 타입보다 더 많은 수의 행동을 가진다.

일반화/특수화는 행동에 관한 것이다.  
일반적인 타입은 특수한 타입에 비해 더 적은 수의 행동을 가지며 특수한 타입은 일반적인 타입에 비해 더 많은 행동을 가진다.  
단, 특수한 타입은 일반적인 타입이 할 수 있는 모든 행동을 동일하게 수행할 수 있어야 한다.

타입의 내연을 의미하는 행동의 가짓수와 외연을 의미하는 집합의 크기는 서로 반대이다.  
일반화/특수화 관계에서 일반적인 타입은 특수한 타입보다 더 적은 수의 행동을 가지지만 더 큰 크기의 외연 집합을 가진다.  
특수한 타입은 일반적인 타입보다 더 많은 수의 행동을 가지지만 더 적은 크기의 외연 집합을 가진다.

### 슈퍼타입과 서브타입

일반화/특수화 관계는 좀 더 일반적인 한 타입과 좀 더 특수한 한 타입 간의 관계이다.  
이 때 좀 더 일반적인 타입을 `슈퍼타입(Supertype)`이라고 하고 좀 더 특수한 타입을 `서브타입(Subtype)`이라고 한다.

서브타입은 슈퍼타입의 행위와 호환되기 때문에 서브타입은 슈퍼타입을 대체할 수 있어야 한다.

서브타입은 슈퍼타입의 행위에 추가적으로 특수한 자신만의 행동을 추가하는 것이므로 슈퍼타입의 행동은 서비타입에게 자동으로 상속된다.

### 일반화는 추상화를 위한 도구다.

추상화의 두 번째 차원은 중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거시켜 단순하게 만드는 것이다.  
일반화/특수화 계층은 객체지향 패러다임에서 추상화의 두 번째 차원을 적절하게 활용하는 대표적인 예다.

## 정적 모델

### 타입의 목적

타입을 사용하는 이유는 인간의 인지 능력으로는 시간에 따라 동적으로 변하는 객체의 복잡성을 극복하기가 너무 어렵기 때문이다.

타입은 시간에 따라 동적으로 변하는 상태를 시간과 무관한 정적인 모습으로 다룰 수 있게 해준다.

### 그래서 결국 타입은 추상화다

타입은 추상화다. 타입을 이용하면 객체의 동적인 특성을 추상화할 수 있다.  
결국 타입은 시간에 따른 객체의 상태 변경이라는 복잡성을 단순화할 수 있는 효과적인 방법인 것이다.

### 동적 모델과 정적 모델

객체가 특정 시점에 구체적으로 어떤 상태를 가지느냐를 객체의 `스냅샷(snapshot)`이라고 한다.  
스냅샷처럼 실제로 객체가 살아 움직이는 동안 상태가 어떻게 변하고 어떻게 행동하는지를 포착하는 것을 `동적 모델(dynamic model)`이라고 한다.

다른 하나는 개체가 가질 수 있는 모든 상태와 모든 행동을 시간에 독립적으로 표현하는 것이다.  
일반적으로 이런 모델을 `타입 모델(type diagram)`이라고 한다.  
이 모델은 동적으로 변하는 객체의 상태가 아니라 객체가 속한 타입의 정적인 모습을 표현하기 때문에 `정적 모델(static model)`이라고도 한다.

객체지향 애플리케이션을 설계하고 구현하기 위해서는 객체 관점의 동적 모델과 객체를 추상화한 타입 관점의 정적 모델을 적절히 혼용해야 한다.

### 클래스

객체지향 프로그래밍 언어에서 정적인 모델을 클래스를 이용해 구현된다.  
따라서 타입을 구현하는 가장 보편적인 방법은 클래스를 이용하는 것이다.

타입은 객체를 분류하기 위해 사용하는 개념인 반면, 클래스는 단지 타입을 구현할 수 있는 여러 구현 메커니즘 중 하나이다.

클래스와 타입을 구분하는 것은 설계를 유연하게 유지하기 위한 바탕이 된다.  
클래스는 타입의 구현 외에도 코드를 재사용하는 용도로도 사용되기 때문에 클래스와 타입을 동일시하는 것은 수많은 오해와 혼란을 불러일으키곤 한다.

객체를 분류하는 기준은 타입이며, 타입을 나누는 기준은 객체가 수행하는 행동이다.  
객체를 분류하기 위해 타입을 결정한 후 프로그래밍 언어를 이용해 타입을 구현할 수 있는 한 가지 방법이 클래스인 것이다.

객체지향에서 중요한 것은 동적으로 변하는 객체의 `상태`와 상태를 변경하는 `행위`다. 클래스는 타입을 구현하기 위해 제공하는 구현 메커니즘 이다.