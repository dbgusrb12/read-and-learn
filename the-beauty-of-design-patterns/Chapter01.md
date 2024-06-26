# 01. 개요

## 1.1 코드 설계를 배우는 이유

- 확장성과 가독성이 높아 유지 보수가 용이한 고품질의 코드를 작성할 때 필요하다.
- 높은 품질의 코드를 작성할 수 있도록 스킬을 향상하기 위해 필요하다.
- 코드 설계와 관련된 지식은 오픈소스 프로젝트를 쉽게 이해할 수 있을 뿐만 아니라 코드의 기술적 본질을 이해하는 데 도움이 되는 프로그램 개발의 기본 기술이다.
- 잘 설계되고 유지 보수가 쉬운 시스템은 더 의미 있는 일을 할 수 있도록 성장 할 수 있다.

## 1.2 코드 품질 평가 방법

코드의 품질을 평가하기 전에 어떤 코드가 좋은 코드인지 알기 위해 필요한 인식은 어떤게 있을까?

- 어떤 코드가 높은 가독성을 가지는 코드인가?
- 어떤 종류의 코드가 확장과 유지 관리에 용이한가?
- 가독성, 확장성, 유지 보수 사이의 관계는 무엇인가?
- 유지 보수는 정확히 어떤 것을 의미하는 것인가?

코드 품질에 대한 설명에 '`좋음`,`나쁨`'과 같은 간단하고 일반적인 설명 방법 외의 다른 설명 방법은 어떤게 있을까?

- `유연성 (flexibility)`
- `확장성 (extensibility)`
- `유지 보수성 (maintainability)`
- `가독성 (readability)`
- `이해 용이성 (understandability)`
- `가변성 (changeability)`
- `재사용성 (reusability)`
- `테스트 용이성 (testability)`
- `모듈성 (modularity)`
- `높은 응집도와 낮은 결합도 (high cohesion loose coupling)`
- `높은 효율성 (high efficiency)`
- `고성능 (high performance)`
- `보안성 (security)`
- `호환성 (compatibility)`
- `사용성 (usability)`
- `깨끗함 (clean)`
- `명확성 (clarity)`
- `간결성 (simplicity)`
- `직접성 (straightforward)`
- `더 작은 코드가 더 많은 것을 담는다 (less code is more)`
- `문서화가 잘 된 (well-documented)`
- `계층화가 잘 이루어진 (well-layered)`
- `정확성 (correctness, bug free)`
- `강건성 (robustness)`
- `신뢰성 (reliability)`
- `확장성 (scalability)`
- `안정성 (stability)`
- `우아함 (elegant)`

이 단어들은 서로 다른 관점에서 코드의 품질을 설명하기 때문에 종합적으로 평가하기가 어려운 것이 사실이다.  
코드 품질에 대한 평가는 다양한 측면에서 각 요소를 평가해야 하며 하나의 관점으로만 평가해서는 안된다.  
ex) 확장성은 좋지만 가독성이 좋지 않은 코드의 경우, 이 코드는 고품질의 코드라고 일방적으로 가정할 수 있는가?

### 유지 보수성

코드 개발에서 유지 보수란 버그의 수정, 이전 코드의 수정 또는 새로운 코드의 추가에 불과하다.  
코드의 '`유지 보수성 (maintainability)`이 높다' 라는 표현의 의미는  
기존의 코드 설계를 손상시키거나 새로운 버그를 발생시키지 않고도 빠르게 코드를 수정하거나 추가할 수 있는 상태를 말한다.

소프트웨어 엔지니어는 버그의 수정, 기존 기능의 논리 수정, 새로운 기능 논리 추가에 대부분의 시간을 할애하기 때문에 코드의 유지 보수성은 특히 중요하다.

### 가독성

코드를 읽는 횟수는 코드를 작성하고 실행하는 횟수보다 훨씬 더 많기 때문에 코드의 `가독성 (readability)`은 매우 중요하다.  
버그를 수정하거나, 기능을 추가하거나, 수정을 하기 전에 먼저 코드를 이해해야 가능하기 때문에 코드의 가독성은 유지보수성에도 큰 영향을 미친다.

코드의 가독성은 어떻게 판단할 수 있을까?
- 코드의 명명이 의미가 있는지?
- 주석이 자세히 기술되어 있는지?
- 함수 길이는 적절한지?
- 모듈 구분이 명확한지?
- 코드가 높은 응집도와 낮은 결합도를 가지는지?
- 코드 리뷰를 통해 판단

### 확장성

코드의 `확장성 (extensibility)`은 기존 코드를 약간 수정하는 것만으로도 혹은 전혀 수정하지 않고도 확장을 통해 새로운 기능을 추가하는 것을 말한다.  
즉, 코드의 확장성은 코드를 작성할 때 새로운 기능을 추가할 수 있는 여지가 설계 당시부터 고려되어 있어 확장용 인터페이스가 이미 존재함을 의미하며,  
확장성이 높으면 새로운 기능 코드를 추가할 때 기존 코드의 대량 수정 없이도 새로운 코드를 바로 추가할 수 있다.

코드의 확장성은 요구 사항의 미래 변화에 대처할 수 있는 코드의 능력을 의미한다.

### 유연성

`유연성 (flexibility)`은 코드의 품질을 설명하는 데에도 사용할 수 있다.  
어떤 상황에서 코드가 유연하다고 말할 수 있을까?
- 기존 코드에 확장을 위한 인터페이스가 준비되어 있어 기존 코드의 수정 없이 새로운 코드를 추가하기만 하면 된다.  
  이 경우 확장성이 높을 뿐만 아니라 코드가 유연하다고 할 수 있다.
- 함수를 구현할 때 기본적으로 재사용 가능한 많은 모듈과 클래스 등이 기존 코드에 추상화된 형태로 이미 제공되어 이를 상속받아 직접 사용할 수 있다.  
  이 경우 재사용성이 높을 뿐만 아니라 코드가 유연하다고 할 수 있다.
- 클래스를 사용할 때 클래스가 다양한 사용 시나리오에 대응하고, 다양한 요구를 충족할 수 있다.  
  이 경우 클래스의 사용성이 높을 뿐만 아니라 코드가 유연하다고 할 수 있다.

코드의 확장과 재사용이 용이하고 사용성이 높을 경우 일반적으로 코드가 유연하다고 생각할 수 있다.

### 간결성

`Keep It Simple, Stupid` 라는 설계 원칙이 있다.  
`KISS 원칙` 이라고 하는데, 이 원칙은 코드를 가능한 단순하게 유지하려는 `간결성 (simplicity)`을 의미한다.  
단순한 코드와 명확한 논리는 종종 코드의 가독성이 높고, 유지 보수성이 높다는 것을 의미한다.  

### 재사용성

코드의 `재사용성 (reusability)`은 반복적인 코드 작성을 최소화하고 기존 코드를 재사용하는 것으로 이해할 수 있다.  
재사용성은 중요한 코드 평가 기준이자 다양한 설계 원칙, 설계 사상, 디자인 패턴에 의해 달성되는 최종 효과이다.

실제로 코드의 재사용성은 `DRY (Don't repeat yourself) 원칙` 과 밀접한 관련이 있다.

### 테스트 용이성

`테스트 용이성 (testability)`은 지금까지 언급한 여섯 가지 코드 품질 평가 기준에 비해 언급되는 비중은 덜하지만, 매우 중요하다.  
코드의 테스트 용이성이 낮으면 단위 테스트를 작성하기 어렵다는 뜻이며, 기본적으로 코드의 설계에 문제가 있음을 보여준다.

## 1.3 고품질 코드를 작성하는 방법

고품질의 코드를 작성하려면 객체지향 설계 패러다임, 설계 원칙, 코딩 규칙, 리팩터링 기술, 디자인 패턴을 포함하여 일부 프로그래밍 방법론을 마스터해야 한다.  

### 객체지향

객체지향 프로그래밍 패러다임은 캡슐화, 추상화, 상속, 다형성 등의 풍부한 기능으로 인해 복잡한 설계 사상을 구현할 수 있으므로  
다양한 설계 원칙과 디자인 패턴 코딩 구현의 기초가 된다.

### 설계 원칙

설계 원칙은 코드 설계를 이끌어내는 몇 가지 경험의 요약이며, 코드 설계의 일반적인 방향을 나타내는 정신에 해당한다.  
또한 디자인 패턴보다 더 일반적이다.

### 디자인 패턴

디자인 패턴은 소프트웨어 개발에서 자주 접하는 일부 설계 문제에 대해 요약된 해결 방법 또는 설계 사상을 모아둔 것이다.  
디자인 패턴을 적용하는 주요 목적은 디커플링을 통해 코드의 확장성을 향상시키는 것이다.  

추상화 측면에서 설계 원칙은 디자인 패턴보다 더 추상적이며, 디자인 패턴은 더 구체적이고 구현하기 쉽다.

### 코딩 규칙

코딩 규칙은 주로 코드 가독성 문제를 해결한다.  
설계 원칙과 디자인 패턴에 비해 더 구체적이며 코드 세부 사항에 중점을 두고 구현이 가능하다.  
진행중인 소규모 리팩터링은 주로 코딩 규칙 이론에 의존하게 된다. 

### 리팩터링 기법

리팩터링은 코드 품질 저하를 방지하는 효과적인 수단으로서  
객체지향 프로그래밍 패러다임, 설계 원칙, 디자인 패턴, 코딩 규칙에 대한 이론적 지식에 의존한다.

## 1.4 과도한 설계를 피하는 방법

코드를 설계하지 않는 것은 좋지 않지만, 과도하게 설계하는 것도 좋지 않다.  
망치만 있으면 모든 것이 못으로 보인다.  
무엇이든지 남용하면 좋지 않다.

- 코드 설계의 원래 의도는 코드 품질을 향상시키는 것이다.
- 코드 설계의 원칙은 앞에 문제가 있고, 뒤에 방안이 있다는 것이다.
- 코드 설계의 응용 시나리오는 복잡한 코드에 적용되어야 한다.
- 지속적인 리팩터링은 과도한 설계를 효과적으로 방지할 수 있다.
- 특정 시나리오 외의 코드 설계에 대해 이야기하지 않는다.

