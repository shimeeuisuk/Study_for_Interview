## hook의 규칙
함수형 컴포넌트에서도 클래스형 컴포넌트의 기능을 사용할 수 있게 하는 기능이다. 
훅을 통해 함수형 컴포넌트에서도 컴포넌트 상태값을 관리할 수 있고, 컴포넌트의 생명 주기 함수를 이용할 수 있다.

## 장점
재사용 가능한 로직을 쉽게 만든다.
훅은 단순한 함수 이므로 함수 안에서 다른 함수를 호출하는 것으로 새로운 훅을 만들 수 있기 때문이다. 


## hook의 종류와 특징을 설명해보세요
기본 훅
- useState(동적 상태 관리)
  - 함수형 컴포넌트에서 가변적인 상태를 지닐 수 있게 해 준다. 
  - 함수형 컴포넌트의 상태 관리에 사용된다.


- useEffect(side effect 수행 - mount / unmount / update)
  - 리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 수행하도록 설정할 수 있는 hook이다.
  - 클래스형 컴포넌트의 componentDidMount와 componentDidUpdate, componentWillUnmount를 합친 형태로 볼 수 있다.
  - 이 훅을 통해서 함수형 컴포넌트에서 사이드 이펙트를 수행할 수 있따.
  - 여기서 사이드 이펙트는 데이터 가져오기, 구독 설정, 수동으로 DOM 조작등을 말한다.
  - useEffect는 리액트에서 컴포넌트 렌더링 이후 어떠한 일을 수행해야 하는지 말해준다. 
  - 

- useContext(컴포넌트를 중첩하지 않고도 전역 값 쉽게 관리)

추가 훅
- useReducer


- useCallback
  - useCallback은 메모이제이션 된 콜백을 반환한다. 주로 렌더링 성능 최적화 해야 하는 상황에서 사용하는데, 이 Hook을 통해서 이벤트 핸들러 함수를 필요할 때만 생성할 수 있다. 

- useMemo
  - useMemo를 사용하면 함수형 컴포넌트 내부에서 발생하는 연산을 최적화 할 수 있다. 
  - 이 Hook은 메모이제이션된 값을 반환한다. 
  - useMemo는 의존성이 변경되었을 때만 메모이제이션 된 값을 다시 계산한다. 
  - 이 최적화는 모든 렌더링 시 고비용 계산을 방지하게 해준다.


- useRef
  - useRef는 함수형 컴포넌트에서 ref를 쉽게 사용할 수 있도록 해준다. 
  - useRef는 .current 프로퍼티로 전달된 인자로 초기화된 변경 가능한 ref 객체를 반환한다.

- useImperativeHandle
- useLayoutEffect
- useDebugValue

커스텀 훅

## Hook 사용 규칙

1. 최상위에서만 hook을 호출
 - React 함수(컴포넌트)의 최상위에서만 Hook을 호출 할 것
 - 반복문, 조건문, 중첩된 함수등에서 호출하면 안됩니다.
2. React 함수에서만 hook을 호출
  - Custom Hook에서는 호출 가능하다.
  - 일반적인 JavaScript 함수에서는 호출 할 수 없습니다. 
3. Hook을 만들때 앞에 use 붙히기
  - 
4. React는 Hook 호출되는 순서에 의존한다.
  - 한 컴포넌트에서 여러 개의 hook이 사용되는 경우
  - hook은 위에서부터 어래로 순서에 맞게 동작한다. 

### useState




## useMemo 와 useCallback의 차이에 대해 설명하세요
[참조](https://narup.tistory.com/273)

## Memoization
메모이제이션은 기존에 소행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법이다.
이것을 활용하면 중복 연산을 피할 수 있다. 

## useMemo
**useMemo는 메모이제이션된 값을 반환하는 함수이다.**

```jsx
useMemo(()=>fn, [dep])
```
여기서 dep으로 지정한 값이 변하면 함수를 실행하고, 그 함수의 반환 값을 반환해 준다.

## useMemo를 사용하는 이유
컴포넌트의 state 값이 변하면 리렌더링이 일어난다.

ex 값이 변할 경우에만 연산을 실행할 수 있도록 useMemo를 사용한다 그 결과, 리렌더링이 발생할 경우, 특정 변수가 변할 떄에만 useMemo에 등록한 함수가 실행되도록 처리하면 
불필요한 연산을 하지 않게 된다.

## useCallback
**useCallback 메모이제이션된 함수를 반환 합니다.**
```jsx
useCallback(fn, [dep])
```
useCallbackdms dep의 값이 변하면 fn에 등록한 함수를 반환하는 기능을 가지고 있다. 

## useCallback의 사용처
1) 자식 컴포넌트에 props로 함수를 전달할 경우
2) 외부에서 값을 가져오는 api를 호출하는 경우

## 자식 컴포넌트에 props로 함수를 전달할 경우
함수는 값이 아니라 참조로 비교된다. 
컴포넌트에서 특정 함수를 정의할 경우 각각의 함수들은 모두 고유한 함수가 된다.
이런 고유한 함수가 생성될 경우, 부모를 통해 props에 함수를 전달받는 자식 컴포넌트에서는 props가 변경되었다고 판단해 리렌더링이 발생하게 된다. 
useCallback을 사용하지 않을 경우, name이 변경되어 리렌더링이 발생하면 매번 함수가 새로 만들어지고, props로 전달되는 함수가 새로 전달되게 된다.
부모컴포넌트만 수정하려고 했지만 연쇄적으로 하위 컴포넌트들 모두 렌더링이 일어나게 된다. 


## 외부에서 값을 가져오는 api를 호출하는 경우