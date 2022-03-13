# 협력하는 객체들의 공동체

객체지향을 처음 접하는 사람들은 "객체지향이란 실세계를 직접적이고 지관적으로 모델링할 수 있는 패러다임" 라는 설명과 마주하게 된다.  
이러한 설명은 객체지향 프로그래밍이란 현실 속에 존재하는 사물을 최대한 유사하게 모방해 소프트웨어 내부로 옮겨오는 작업이기 때문에 그 결과물인  
객체지향 소프트웨어는 실세계의 투영이며, 객체란 현실 세계에 존재하는 사물에 대한 추상화라는 것이다.

실세계의 모방이라는 개념은 객체지향의 기반을 이루는 철학적인 개념을 설명하는 데는 적합하지만 유연하고 실용적인 관점에서 객체지향 분석, 설계를  
설명하기에는 적합하지 않다.

객체지향의 목표는 실세계를 모방하는 것이 아닌, 오히려 새로운 세계를 창조하는 것이다. 소프트웨어 개발자의 역할은 단순히 실세계를 소프트웨어 안으로  
옮겨 담는 것이 아니라 고객과 사용자를 만족시킬 수 있는 신세계를 창조하는 것이다.

실세계의 모방이라는 개념이 비현실적임에도 여전히 많은 사람들이 실세계 객체와 소프트웨어 객체 간의 대응이라는 과거의 유산을 반복적으로 재생산하는  
이유는 실세계에 대한 비유가 객체지향의 다양한 측면을 이해하고 학습하는 데 매우 효과적이기 때문이다.

실세계의 사물을 기반으로 소프트웨어 객체를 식별하고 구현까지 이어간다는 개념은 객체지향 설계의 핵심 사상인 `연결완전성(seamlessness)` 을  
설명하는 데 적합한 틀을 제공한다.

객체지향을 설명하는 많은 책과 문서들이 오해의 여지가 있다는 사실을 잘 알고 있음에도 실세계의 모방이라는 개념을 쉽게 포기하지 못하는 이유는  
휼륭한 프로그램을 설계하고 구현하는 실무적인 관점에서는 부적합하지만 객체지향이라는 용어에 담긴 기본 사상을 이해하고 학습하는데 매우 효과적이기 때문이다.

## 협력하는 사람들

### 커피 공화국의 아침

바쁜 아침 시간의 카페에서 커피를 주문 할 때 손님이 커피를 주문하고, 캐시어는 주문을 받고, 바리스타는 커피를 제조한다.  
바리스타의 제조가 끝난 커피는 다시 캐시어에게 전달되고, 캐시어는 손님에게 커피를 주고, 손님은 커피를 받는다.

커피 한잔을 주문하는 작은 이벤트를 완성하는 데도 여러 사람의 `조율`과 `조화`가 필요한 것이다.  
커피를 주문하고 제조하는 과정은 `역할`, `책임`, `협력`이라는 사람의 일상 속에 항상 스며들어 있는 세 가지 개념이 한데 어울려 조화를 이루며 만들어 낸 것이다.

### 요청과 응답으로 구성된 협력

사람들은 스스로 해결하지 못하는 문제와 마주치면 문제 해결에 필요한 지식을 알고 있거나 서비스를 제공해줄 수 있는 사람에게 도움을 `요청(request)` 한다.  
하나의 문제를 해결하기 위해 다수의 사람 혹은 역할이 필요하기 때문에 한사람에 대한 요청이 또 다른 사람에 대한 요청을 유발하는 것이 일반적이기 때문에  
요청은 연쇄적으로 발생한다.

요청을 받은 사람은 주어진 책임을 다하면서 필요한 지식이나 서비스를 제공한다. 즉, 다른사람의 요청에 `응답(response)` 한다. 요청이 연이러 발생하기  
때문에 응답 역시 요청의 방향과 반대 방향으로 연쇄적으로 전달된다.

요청과 응답을 통해 다른 사람과 `협력(collaboration)` 할 수 있는 능력은 인간으로 하여금 거대하고 복잡한 문제를 해결할 수 있는 공동체를 형성할 수 있게 만든다.  
협력의 성공은 특정한 역할을 맡은 각 개인이 얼마나 요청을 성실히 이행하는가에 달려있다.

### 역할과 책임

사람들은 다른 사람과 협력하는 과정 속에서 특정한 `역할(role)` 을 부여받는다. '손님', '캐시어', '바리스타' 라는 역할이 그 예이다.  
역할은 어떤 협력에 참여하는 특정한 사람이 협력 안에서 차지하는 책임이나 의무를 의미한다. 역할이라는 단어는 의미적으로 책임이라는 개념을 내포한다.

특정한 역할은 특정한 책임을 암시한다. 협력에 참여하며 특정한 역할을 수행하는 사람들은 역할에 적합한 책임을 수행하게 된다.  
사람들이 협력을 위해 특정한 역할을 맡고 역할에 적합한 책임을 수행한다는 사실은 몇가지 중요한 개념을 제시한다.

- 여러 사람이 동일한 역할을 수행할 수 있다.
- 역할은 대체 가능성을 의미한다.
- 책임을 수행하는 방법은 자율적으로 선택할 수 있다.
- 한 사람이 동시에 여러 역할을 수행할 수 있다.

## 역할, 책임, 협력

### 기능을 구현하기 위해 협력하는 객체들

앞의 예시에서 사람이라는 단어를 `객체`로, 에이전트의 요청을 `메시지`로, 에이전트가 요청을 처리하는 방법을 `메서드`로 바꾸면 대부분의 설명을  
객체지향이라는 문맥으로 옮겨올 수 있다. 이것이 많은 사람들이 객체지향을 설명하기 위해 실세계의 모방이라는 은유를 차용하는 이유이다.

### 역할과 책임을 수행하며 협력하는 객체들

객체지향 설계는 적절한 객체에게 적절한 책임을 할당하는 것에서 시작된다. 책임은 객체지향 설계의 품질을 결정하는 가장 중요한 요소다.  
책임이 불분명한 객체는 애플리케이션의 미래 역시 불분명하게 만든다. 얼마나 적절한 책임을 선택하느냐가 애플리케이션의 아름다움을 결정한다.

역할은 협력에 참여하는 객체에 대한 일종의 페르소나고, 관련성 높은 책임의 집합이다. 객체의 역할은 사람의 역할과 유사하게 다음과 같은 특징을 지닌다.

- 여러 객체가 동일한 역할을 수행할 수 있다.
- 역할은 대체 가능성을 의미한다.
- 각 객체는 책임을 수행하는 방법은 자율적으로 선택할 수 있다.
- 하나의 객체가 동시에 여러 역할을 수행할 수 있다.

역할은 유연하고 재사용 가능한 협력 관계를 구축하는 데 중요한 설계 요소다. 대체 가능한 역할과 책임은 객체지향 패러다임의 중요한 기반을 제공하는  
다형성과도 깊이 연관되어 있다.

## 협력 속에 사는 객체

객체지향을 객체지향이라고 부르는 이유는 패러다임의 중심에 객체가 있기 때문이다. 객체지향 애플리케이션의 아름다움을 결정하는 것이 협력이라면  
협력이 얼마나 조화를 이루는지를 결정하는 것은 객체다. 결국 협력의 품질을 결정하는 것은 객체의 품질이다.

협력 공동체의 일원으로서 객체는 다음과 같은 두 가지 덕목을 갖춰야 하며, 두 덕목 사이에서 균형을 유지해야 한다.

첫째, 객체는 충분히 `협력적` 이어야 한다. 객체는 다른 객체의 요청에 충실히 귀 기울리고 다른 객체에게 적극적으로 도움을 요청할 정도로 열린 마음을 지녀야한다.  
외부의 도움을 무시한 채 모든 것을 스스로 처리하려고 하는 전지전능한 객체는 내부 복잡도에 의해 자멸하고 만다.  
충분히 협력적이라는 말은 수동적인 존재를 의미하는 것은 아니다.  
다른 객체의 명령에 복종하는 것이 아니라 요청에 응답할 뿐, 어떤 방식으로 응답할지는 객체 스스로 판단하고 결정한다.  
요청에 응할지 여부마저 객체 스스로 결정할 수 있다.

둘째, 객체는 충분히 `자율적` 이어야 한다. '자율적' 이라는 단어의 뜻은 `자기 스스로의 원칙에 따라 어떤 일을 하거나 자기 스스로를 통제하여 절제하는 것` 을 의미한다.  
어떤 사물이 자신의 행동을 스스로 결정하고 책임진다면 우리는 그 사물을 자율적인 존재라고 말한다.  
객체 공동체에 속한 객체들은 공동의 목표를 달성하기 위해 협력에 참여하지만 스스로의 결정과 판단에 따라 행동하는 자율적인 존재다.  
객체지향 설계의 묘미는 다른 객체와 조화롭게 협력할 수 있을 만큼 충분히 개방적인 동시에 협력에 참여하는 방법을 스스로 결정할 수 있을 만큼  
충분히 자율적인 객체들의 공동체를 설계하는 데 있다.

### 상태와 행동을 함께 지닌 자율적인 객체

흔히 객체를 `상태(state)`와 `행동(behavior)`을 함께 지닌 실체라고 정의한다. 이 말은 객체가 협력에 참여하기 위해 어떤 행동을 해야 한다면  
그 행동을 하는 데 필요한 상태도 함께 지니고 있어야 한다는 것을 의미한다.  
객체가 협력에 참여하는 과정 속에서 스스로 판단하고 스스로 결정하는 자율적인 존재로 남기 위해서는 필요한 행동과 상태를 함께 지니고 있어야한다.

객체지향에서는 데이터와 프로세스를 객체라는 하나의 틀 안에 함께 묶어 놓음으로써 객체의 자율성을 보장한다.  
자율적인 객체로 구성된 공동체는 유지보수가 쉽고 재사용이 용이한 시스템을 구축할 수 있는 가능성을 제시한다.

### 협력과 메시지

풍부한 메커니즘을 이용해 요청하고 응답할 수 있는 인간들의 세계와 달리 객체지향의 세계에서는 오직 한 가지 의사소통 수단만이 존재하는데, 이것을 `메시지`라고 한다.  
한 객체가 다른 객체에게 요청하는 것을 메시지를 전송한다고 말하고 다른 객체로부터 요청을 받는 것을 메시지를 수신한다고 말한다.

객체는 협력을 위해 다른 객체에게 메시지를 전송하고 다른 객체로부터 메시지를 수신한다.  
객체지향의 세계에서 협력은 메시지를 전송하는 객체와 메시지를 수신하는 객체 사이의 관계로 구성된다.  
이때 메시지를 전송하는 객체를 `송신자(sender)`라고 부르고 메시지를 수신하는 객체를 `수신자(receiver)`라고 부른다.

### 메서드와 자율성

객체가 수신된 메시지를 처리하는 방법을 `메서드(method)` 라고 부른다.

객체지향 프로그래밍 언어에서 메서드는 클래스 안에 포함된 함수 또는 프로시저를 통해 구현된다.  
메시지를 수신한 객체가 실행 시간에 메서드를 선택할 수 있다는 점은 다른 프로그래밍 언어와 객체지향 프로그래밍 언어를 구분 짓는 핵심적인 특징 중 하나다.  
이것은 프로시저 호출에 대한 실행 코드를 컴파일 시간에 결정하는 절차적인 언어와 확연히 구분되는 특징이다.

외부의 요청이 무엇인지를 표현하는 메시지와 요청을 처리하기 위한 구체적인 방법인 메서드를 분리하는 것은 객체의 자율성을 높이는 핵심 메커니즘이다.  
이것은 `캡슐화(encapsulation)` 라는 개념과도 깊이 관련되어 있다.

## 객체지향의 본질

지금까지 설명한 내용을 종합해보면 객체지향의 개념은 다음과 같다.

- 객체지향이란 시스템을 상호작용하는 `자율적인 객체들의 공동체`로 바라보고 객체를 이용해 시스템을 분할하는 방법이다.  
- 자율적인 객체란 `상태`와 `행위`를 함께 지니며 스스로 자기 자신을 책임지는 객체를 의미한다.
- 객체는 시스템의 행위를 구현하기 위해 다른 객체와 `협력`한다. 각 객체는 협력 내에서 정해진 `역할`을 수행하며, 역할은 관련되 `책임`의 집합이다.
- 객체를 다른 객체와 협력하기 위해 메시지를 전송하고, `메시지`를 수신한 객체는 메시지를 처리하는 데 적합한 `메서드`를 자율적으로 선택한다.

### 객체를 지향하라

클래스가 객체지향 프로그래밍 언어의 관점에서 매우 중요한 `구성요소(construct)` 인 것은 분명하지만 객체지향의 핵심을 이루는 중심 개념이라고 말하기에는 무리가 있다.  
자바스크립트 같은 프로토타입(prototype) 기반의 객체지향 언어에서는 클래스가 존재하지 않으며 오직 객체만이 존재한다.  
프로토타입 기반의 객체지향 언어에서는 상속 역시 클래스가 아닌 객체 간의 위임(delegation) 메커니즘을 기반으로 한다.  
지나치게 클래스를 강조하는 프로그래밍 언어적인 관점은 객체의 캡슐화를 저해하고 클래스를 서로 강하게 결합시킨다.

훌륭한 객체지향 설계자가 되기 위해 거쳐야 할 첫 번째 도전은 코드를 담는 클래스의 관점에서 메시지를 주고받는 객체의 관점으로 사고의 중심을 전환하는 것이다.  
어떤 클래스가 필요한가가 아니라 어떤 객체들이 어떤 메시지를 주고받으며 협력하는가다. 클래스는 객체들의 협력 관계를 코드로 옮기는 도구에 불과하다.

클래스의 구조와 메서드가 아니라 객체의 역할, 책임, 협력에 집중해야 된다. 객체지향은 객체를 지향하는 것이지 클래스를 지향하는 것이 아니다.