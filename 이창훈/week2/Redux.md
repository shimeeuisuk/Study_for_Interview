# 리덕스 상태관리

## 

## FLUX에 대해서 설명하세요.

FLUX패턴은  MVC패턴과 다르게 단방향으로 데이터가 흐른다. 


## 리덕스에 대해서 설명하세요

Redux는 상태관리 라이브러리다.



## 관심사의 분리(Separation of Concerns)원칙
SoC 법칙이란 시스템 요소가 단일 목적이고 배타성을 가져야 한다는 것을 명시한다. 
그 말은, 어떤 요소도 다른 요소와 책임을 공유하면 안 되고, 그 요소와 관계가 없는 책임을 포함시킬 수 없다는 것이다.

'가능한 모든 것들을 단순하게 만들어라. 더 단순하게가 아니라.'

SoC는 질서에 관한 것이다. SoC의 종합적인 목표는 각각의 파트가 의미있고 직관적인 롤을 수행하지만 변화에 적응하는 능력을 극대화시킨, 잘 조직된 시스템을 설립하는 것이다.




## MVC패턴

(Model-View-Controller)패턴
MVC패턴은 **양방향 데이터 흐름**을 가진 개발 디자인 패턴으로, 애플리케이션을 3가지의 부분으로 나누어, 각각의 부분이 독자적인 처리를 행하도록 하는 디자인 패턴을 말한다.


- Model : 데이터를 관리하고 변환, 처리하는 역할

- View : Model의 상태를 참조하여 사용자에게 눈에 보이는 형태로 표시, 렌더링하는 역할. 인터페이스의 역할을 하기 때문에 떄떄로 사용자로 부터 데이터를 입력 받기도 한다.

- Controller : 유저로부터 입력(Action)을 받아, Model과 View에게 데이터를 변환, 업데이트하도록 지시하는 역할

MVC 패턴은 양방향 데이터 흐름을 가졌다.

Model이 변경되면 View가 변경되며, 유저에 의해 View에서 의도치 않게 Action이 일어난다면 데이터를 관리하고 변환, 처리하는 역할을 가진 Model은 View로 부터의 데이터 또한 처리해야한다.

중요한 문제는, MVC 패턴에서 애플리케이션의 규모가 커지면 커질 수록 애플리케이션의 구조가 아주 복잡해진다는 것이다. 

애플리케이션의 규모가 커질수록 한 개의 Model이 여러 개의 View를 조작하거나, 한 개의 View가 여러 개의 Model을 조작하기 되는 등 버그를 감지하기 어려워지코 데이터 흐름을 추적하는 것에 괴장한 비용이 들게 된다. 