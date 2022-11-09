# [React.js 공부 부분]

**리액트 인프런 강의 영상 사이트: https://www.inflearn.com/course/%EC%B2%98%EC%9D%8C-%EB%A7%8C%EB%82%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8/dashboard**
```
npm start
터미널에 이걸 입력해서 리액트 실행.

npx 관련 코드 사용해서 리액트 프로젝트 생성.

-------------------

< 증감 연산자 >

let a = 1;
let b = a++;

console.log(a, b);
// 출력결과: 2 1

let c = 1;
let d = ++c;

console.log(c, d);
// 출력결과: 2 2

// 참고로 c언어도 마찬가지이다.

-------------------

자바스크립트에서의 var let const 차이점:
https://velog.io/@marcus/2019-02-10-1702-%EC%9E%91%EC%84%B1%EB%90%A8

-------------------

a === b
(a가 b와 값과 자료형이 모두 같다)
// 만약 a=1, b='1'인데 a==b를 출력하면 true가 나오고, a===b를 출력하면 false가 나온다.

a !== b
(a가 b와 값이나 자료형이 같지 않다)

-------------------

< 함수 생성 방법 2가지 >

// function statement를 사용
function sum(a, b) {
    return a + b;
}

console.log(sum(10, 20));
// 출력 결과: 30

// arrow function expression을 사용 (화살표 함수 생성 방법)
const multiply = (a, b) => {
    return a * b;
}

console.log(multiply(10, 20));
// 출력 결과: 200

-------------------

React는 자바스크립트 라이브러리이다. 프레임워크가 아니다.

-------------------

JSX
=> 자바스크립트 확장판으로써, JavaScript + XML/HTML

예를들어 JSX 코드 예시로는,
const element = <h1>Hello, world!</h1>;

JSX 코드는 내부적으로 html과 xml코드를 javascript 로 변환하는 과정을 거친다.
그러므로 최종적으로는 javascript 코드가 나오게 되는 것이다.

만약 JSX 코드를 미사용 하고 순수한 javascript 코드로만 사용시,
이처럼 JSX 코드를 javascript 코드로 변환해주는 역할과 같은 역할을 하는것이,
React의 createElement 라는 함수이다.

React.createElement(
    type,
    [props],
    [...children]
)
// 여기 props 부분에는 자바스크립트 객체를 넣으면 된다고 한다. 그러면 해당 컴포넌트의 props가 된다고 한다.

- JSX 사용함 -
<div>Hello, {name}</div>
- JSX 사용 안함 -
React.createElement('div', null, 'Hello, ${name}');

- JSX 사용 예시 코드 -
const name = '현진';
const element = <h1>안녕, {name}</h1>;
ReactDOM.render(
    element,
    document.getElementById('root')
);
// html 코드 사용하다가 도중에 중간에 js코드를 사용하고 싶다면 {} 중괄호로 묶어 그 안에 js코드를 적어주면 된다.
// 이는 React element인 element를, Dom element (html element)인 <div id="root"></div> 부분에 렌더링 하는 코드이다.
// 참고로 이는 html 파일의 root dom node 부분인 <div id="root"></div> 안에 자동으로 렌더링하여 넣어져서 실행되어 사용되게 된다.
// 즉, 이 렌더링 과정은 virtual dom에서 실제 dom으로 이동하는 과정인 것이다.

- 함수 컴포넌트 및 JSX 사용 예시 코드 -
function Welcome(props) {
    return <h1>안녕, {props.name}</h1>;
}
const element = <Welcome name="인제" />;
ReactDOM.render(
    element,
    document.getElementById('root')
);
// 이처럼 Component 태그의 이름은 항상 대문자로 시작해야 한다.
// 참고로 헷갈리지 말아야할것은,
// 함수 컴포넌트인 function Welcome 안에서의 <h1>태그는 대문자로 시작하는게 아니니 사용여부를 잘 따져 구분하자.

-------------------

백틱 `: https://developerjm.tistory.com/25
사용법은 영문으로 ₩키를 누르면 된다.

-------------------

React element는 리액트의 virtual dom 에 존재하는 것이고,
Dom element는 실제 브라우저의 dom에 존재하는 것이다.
둘이 다른것이니 헷갈리면 안된다.

element는 생성후에 속성이나 children을 변경할수 없으므로,
새로운 element를 생성하여 바꿔치기하는 방식으로 변경한다.

-------------------

React component의 입력은 Props이고, 출력은 React element이다.
결국 React component가 해주는 역할은, 어떠한 속성들을 입력받아서 그에 맞는 화면에 나타날 element를 생성하여 return 해주는것이다.
마치 이를 객체지향에 비유하자면, Component는 클래스이고, element는 해당 클래스의 인스턴스 인것이다.

Props: 컴포넌트에 전달한 다양한 정보를 담고 있는 자바스크립트 객체이다.
Props의 Prop은 Property의 줄임말이다. 리액트에서는 속성이라는 뜻이다.
이 속성은 바로 React component의 속성이다.
즉, 컴포넌트에 어떠한 데이터를 전달하고 전달된 데이터의 내용에 따라 다른 모습의 element를 화면에 렌더링하고 싶을때, 해당 데이터를 props에 넣어서 그 props를 컴포넌트에 전달하여 새로운 element를 반환하여 출력하는 것이다.

참고로 Props 속성값을 다른 컴포넌트에서 직접 값을 할당해줄때, 문자열은 { }안에 적을 필요없이 " "안에 적어주면 된다.

내가 생각하기에,
component는 자바스크립트 함수처럼 틀로써, props라는 속성값 매개변수를 파라미터로 넣어주면, 각기 다른 element 결과가 반환되어 돌아오는것 같다.
즉, 다른 데이터로 element의 내용을 교체하여 새로운 element를 화면에 교체하여 띄워주고 싶을때 사용하는것 같다.
마치 비유하자면 함수가 component, 함수 파라미터가 props, return 반환값이 element 인것 같다.

모든 리액트 컴포넌트는 그들의 Props에 관해서는 Pure 함수 같은 역할을 해야한다.
즉, 모든 리액트 컴포넌트는 Props를 직접 바꿀수 없고, 같은 Props에 대해서는 항상 같은 결과를 보여주어야한다.

-------------------

컴포넌트를 추출할땐, 재사용성이 뛰어날수있도록 기능별 단위로 추출해주는것이 좋다.
재사용 가능한 Component를 많이 갖고 있을수록 개발 속도가 빨라진다.

-------------------

< chapter_05 / CommentList.jsx > (map함수의 구조와 객체 사용법을 위주로 보면 됨.)

import React from "react";
import Comment from "./Comment";

const alljsobjects = [
    {
        name: "사현진",
        comment: "제가 만든 첫 컴포넌트입니다. 참고로 댓글입니다.",
    },
    {
        name: "유재석",
        comment: "다른 사람 이름의 다른 댓글 적어보았습니다.",
    },
    {
        name: "홍길동",
        comment: "저도 리액트 배워보고 싶어요!",
    },
];

function CommentList(props) {
    return (
        <div>
            {  // 왼쪽의 이 중괄호는, 자바스크립트 문법 사용을 위하여, 자바스크립트 코드를 작성한 코드 부분 범위를 묶기위해 사용한것이다.
                alljsobjects.map(  // alljsobjects에 map 함수(메소드)를 실행(호출)할것이다.
                    (onejsobject) =>  // map 메소드를 실행할 매개변수는 onejsobject 이고, 이는 alljsobjects에서 소속된 객체를 하나씩 빼서 onejsobject라는 매개변수에 넣어줄 것이다.
                    {
                        return (
                            <Comment name={onejsobject.name} comment={onejsobject.comment} />
                        );
                    }  // 이 map 함수의 구조를 결론적으로 말하자면, map 함수의 매개변수는 onejsobject 이고, map 함수의 반환결과는 => 다음의 { } 중괄호 안의 부분이다.
                )  // map 함수의 범위가 여기까지이므로 닫아줌.
            }
        </div>
    );
}

/*
// 아래 코드가 원래 강의 내용의 변수명인데, 변수명이 다 비슷비슷해서 개념정리하는데 헷갈릴까봐 내가 위의 코드의 변수명으로 바꾸어 적어둠.
// 그리고 또한 위 코드에서는 map 함수의 구조가 잘 이해되지않을까봐 코드를 좀 넓게 분해해보았음.

const comments = [
    {
        name: "사현진",
        comment: "제가 만든 첫 컴포넌트입니다. 참고로 댓글입니다.",
    },
    {
        name: "유재석",
        comment: "다른 사람 이름의 다른 댓글 적어보았습니다.",
    },
    {
        name: "홍길동",
        comment: "저도 리액트 배워보고 싶어요!!",
    },
];

function CommentList(props) {
    return (
        <div>
            {comments.map((comment) => {
                return (
                    <Comment name={comment.name} comment={comment.comment} />
                );
            })}
        </div>
    );
}

*/

export default CommentList;

-------------------

setInterval() 함수는,
웹페이지의 특정 부분을 주기적으로 업데이트해줘야 하거나, 어떤 API로 부터 변경된 데이터를 주기적으로 받아와야 하는 경우가 있는데,
이럴 때는 자바스크립트의 setInterval() 함수를 사용할 수 있다.
즉, 어떠한 코드를 일정한 시간 간격을 두고 반복해서 실행하고 싶을 때 사용한다.
예를들어 실시간 시계를 나타낼때도 사용한다.
함수의 첫번째 인자로 실행할 코드를 담고 있는 함수를 받고, 두번째 인자로 반복 주기를 밀리초(ms) 단위로 받는다.
참고로 밀리초는 1000ms=1초 이다.

-------------------

< 리액트 클래스 컴포넌트의 특징과 구조, 생성자 메소드, state(상태) 에 대하여 >

클래스 컴포넌트는 extends로 React.Component 를 상속받는다.

클래스 컴포넌트 안에는 constructor(props) 라는 생성자 메소드가 들어가며,
그 생성자 메소드 안에는 super(props); 와 this.state = {}; 가 들어간다.

이러한 클래스 컴포넌트의 전체적인 구조는 대체적으로 밑과 같다.
class LikeButton extends React.Component {
    constructor(props) {
        super(props);

        this.state = {};
    }
}

상태인 state는 직접 수정하면 안된다.
예를들어
this.state = {
    name: 'shj'
};
이런식은 직접 수정이라 사용하면 안되고,
수정하고싶다면 예를들어
this.setState({
    name: 'shj'
});
이런식으로 반드시 setState 함수를 사용해야만한다. 참고로 이건 = 이 아니라, .setState로 메소드를 실행한것이다. 헷갈리지 말자.

-------------------

< 리액트 클래스 컴포넌트의 생명주기(라이프 싸이클) 특징과 구조와 메소드>

리액트 클래스 컴포넌트의 생명주기(라이프 싸이클)은
출생(Mounting), 인생(Updating), 사망(Unmounting) 으로 나뉜다.
즉, 리액트 클래스 컴포넌트는 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다는 것이다.

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
생명주기:      |             출생(Mounting)           |                  인생(Updating)                  |		           사망(Unmounting)
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
특징:         |  constructor 생성자 실행              |    New props 컴포넌트의 props 변경		      |   상위 컴포넌트에서 현재 컴포넌트들을 더이상 화면에 표시안할때 사망
             |  첫 state 정의                       |   setState() 함수 호출에 의해 state 변경		      |   사망 '직전'에 사망 생명주기 함수 호출
 	      |  렌더링되며 '이후'에 출생 생명주기 함수 호출  |    forceUpdate() 강제 업데이트 함수 호출로 다시 렌더링   |
	      |		            		   |    렌더링 '이후' 인생 생명주기 함수 호출		      |
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
생명주기 함수:  |  componentDidMount 함수		   |    componentDidUpdate 함수			      |   componentWillUnmount 함수
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

-------------------

< chapter_06 / NotificationList.jsx >
(클래스 컴포넌트 생성, constructor 생성자 메소드, state(상태), 생명주기 함수, const{} 변수 설명, setInterval()함수 사용법, 화살표 함수 생성 방법, setState() 함수 사용법을 위주로 보면 됨.)

import React from "react";
import Notification from "./Notification";

const reservedNotifications = [
    {
        message: "안녕하세요, 오늘 일정을 알려드립니다.",
    },
    {
        message: "점심식사 시간입니다.",
    },
    {
        message: "이제 곧 미팅이 시작됩니다.",
    },
];

var timer;

class NotificationList extends React.Component {  // 내생각엔 클래스 컴포넌트는 원래 React.Component를 상속받는것 같다.
    constructor(props) {  // constructor는 클래스 컴포넌트의 생성자 메소드이다.
        super(props);

        this.state = {  // 이처럼 클래스 컴포넌트의 state는 생성자 메소드 안에 적혀진다.
            notifications: [],
        };
    }

    componentDidMount()  // 리액트 클래스 컴포넌트의 라이프싸이클 생명주기에서, '출생,인생,사망' 중에서 출생부분임.
    {
        const { notifications } = this.state;  // const notifications = this.state.notifications; 와 같은 말임. 여기서 좌항의 notifications은 새로운 이름의 변수이고, 우항의 notifications은 state의 notifications을 뜻한다.
        // 위와 비슷한 예로, const { name, nickname } = state; 는, const name = state.name; const nickname = state.nickname; 이랑 같은 말이다. object 안에 존재하는 값을 바로 변수 할당 시켜주는것이다.
        timer = setInterval(  // setInterval 함수는, 어떠한 코드를 일정한 시간 간격을 두고 반복해서 실행하고 싶을 때 사용한다. 함수의 첫번째 인자로 실행할 코드를 담고 있는 함수를 받고, 두번째 인자로 반복 주기를 밀리초(ms) 단위로 받는다.
            () => {  // 화살표 함수 생성 방법중 매개변수가 없는 함수를 만드는법은, () => { statements }  // setInterval 함수의 첫번째 매개변수 인자 부분이다.
            if (notifications.length < reservedNotifications.length)  // 이 코드줄의 notifications는, state의 notifications가 아닌, 새롭게 선언된 변수인 notifications 이다.
            {
                const index = notifications.length;  // 이 코드줄의 notifications는, state의 notifications가 아닌, 새롭게 선언된 변수인 notifications 이다.
                notifications.push(reservedNotifications[index]);  // 이 코드줄의 notifications는, state의 notifications가 아닌, 새롭게 선언된 변수인 notifications 이다.

                this.setState({  // 클래스 컴포넌트에서 state를 업데이트하기위해서는 반드시 setState 함수를 사용해야만한다. 참고로 이건 = 이 아니라, .setState로 메소드를 실행한것이다. 헷갈리지 말자.
                    notifications: notifications,  // = state의 notifications: 새롭게 선언된 변수인 notifications
                });

            }
            else
            {
                clearInterval(timer);
            }
        }, 1000);  // 1000이 setInterval 함수의 두번째 매개변수 인자 부분이다.
    }

    render() {
        return (
            <div>
                {this.state.notifications.map((notification) => {  // 이 코드줄의 notifications는 state의 notifications 이고, notification은 map메소드의 사용을 위해 매개변수로 지정한 새로운 변수명이다.
                    return (
                        <Notification
                            message={notification.message}  // 이 코드줄의 notification은, state의 notifications 에서 추출한 map메소드의 매개변수이다.
                        />
                    );
                })}
            </div>
        );
    }
}

export default NotificationList;

-------------------

```
