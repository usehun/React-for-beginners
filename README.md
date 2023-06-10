# nomard - React for beginners

### React 사용방법

    <script src=""></script>
    https://unpkg.com/react@17.0.2/umd/react.production.min.js
    https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js
    src 부분에 입력하면 React를 사용할 수 있게 해준다.

    React JS: 어플리케이션이 아주 인터랙티브하도록 만들어주는 library.
    React-dom: library 또는 package. 모든 react element들을 HTML body에 둘 수 있도록 해준다.
    ReactDOM.render() - render의 의미는 react element를 가지고 HTML로 만들어 배치한다는 것. 즉, 사용자에게 보여준다는 의미
    ReactDOM.render(span, span이 가야할 위치)
    -> 그래서 보통 body에 id=“root” 만들어서 span을 root 안에 두라고 함

    React.createElement("span", {span의 property}, “span의 내용”)
    -> property는 class name, id도 가능 style도 가능
    -> 참고만 하고 외우지 말기. 이렇게 쓸 일 없음

    바닐라JS는 HTML -> JS 순서
    리액트는 JS -> HTML 순서

    JS가 element를 생성하고 React JS가 그것을 HTML로 번역하는 것
    React JS는 업데이트 해야 하는 HTML을 업데이트 할 수 있음

### JSX 사용방법

    JSX
    - JavaScript 확장한 문법
    - HTML에서 사용한 문법과 유사한 문법으로 element생성할 수 있도록 해준다.
    - * 브라우저가 JSX 이해할 수 있도록 Babel 별도 설치 필요하다.
    - Babel : code transformer, JSX 코드를 브라우저가 이해할 수 있는 형태로 변경한다.
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">

    div에 const 넣기 위해선
    1. const를 함수로 만들어 줘야함 const Btn = () => ( );
    -> arrow function 이라고 부름
    = () => ( ); 는 function Btn() { return ( ); } 와 같음
    2. HTML 태그처럼 만들어서 넣어줌
    3. (중요) 컴포넌트의 첫 글자는 반드시 대문자여야 함
    -> 우리가 직접 만든 요소는 전부 대문자로 시작해야 함

    (컴포넌트 X) : ReactDOM.render(Container , root);
    (컴포넌트O) : ReactDOM.render(<Container />, root);

### State

    변수를 JSX에 전달하는 방법
    let counter = 0; 변수를 만들고
    Total clicks: {counter} 로 만들어주면
    변수의 카운터 숫자에 따라 변화됨

    onClick={countUp}
    -> 이벤트리스너가 countUp 함수를 호출하고 countUp은 카운트를 바꿔줌

    ReactDOM.render()로 container 처음 랜더링 할 때 카운터가 0이므로 0으로 호출됨
    그리고 container를 리렌더링을 해줘야 카운터가 +1 상태로 업데이트 됨.
    즉, countUp을 호출할 때마다 ReactDOM.render()을 다시 호출해야함
    -> countUp에 ReactDOM.render( ) 넣어주기

### State Functions

    state를 세팅하는 데는 2가지 방법이 있다.
    (1) 직접 할당 :setState(state +1)
    (2) 함수를 할당:setState(state => state +1) (함수의 첫번째 인자는 현재 state 이다)

    현재 state랑 관련이 없는 값을 새로운 state로 하고싶은 경우에는 (1),
    현재 state에 조금의 변화를 주어서 새로운 state를 주고 싶은 경우에는 (2)

    Flip
    const onFlip = () => setFlipped(!flipped);
    -> flipped가 true라면 부정명제인 !flipped는 false
    -> false라면 true

    state값으로 input을 enabled할지 disabled 할지를 결정할 수 있음

    useState의 두번째 인자인 modifier함수를 실행하면 해당 컴포넌트가 리렌더링 된다.

    [리렌더링 조건]
    (1) props이 바뀔때
    (2) state가 바뀔때
    (3) 부모 컴포넌트가 리렌더링 될 때

### Props Functions

    컴포넌트화 재사용
    프로젝트 진행하다보면 디자인가이드가 나와서 디자인은 똑같은 컴포넌트인데 내용만 달라지는 경우 있음. 그때마다 버튼을 계속 만들기보다 재사용가능한 버튼을 만드는 것이 좋음.
    Props속성 사용하면 부모 컴포넌트에서 자식 컴포넌트에 데이터 전달할 수 있으므로 내용만 다른 버튼 생성 가능

    1. props에 function도 보낼 수 있음
    이것은 JSX로 html 태그 자체에 이벤트 리스너를 넣는것과는 전혀 다른 것임.
    그저 이벤트를 실행시키는 함수가 프로퍼티로 들어간 것임.
    prop은 그냥 부모에서 자식으로 데이터를 넘길 때 사용하는 argument의 역할이니까!

    2. 부모의 상태를 바꾸는 함수를 만들었고, 부모 컴포넌트에서 그 함수를 props으로 보내면 자식 컴포넌트에서 그 함수가 실행된다.

    3. 불필요한 re-render는 React.memo()로 관리할 수 있음
    부모 컴포넌트의 state를 변경하면 당연히 그 자식 컴포넌트들도 Re-render가 일어남. 불필요한 렌더링이 발생할 수도 있는데, 이 경우에는 React.memo()로 prop의 변경이 일어난 부분만 렌더링 시킬 수 있음. 아주 많은 자식 컴포넌트를 가지고 있는 부모 컴포넌트일 때 사용하면 될듯.

    * React.memo()
    컴포넌트가 React.memo()로 wrapping 될 때, React는 컴포넌트를 렌더링하고 결과를 메모이징(Memoizing)한다. 그리고 다음 렌더링이 일어날 때 props가 같다면, React는 메모이징(Memoizing)된 내용을 재사용한다.

    1.리액트는 파라미터를 잘 못 넘겨도 확인할 수 없는 문제점이 존재한다.
    2. 이런 문제를 줄이기 위해서 PropTypes라는 모듈의 도움을 받을 수 있다.
        => https://unpkg.com/prop-types@15.7.2/prop-types.js
    3. type과 다르게 입력 되엇을 경우 warning을 뜨게 할수 있고, parameter 에 값을 넣지 않는 경우 경고 메시지를 띄울수 있다.

#### 2023-05-16 Props 기능

#### 2023-05-11 State 기능

#### 2023-02-17 State 사용방법

#### 2023-02-16 React 기초문법, JSX 사용방법

#### 2023-02-14 React 사용방법, 설정
