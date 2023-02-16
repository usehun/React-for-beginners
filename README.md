# nomard - React for beginers

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

#### 2023-02-14 React 사용방법, 설정

#### 2023-02-16 React 기초문법, JSX 사용방법
