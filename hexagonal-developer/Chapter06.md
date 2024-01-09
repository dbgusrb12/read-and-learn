# 리팩터링

## 수정 공포와 변경 비용

레거시는 오래되었지만 여전히 사용되고 있는 코드를 말한다.   
개발자는 레거시에 대해 많은 부담을 갖는다.

개발자는 왜 레거시에 부담을 느낄까?  
다음은 레거시에서 나타나는 흔한 특성이다.

- 긴 클래스, 긴 메서드
- 복잡한 코드
- 이상한 이름
- 많은 중복
- 테스트 코드 없음

이러한 특성은 코드 수정을 어렵게 만든다.  
이 상태에서 새로운 요구가 들어온다면, 요구를 충족하기 위해 기존 코드를 분석해야 한다.  
하지만 일정상의 여유가 없기 때문에 코드를 완벽하게 이해하지 못한 상태에서 코드를 수정해야한다.  
테스트 코드도 없기 때문에 수정한 코드가 기존 기능에 어떤 영향을 끼칠지도 알 수 없다.

당연히 이런 상황에서 기존 코드 수정은 매우 두려운 일이 된다.  
동작하는 코드는 건들지 않고 기존 코드에 새 코드를 덧댄다.  
기존 코드를 복사해서 붙여넣기 한 다음 일부 코드만 수정하거나, if-else 블록 안에 새로운 if-else 블록을 중첩하는 식으로 말이다.  

이러한 작업은 코드를 더 길고 복잡하게 만든다.  
중복 코드도 늘어나고 이상한 이름도 그래도 사용하기 때문에 레거시 코드를 더 이해하기 어렵게 만든다.  
악순환이 반복되고 레거시 수정에 대한 공포는 더욱 증폭된다.

코드 수정이 힘든 레거시는 피하고 싶지만 우리는 누구나 레거시를 만난다.  
10년 전에 만들어져 지금까지 운영 중인 시스템이나, 남들은 쓰지 않은 기술을 사용한 시스템을 만날 때도 있다.  
불과 몇 달 전에 내가 만든 코드라도 수정하기 두렵다면 그게 바로 레거시이다.

## 리팩터링

리팩터링은 외부로 드러나는 동작이나 기능을 변경하지 않고 내부 구조를 변경해서 재구성하는 기법이다.  
리팩터링은 새로운 기능을 추가하거나 기존 기능을 개선하지 않기 때문에 겉으로 드러나는 이점이 없다.  
하지만 장기적 관점에서는 이점이 생긴다.  
코드 가독성이 높아지고 리팩터링 이전보다 구현 변경과 확장이 용이해진다.  
이러한 변화는 단기적으로 수정 비용을 낮춰주고 장기적으로는 개발 비용을 줄여준다.

내부 구현을 변경했는데 다르게 동작하면 안 되기 때문에 리팩터링을 하고 나면 기존과 동일하게 동작하는지 확인해야 한다.  
코드를 수정할 때 마다 수동으로 확인하다 보면 시간이 오래 걸리고 특정 조건에서의 검증을 놓치기 쉽다.  
따라서 테스트 코드를 사용해서 검증하는게 좋다.

물론 레거시 코드에 대한 테스트 코드를 만드는 게 쉽지는 않지만,  
테스트 코드를 만들고 나면 리팩터링을 더욱 안전하게 진행할 수 있다.

경우에 따라 코드를 수정하지 않고서는 테스트 코드를 만들 수 없을 때도 있다.  
테스트 코드 없이 리팩터링을 하면 부담될 것이지만 리팩터링을 하지 않는 것보다 하는게 낫다.  
테스트 코드를 만들지 못해도 리팩터링은 시도해야 한다.  
현재의 위험을 회피하다 보면 미래에 더 큰 위험으로 다가오기 때문이다.

### 미사용 코드 삭제

가장 쉽지만 가장 부담되는 리팩터링이 코드 삭제이다.  
삭제 대상이 될 수 있는 흔한 예가 주석 처리된 코드이다.  

사용하지 않는 변수 삭제도 가장 쉽게 할 수 있는 리팩터링이다.  
개발 도구로 사용하지 않는 변수를 쉽게 확인할 수 있다.  
변수가 많을수록 코드를 분석하는데 더 많은 시간이 소요되므로 변수는 적을수록 좋다.

메서드와 클래스를 삭제할 때는 리플렉션으로 접근하는 코드인지 확인해 봐야 한다.

### 매직 넘버

매직 넘버는 그 값이 무엇을 의미하는지 유추하기 어렵기 때문에 정확하게 코드 의미를 이해하려면 여러 다른 요소를 함께 분석해야 한다.

상수나 열거 타입을 사용해서 이름을 부여하는 방법으로 특정 값의 의미를 드러낼 수 있다.  
의미가 드러가는 이름을 사용하면 코드 가독성이 높아지고 분석 시간이 줄어든다.

### 이름 변경

보이는 이름과 실제 의미가 일치하지 않으면 코드를 분석할 때 혼란을 겪게 된다.

이름 변경은 가장 쉬우면서도 개발 도구가 가장 잘 지원하는 리팩터링이기도 하다.  
의미가 잘 드러나지 않는 이름을 만나면 좀 더 알맞은 이름으로 변경하는 시도를 지속해보자.  
그만큼 코드 가독성이 좋아진다.

### 메서드 추출

이름 변경 다음으로 많이 하는 리팩터링은 메서드 추출이다.  
메서드 추출을 잘 활용하면 코드 가독성이 높아진다.

메서드 추출은 관련 코드를 묶어서 별도 메서드로 추출하는 방법이다.  
논리적으로 하나의 작업을 수행하는 코드를 대상으로 한다.  
추출한 메서드에 알맞은 이름을 부여함으러써 가독성이 좋아지고,  
관련 코드가 한 메서드에 모이면서 코드도 더 응집된다.

메서드를 추출하기 좋은 대상은 if-else 의 각 블록에 있는 코드이다.

메서드 추출 리팩터링의 매력에 빠져들면 코드가 길든 짧든 메서드를 추출하고 싶은 욕구에 사로잡힐 수 있다.  
하지만 무턱대고 메서드를 추출하면 안된다.  
가독성이나 응집도가 좋아지는 방향으로 메서드를 추출해야 한다. 과할 정도로 메서드 추출을 많이 하면 오히려 코드 분석이 어려워질 수도 있다.  
조금은 부족해 보이더라도 메서드가 비교적 의미를 잘 드러내고, 코드를 자연스럽게 읽을 수 있다면 적정선에서 메서드 추출을 멈춰도 괜찮다.

### 클래스 추출

메서드를 중첩하여 추출하는 과정에서 파라미터로 값을 전달하는 과정이 복잡해진다면,  
메서드 추출 대신 클래스 추출을 고려해 볼 수 있다.

로직을 클래스로 추출하면 해당 로직만 따로 테스트할 수 있는 이점도 생긴다.

### 클래스 분리

한 클래스에 많은 기능이 모여 있으면 각 기능을 별도 클래스로 분리한다.  
기능을 분리할 때는 한 번에 다 하기보다 한 기능씩 점진적으로 진행한다.

클래스 추출과 마찬가지로 분리한 클래스는 코드 줄 수가 줄어들고  
한 기능에 초점을 맞추고 있기 때문에 후속 리팩터링이 쉬워진다.

### 메서드 분리

서로 다른 기능을 한 메서드에 구현하면 유사한 if-else 가 곳곳에 생겨 코드가 복잡해지고 실행 흐름 추적이 어려워진다.  
이 상태에서 메서드 추출같은 리팩터링을 하면 가독성은 개선되지 않고 구조만 더 복잡해질 수 있다.  
이렇게 메서드가 완전히 구분되는 기능을 구현하고 있는 경우에는  
각 기능을 구현하는 메서드를 따로 만들고 분리해서 기능별로 응집도를 높여야한다.

메서드를 분리할 때는 다음 순서대로 진행한다.

1. 두 기능 중 한 기능을 위한 메서드를 추가한다. 이 메서드는 내부에서 기존 메서드를 호출한다.
2. 기존 메서드를 호출하는 코드가 새 메서드를 호출하도록 변경한다.
3. 기존 메서드의 코드를 새 메서드로 이동한다.
4. 이름을 변경한다.
5. 코드를 정리한다.

메서드를 분리하고 이어서 클래스 분리 리팩터링을 해서 코드 응집도를 더 높일 수 있다.

### 파라미터값 정리

메서드에서 사용하지 않는 파라미터 데이터는 제거해야 한다.  
사용하지 않는 파라미터값은 코드 분석을 어렵게 만들기 때문이다.  
파라미터의 특정 값이 실제로 사용되는지 확인하려면  
메서드 자체와 그 메서드가 같은 파라미터를 사용해서 호출하는 메서드까지 흐름에 따라 모든 코드를 뒤져야한다.  

한 타입을 한 메서드에서만 파라미터로 사용할 경우 상대적으로 사용하지 않는 값을 삭제하기 쉽다.  
문제는 여러 메서드에서 한 타입을 파라미터로 사용할때 발생한다.  
여러 메서드가 한 타입을 파라미터로 사용하면 자연스럽게 특정 메서드에서만 필요로하는 값이 타입에 추가된다.

파라미터값을 정리하는 과정은 다음과 같다.

1. 메서드 상단에 새 타입을 사용한 객체 생성
2. 메서드가 새 타입 객체를 사용할 때 까지 다음 반복
    - 메서드에서 사용하는 파라미터 프로퍼티를 새 타입 객체에 추가
    - 메서드에서 새 타입 객체의 프로퍼티를 사용하도록 변경
3. 새 타입 객체를 생성하는 부분을 뺀 나머지를 별도 public 메서드로 추출
4. 메서드 호출을 인라인 처리
5. 과정 3에서 추출한 메서드 이름을 원래 메서드 이름으로 변경

### for 에서 하는 2자기 일 분리

코드를 작성하다 보면 하나의 for 문에서 한 번에 여러 일을 처리하고 싶을 때가 있다.  
for 문을 두 번 실행하는 것보다 한 번만 실행하는 게 효율적으로 느껴지기 떄문이다.

이렇게 하나의 for 문에서 여러 가지 작업을 실행하면 서로 다른 목적을 가진 코드가 뒤섞일 수 있다.  
서로 다른 목적의 코드가 뒤섞이면 코드 복잡도가 증가하고 코드를 이해하기가 어려워진다.

for 문이 복잡해지지 않게 방지하는 방법의 하나는 for 루프가 1개의 일만 하도록 수정하는 것이다.  
for 문이 하는 일을 논리적인 단위로 분리하면 다음과 같은 이점이 생긴다.

- 코드가 복잡해지지 않고 논리적인 단위로 구분된다.
- 논리적인 단위로 구분되어 코드를 이해하기 쉽다.
- 메서드 추출과 같은 리팩터링이 용이하다.
- 다른 로직을 추가하기가 용이하다.

루프를 여러 번 돌게 되면 성능이 느려진다고 걱정하는 개발자도 있다.  
하지만 미리 걱정할 필요는 없다. 대부분 성능에 문제가 없기 떄문이다.  
정말로 문제가 될 때만 측정해서 개선하면 된다.  
복잡한 코드보다 이해하기 좋은 코드가 주는 이점이 훨씬 크다.

## 리팩터링 VS 새로 만들기

리팩터링은 기존 코드를 점진적으로 개선한다.  
리팩터링으로 조금씩 코드를 개선하다 보면 어느새 코드 품질이 확연히 좋아진다.  
하지만 코드 품질을 개선하는 방법이 리팩터링만 있는 것은 아니다. 새로 만드는 방법도 있다.

새로 만드는 방법 중 하나는 일부 기능을 마이크로서비스로 분리하는 것이다.  
일부 기능만 새로 만들기 때문에 전체를 새로 만드는 것보다 위험 부담이 적다.  
단 프로세스가 분리되기 때문에 데이터 동기화나 통신 실패 같은 기존에 겪지 않았던 다른 문제에 직면할 수 있다.  
새로 만들 때의 단점보다 이점이 더 클 때 개선의 방법으로 마이크로서비스를 선택해야 한다.

또한 새로 만든다고 코드가 좋아진다는 법은 없다.  
좋은 코드를 만드는 방법을 알아야 코드 품질이 좋다진다는 사실을 꼭 기억하자.