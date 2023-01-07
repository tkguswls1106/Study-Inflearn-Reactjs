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

자바스크립트에서의 객체와 배열 설명 참고 사이트:
https://www.zerocho.com/category/JavaScript/post/572c6f759a5f1c4db2481ee3

배열은 선언할때 [] 사용.
객체는 선언할때 {} 사용.

객체 예시로
var hello = {
  firstName: 'Zero',  // 'firstName': 'Zero' 도 가능함. 그러면 호출할때 hello['firstName']과 hello.firstName 모두 가능함. 키에 띄어쓰기 없으면 웬만하면 마침표 방법으로 호출함.
  lastName: 'Cho',  // 'lastName': 'Zero' 도 가능함. 그러면 호출할때 hello['lastName']과 hello.lastName 모두 가능함. 키에 띄어쓰기 없으면 웬만하면 마침표 방법으로 호출함.
  'other Name': 'shj'  // 키에 띄어쓰기 있으므로 other Name: 'shj' 은 불가능함. 그러면 호출할때 hello['other Name'] 으로만 가능함. 마침표 호출방법은 불가능함.
};

단, 만약 props. 같은 말이 추가로 붙어있다면 []이걸로 호출하자.
예시로
hello[props.whatchoose] 이렇게 말이다.
hello.props.whatchoose 는 불가능하다.

map메소드는 배열에서 사용하므로, 이를 응용하면
배열 안의 각 인덱스에 속해있는 객체를 꺼내 사용할 수 있다.
예시로
const students = [
    {
        id: 1,
        name: "Inje",
    },
    {
        id: 2,
        name: "Steve",
    },
];
이처럼 배열[]안에 객체{}가 들어있다면, 배열student를 map메소드로 돌려 각 객체를 뽑아 사용 가능하다. 그 예시로
students.map( (student) => {return <li key={student.id}>{student.name}</li>;} )
이런식으로 말이다.
꼭 괄호생김새를 잘 구분하자.

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
생명주기:      |             출생(Mounting)           |                  인생(Updating)                   |		           사망(Unmounting)
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
특징:         |  constructor 생성자 실행              |    New props 컴포넌트의 props 변경		      |   상위 컴포넌트에서 현재 컴포넌트들을 더이상 화면에 표시안할때 사망
             |  첫 state 정의                       |   setState() 함수 호출에 의해 state 변경		      |   사망 '직전'에 사망 생명주기 함수 호출
 	      |  렌더링되며 '이후'에 출생 생명주기 함수 호출  |    forceUpdate() 강제 업데이트 함수 호출로 다시 렌더링   |
	      |		            		       |    렌더링 '이후' 인생 생명주기 함수 호출		      |
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
생명주기 함수:  |  componentDidMount 함수		      |    componentDidUpdate 함수			      |   componentWillUnmount 함수
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

참고로 생명주기 함수는 요즘은 잘 쓰이지 않는 클래스 컴포넌트에서만 쓰여 흐름과정 외에는 잘 몰라도 괜찮지만,
state(상태)는 반드시 잘 알아야만 한다.

-------------------

< 함수 컴포넌트의 Hooks훅 이란? >

클래스 컴포넌트에서는 state와 생명주기를 사용하여 원하는 시점에 원하는 출력이나 코드를 사용할 수 있지만,
함수 컴포넌트에서는 state와 생명주기를 사용할 수 없어, 이러한것을 대체하여 사용할 수 있게해준것이 Hooks이다.

훅Hooks를 사용할때에는 앞에 use를 붙여주어야한다.
예를들어 state를 사용하기 위한 Hook은, useState() 이다.
그리고 생명주기 사용을 위한 Hook은, useEffect() 이다.

-------------------

< useState() 사용법 >
const [변수명, set함수명] = useState(초기값);

< useState() 사용법 예시 코드 >
import React, { useState } from "react";

function Counter(props) {
    const [count, setCount] = useState(0);  // 만약 이걸 var count = 0; 이렇게 적었다면, count값은 클릭때마다 1씩 올라가긴하지만, 렌더링이 되지않아 화면에 출력값은 그대로 변하지않는다. 그래서 함수 컴포넌트에서 state를 사용하기위해 Hook훅을 사용한것이다.

    return (
        <div>
            <p>총 {count}번 클릭했습니다.</p>
            <button onClick={() => setCount(count + 1)}>
                클릭
            </button>
        </div>
    );
}

-------------------

훅Hook 중에서 side effect라는 렌더링시 변경 시점 접근인 생명주기를 함수 컴포넌트에서 사용할 수 있도록 해주는것이 useEffect() 이다.
주로 의존성 배열의 값이 변경될때, 이펙트 함수 부분이 실행된다.

< useEffect() 사용법 >
useEffect(이펙트 함수, 의존성 배열);  // 출생(mount)과 인생(update) 시점에, 해당 생명주기 함수와 동일한 시점에 실행된다.
useEffect(이펙트 함수, []);  // []으로 배열이 비었으므로 의존성 배열이 변경될수 없기때문에 어떤값에도 의존하지않아, 출생(mount)과 사망(unmount) 시점에 각각 단 한번씩, 해당 생명주기 함수와 동일한 시점에 실행된다.
useEffect(이펙트 함수);  // 의존성 배열을 생략하면 컴포넌트가 업데이트될 때마다 이펙트 함수가 호출된다. 즉, 출생(mount)과 인생(update) 시점에, 해당 생명주기 함수와 동일한 시점에 실행된다.

만약 useEffect() 함수 내부에 return 문이 들어있다면, 해당 return 부분은 컴포넌트가 마운트 해제인 unmount 될때 호출된다. 즉, 사망(unmount) 시점에, 해당 생명주기 함수와 동일한 시점에 실행된다.
참고로 return문이 없을수도 있다. 반드시 존재해야하는건 아니므로 주의하자.

< useEffect() 사용법 예시 코드 >
import React, { useState, useEffect } from "react";

function Counter(props) {

    ... 생략

    useEffect(() => {  // 의존성 배열 생략했으므로, 처음 mount와 update 될때마다 이펙트 함수 실행함. 참고로 여긴 return문 없으므로 unmount때는 생각하지 않는다.
        document.title = `총 ${count}번 클릭했습니다.`;  // 이펙트 함수
    });

    useEffect(() => {  // 의존성 배열 생략했고 useEffect() 내부에 return문 존재함.
        ServerAPI.subscribeUserStatus(props.user.id, handleStatusChange);  // 이부분을 처음 mount와 update 될때마다 이펙트 함수 실행함.
        
        return () => {
            ServerAPI.unsubscribeUserStatus(props.user.id, handleStatusChange);  // 이 부분은 useEffect() 내부의 return문이므로, 이 부분은 unmount때 실행된다.
        };
    });

    ... 생략

    return isOnline ? '온라인' : '오프라인';  // 이 코드줄은 위의 useEffect() 외부의 return문이므로, 생명주기와는 전혀 관계없다는걸 보여주기위해 적어본 것이다.
}

< useEffect() 사용법 구조와 설명 >
useEffect(() => {
    // 컴포넌트가 마운트 된 이후,
    // 의존성 배열에 있는 변수들 중 하나라도 값이 변경되었을 때 실행됨
    // 의존성 배열에 빈 배열[]을 넣으면 마운트와 언마운트시에 단 한 번씩만 실행됨
    // 의존성 배열 생략 시 컴포넌트 업데이트 시마다 실행됨
    ...

    return () => {
        // 컴포넌트가 마운트 해제되기 전에 실행됨
        ...
    }
}, [의존성 변수1, 의존성 변수2, ...]);

<<< 위의 내용이 애매해서 구글링기준과 내기준으로 useEffect() 사용법을 한번더 적어보겠음. >>>
useEffect(이펙트 함수, 의존성 배열);  // 출생(mount)과, '의존성 배열의 요소 값 변경'시 인생(update) 시점에 실행.
useEffect(이펙트 함수, []);  // 출생(mount) 시점에만 실행.
useEffect(이펙트 함수);  // 출생(mount)과, '함수 컴포넌트 리렌더링'시 인생(update) 시점에 실행.
useEffect() 함수 내부의 return 문  // 해당 return 부분은 컴포넌트가 마운트 해제인 사망(unmount) 시점에 실행.
// 참고로 대표적인 3가지 리렌더링의 조건으로는,
// 1. 컴포넌트의 state가 변했을때 (예를들어 useState() 적용한 set함수의 변수값이 변경되었을때)
// 2. props의 값이 변했을때
// 3. 부모 컴포넌트가 렌더링 되었을때

-------------------

< 훅Hook의 useMemo() >

렌더링시 그 렌더링하는 시점에 사용된다.

useMemo(() => fn, deps)
useMemo()는 deps 가 변한다면, () => fn 이라는 함수를 실행하고, 그 함수의 반환 값을 반환한다.
즉, 메모이제이션된 '값'을 반환한다.

useMemo(() => {console.log(ex)}, [ex]);  // useMemo() 그대로 사용하기
useMemo()는, 뒷매개변수인 의존성 배열의 값이 변하면, 앞매개변수의 함수를 실행한다.

< 훅Hook의 useCallback() >

렌더링시 그 렌더링하는 시점에 사용된다.

useCallback(fn, deps)
useCallback()는 deps 가 변한다면, fn 이라는 '새로운' 함수를 반환한다.
즉, 메모이제이션된 '함수'를 반환한다.

useMemo()는 그냥 함수를 실행해버리는 반면, useCallback()는 함수를 반환한다.

const useCallbackReturn = useCallback(() => {console.log(why)}, [ex]);  // useCallback()이 () => {console.log(why)} 라는 함수를 반환한다.
useCallbackReturn()  // useCallback이 담겨있는 함수를 실행한다. 즉, 새로운 함수를 만들어준것이다.

< 위의 useMemo()와 useCallback()의 더 자세한 설명 >
사이트 링크 참고: https://basemenks.tistory.com/238

-------------------

< 훅Hook의 useRef()와, callback ref 방법과 focus()와 ref에 대하여 >

사용법: const refContainer = useRef(초기값);

마치 전역변수와 c언어의 포인터처럼 값을 DOM요소에 접근하여 reference참조하여
렌더링될때마다 함수실행으로 원래의 초기값으로 다시 돌아가 초기화되어버리지않게 해준다.
즉, useRef() 사용한 변수의 current의 경우, 마운트될때 초기화된 상태에서 그대로 값을 유지하다가
값이 업데이트 되면서 렌더링되어 함수가 계속 재실행될때, 값의 초기상태 복귀없이 그대로 값을 변동하고 업데이트하여 갖고있는다.

참고로 const inputRef = useRef(null); 처럼 선언해주는데, 아마 inputRef는 자바스크립트객체일것이다. 뭐 의미는 변수처럼 봐도 아마 무방할듯하다.

더 자세한 설명은 사이트 링크 참고: https://itprogramming119.tistory.com/entry/React-useRef-%EC%82%AC%EC%9A%A9%EB%B2%95-%EB%B0%8F-%EC%98%88%EC%A0%9C
위의 사이트 코드중에서
focus()가 적힌 inputRef.current.focus();의 의미는, ref={inputRef}라고 적혀있는 태그 부분에 키보드 커서를 자동으로 이동시켜준다.
그러므로, 사이트가 첫 렌더링 되면 ref={inputRef}라고 적혀있는 input태그 글상자에 키보드 커서가 자동으로 타겟팅된다.
그리고 input ref의 ref의 의미는, html에서 id값을 지정하는것처럼 비슷하게 위치를 이름으로 지정해주는 것이다. 또한 내생각엔 아마 값도 전달해주는 역할도 하는것같다.
input ref에서 input함수로 만들어진 글상자에 값을 적어서 버튼을 클릭하면, 그 값을 가지고 loginAlert 함수가 실행된다.

useRef() 사용은, .current 프로퍼티값을 변경해도 리렌더링이 일어나지 않아 컴포넌트에서 인지를 하지못해서 변경되었는지 확인하기가 어렵다.
그럴때는 callback ref 방법을 사용하면 된다.
훅의 useCallback() 을 사용하여 함수를 반환하여 새로운 함수를 만들고, 그 새로운 함수를 특정html태그의 ref={}안에 넣어주면,
예시로 자식 컴포넌트가 바뀌었을때 알림을 받을 수 있다. 이를 통해 다른 정보들을 업데이트 할 수 있다.
참고할만한 사이트: https://leehwarang.github.io/2020/11/29/ref.html

-------------------

< 훅의 주의사항 >

훅은 무조건 최상위 레벨에서만 호출해야한다.
컴포넌트가 렌더링될 때마다 매번 같은 순서로 호출되어야하므로
즉, for반복문과 if문처럼 결과가 달라질수있는 조건에서 행하면 안되며,
중첩된 함수 컴포넌트 사이에서도 불가능하다.
이 조건은 Custom Hook에서도 동일하게 적용된다.

< Custom Hook >

커스텀 훅은
이름이 use로 시작하고
내부에서 다른 Hooks을 호출하는
하나의 자바스크립트 함수이다.

두 함수 컴포넌트의 중복된 로직 부분을(아마 훅도 포함?) 하나의 훅 함수 컴포넌트로 묶어준것이다.

커스텀 훅은 리액트 컴포넌트와는 달리 딱히 특별한 규칙이 없지만, 훅은 무조건 최상위 레벨에서만 호출해야한다는 주의사항은 지켜주어야한다.
커스텀 훅은 이름이 use로 시작하는 단순한 함수와도 같다고 봐도 된다.

참고로 예를들어 두 함수 컴포넌트의 중복부분을 커스텀 훅으로 생성하여 적용하였고 그 커스텀 훅 안에 state와 effect가 들어있다면,
그 각각의 함수 컴포넌트 1,2들은 같은 커스텀 훅을 호출하여 사용하긴했지만 각각 state와 effect는 분리되어 작동하고 적용된다.
뿐만아니라, 하나의 함수 컴포넌트에서 같은 커스텀 훅을 여러번 호출하여도, 커스텀 훅의 호출들도 모두 각각 완전히 독립적이다.

-------------------

< chapter_07 / Accommodate.jsx >
(Custom Hook 사용, useEffect() 종류별 호출 생명주기 순서와 그 이유 주석 설명 위주로 보면 됨.)

import React, { useState, useEffect } from "react";
import useCounter from "./useCounter";

const MAX_CAPACITY = 10;

function Accommodate(props) {
    const [isFull, setIsFull] = useState(false);
    const [count, increaseCount, decreaseCount] = useCounter(0);  // Custom Hook 호출함.

    useEffect(() => {  // 위에꺼 useEffect() 훅  // 의존성 배열이 없으므로, 함수 state인, isFull 값이 바뀔때와 count 값이 바뀔때 모두 실행됨.
        console.log("======================");
        console.log("useEffect() is called.");
        console.log(`isFull: ${isFull}`);
    });  // 의존성 배열이 없는 useEffect()  // 출생(mount)과, 함수 컴포넌트 렌더링시 인생(update)때 실행됨.
    // count값을 10까지 늘리고 나면, 위아래 useEffect() 훅을 전부 isFull=false값 기준으로 둘다 모두 출력후,
    // 밑에꺼 useEffect()의 setIsFull(count >= MAX_CAPACITY);로 인하여, isFull=false 에서 true로 바뀌었기에, 리렌더링의 조건중 하나인 '컴포넌트의 state가 변했을 때'를 만족하여
    // count=10값은 유지한채로 컴포넌트가 렌더링되고, 그렇기 때문에
    // count값은 변하지않아 밑에꺼 useEffect() 는 실행되지 않고, 이 useEffect() 훅만 한번더 isFull=true값 기준으로 실행된다.
    // count값을 10에서 9로 줄일때에도 마찬가지의 이유로, 위아래 useEffect() 훅을 전부 isFull=true값 기준으로 둘다 모두 출력후, 밑에꺼 useEffect() 말고 이 useEffect() 훅만 한번더 isFull=false값 기준으로 실행된다.

    useEffect(() => {  // 밑에꺼 useEffect() 훅  // 의존성 배열 [count]가 있으므로, count 값이 바뀔때만 실행됨.
        setIsFull(count >= MAX_CAPACITY);  // isFull = boolean(조건 count >= MAX_CAPACITY) 이라는 의미이다.
        console.log(`Current count value: ${count}`);
    }, [count]);  // 의존성 배열이 있는 useEffect()  // 출생(mount)과, 의존성 배열 업데이트인 인생(update)때 실행됨.
    // count값을 10까지 늘리고 나면, 위아래 useEffect() 훅을 전부 isFull=false값 기준으로 둘다 모두 출력후, 더이상 의존성 배열의 count값이 변화되지 않기에, 이 useEffect() 훅 말고, 저 위의 useEffect() 훅만 한번더 isFull=true값 기준으로 실행된다.
    // count값을 10에서 9로 줄일때에도 마찬가지의 이유로, 위아래 useEffect() 훅을 전부 isFull=true값 기준으로 둘다 모두 출력후, 이 useEffect() 말고, 저 위의 useEffect() 훅만 한번더 isFull=false값 기준으로 실행된다.

    return (
        <div style={{ padding: 16 }}>
            <p>{`총 ${count}명 수용했습니다.`}</p>

            <button onClick={increaseCount} disabled={isFull}>
                입장
            </button>
            <button onClick={decreaseCount}>퇴장</button>

            {isFull && <p style={{ color: "red" }}>정원이 가득찼습니다.</p>}
        </div>
    );
    // increaseCount와 decreaseCount는 아마 변수형 함수인것같다. 함수 실행.
}

export default Accommodate;

-------------------

< Event >

Dom의 Event의 예시는,
onclick="activate()"  // 소문자 c이며, 문자열 함수 전달

리액트의 Event의 예시는,
onClick={activate}  // 대문자 C이며, 함수 그대로 전달 => 대문자는 camelCase라고해서 카멜 표기법이라고 부른다.

Event Handler란,
어떤 사건이 발생하면, 사건을 처리하는 역할이다.
이는 Event Listener이라고도 부른다.

< 클래스 컴포넌트에서의 바인딩(bind) >

'자바스크립트에서의 바인딩(bind) & 리액트에서의 바인딩(bind)' & 바인딩 없이 화살표 함수 작성 방법으로 사용하는법  // 설명은 인터넷 사이트 링크 참고하기.
: https://jeong-pro.tistory.com/79

바인딩 없이 사용방법  // 설명은 인터넷 사이트 링크 참고하기.
: https://melthleeth.tistory.com/entry/React-Class-Method%EC%99%80-Arrow-Function
: https://dev.to/guin/learn-public-class-field-syntax-by-refactoring-a-react-component-njh

// 클래스 컴포넌트에서 이벤트 사용시, 바인딩 방법
// : 클래스 컴포넌트의 생성자 메소드인 constructor 메소드 안에서 바인딩(bind)해준다.
class App extends React.Component {
    constructor() {
        super();
        this.state = {
              hidden: false,
        };
        this.update = this.update.bind(this);  // 바인딩
    }
    update() {
        this.setState({
            hidden: true
        });
    }
 
    render() {
        return <div
            onClick={ this.update }
        />;
    }
}

// 클래스 컴포넌트에서 이벤트 사용시, 바인딩 직접 사용안하고 바인딩 시키는 방법
// : class field syntax 방법을 사용하여, 생성자 메소드인 constructor 메소드 안에
//    this.handleClick = this.handleClick.bind(this);같은 바인딩 함수 코드를 제외하고, super(props);와 this.state = {}; 같은 초기설정 코드만 적어준채로,
//    바로 핸들러메소드를 화살표 함수 작성 방법(arrow function)으로 만들어주면 된다.
class MyButton extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
              hidden: false,
        };
    }
    handleClick = () => {
        console.log('this is:', this);
        // this.setState(() => ({ hidden: true })); 참고로 이건 참고하라고 아무거나 추가로 적은 코드임.
    }
    render() {
        return (
            <button onClick={this.handleClick}>
                클릭
            </button>
        );
    }
}

< 함수 컴포넌트에서의 이벤트를 정의하는 방법 >

function Toggle(props) {
    const [isToggleOn, setIsToggleOn] = useState(true);

    // 방법 1. 함수 안에 함수로 정의
    function handleClick() {
        setIsToggleOn((isToggleOn) => !isToggleOn);
    }

    // 방법 2. arrow function을 사용하여 정의    
    const handleClick = () => {
        setIsToggleOn((isToggleOn) => !isToggleOn);
    }

    return (
        <button onClick={handleClick}>  // 함수 컴포넌트에서는 클래스 컴포넌트와는 다르게, 이벤트 함수 호출할때 this.를 사용하지 않는다.
            {isToggleOn ? "켜짐" : "꺼짐"}
        </button>
    );
}        

< 클래스 컴포넌트에서의 전달할 데이터를 매개변수(파라미터)로 이벤트 핸들러에 전달하는법 >

// 화살표 함수 방법
<button onClick={(event) => this.deleteItem(id, event)}>삭제하기</button>

// 일반 바인딩 방법
<button onClick={this.deleteItem.bind(this, id)}>삭제하기</button>

두 경우 모두 React 이벤트를 나타내는 event 인자가 ID 뒤에 두 번째 인자로 전달된다.
화살표 함수를 사용하는 방법이면, 명시적으로 직접 event 인자를 전달해야 하지만,
bind를 사용하는 방법이면, event를 인자로 따로 직접 적어줄필요없이 추가 인자가 자동으로 전달된다. 즉, 자동으로 {this.deleteItem.bind(this, id, event)} 이렇게 된다는 것이다.

단, 어차피 클래스 컴포넌트는 이제 잘 사용하지 않는 추세이니, 잘 알지 못해도 괜찮다고 한다.
함수 컴포넌트를 유심히 보자.

< 함수 컴포넌트에서의 전달할 데이터를 매개변수(파라미터)로 이벤트 핸들러에 전달하는법 >

function MyButton(props) {
    const handleDelete = (id, event) => {
        console.log(id, event.target);
    );

    return (
        <button onClick={(event) => handleDelete(1, event)}
            삭제하기
        </button>
    );
}

-------------------

< 헷갈릴수 있는것 >

함수 컴포넌트에서 사용:
useState 같은 훅
useEffect 같은 훅

클래스 컴포넌트에서 사용:
setState
componentDidUpdate 같은 생명주기 함수

-------------------

< 번외: prevState란? >

리액트에서는 prevState 라는 개념이 있다.
setState로 상태 값을 여러번 변경 하려고 할때마다 즉각적으로 state 에 변경된 상태값을 적용시키지 않는다.
리액트는 상태값이 변경 될 때 마다 렌더링을 시켜주는데, 매번 상태값을 즉각적으로 변경시킬때 마다 렌더링이 된다면 매우 비효율적이다.
따라서 setState으로 미리 변경된 상태값을 바로 땡겨와서 변경될 state에 적용시키는 방법이 있다.
PrevState 개념을 사용하면 편리하다.
참고로 setState는 클래스 컴포넌트의 것이고, 밑의 setCount는 함수 컴포넌트의 useState 훅 이긴 하지만, 예시로 든것이다.

const onClickCount = () => {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
  };
이렇게만 하면, 
위 코드에서 처럼 여러번 setCount(count+1)을 해주었을때 현재 count 는 정상적으로 증가를 하지 않는다.
setCount 가 여러번 실행되면서 카운트가 누적되는것 처럼 보이지만, 실질적으로는 setCount로 1증가 하고 다시 setCount로 1증가 이런식으로 흐름이 진행됨으로 실질적으로 count 에는 1만 증가되는 현상이 있다.
왜냐하면 함수가 렌더링 되기전에 여러번 실행해봤자 렌더링이 아직 안된 상태이므로, setCount는 한번만 적용되었기 때문이다.

const onClickCount = () => {
    // setState에서 상태값을 변경 시킬때 곧장 바로 변경될 수가 없음
    // state는 이전 상태값을 계속해서 가지고 있을 뿐 함수가 전부 실행되기 전까지는 렌더링을 하지 않음으로 카운트가 올라가지 않음
    // 따라서 콜백을 이용해서 이전 상태값을 가져와서 사용이 가능하다.
    setCount((count) => count + 1);
    setCount((count) => count + 1);
    setCount((count) => count + 1);
    setCount((count) => count + 1);
  };
(()=>S) 처럼 이전에 가지고 있는 상태 값을 가져다가 다음 상태 값으로 덮어 씌우기를 할 수 있다.
이러한 방법을 통해서 이전 상태값과 변경될 상태값을 가지고 state를 즉각적으로 변경 시킬수 있다.
마치 c언어에서 num = 1 만 반복 선언하다가, num = num + 1 로 바꿔 선언한 느낌이랄까?

결론적으로말하자면, setState 함수 사용 시 이전 state 값을 사용하고 싶으면 prevState를 이용하면 된다.
밑은 그의 예시이다.
    handleConfirm() {
        this.setState((prevState) => ({
            isConfirmed: !prevState.isConfirmed,
        }));
    }
이벤트 핸들러로 handleConfirm()가 실행되면, 이전의 state를 불러와 !로 반전시키고 그걸 state로 덮어씌우는것이다.

-------------------

< 밑의 이것들에 대한 예시로, 설명관련 사진자료 파일에 첨부해두었음. >

Conditional Rendering(컨디셔널 렌더링): 조건에 따른 렌더링 (조건부 렌더링)
=> 어떠한 조건(프로그래밍의 조건문처럼 True와 False로 나오는 결과)에 따라서 렌더링이 달라지는 것을 의미한다.

아마 컨디셔널 렌더링에는 '일반적인 if-else문 사용 방법'과, 'Inline If 방식으로 &&연산자 사용 방법'과, 'Inline If-Else 방식으로 ?삼항연산자 사용 방법'이 존재하는것같다.

Component 렌더링 막기: 만약 return된 값이 null일 경우, 해당 컴포넌트의 렌더링을 막고 결국 출력자체를 아예 배제시켜 못하게 할 수 있다.

Element Variables(엘리먼트 변수): 렌더링해야될 컴포넌트를 변수처럼 다루고 싶을때, 리액트의 엘리먼트를 변수처럼 다루는 방법이다.

Inline Conditions: 조건문을 분리해서 따로 작성하지않고 필요한 코드 안에 집어넣는 것.
이에는 'Inline If 방법'과 'Inline If-Else 방법'이 존재한다.

Inline If: If문의 경우 && 연산자를 사용한다. {condition && expression}인, {A && B}의 형태로써, 보통 A는 조건관련코드(condition)를 넣어주고 B는 출력하고싶은코드(expression)를 넣어준다.
만약 A && B 에서 조건A가 true이면, B를 반환하여 출력함.
만약 A && B 에서 조건A가 false이면, A만보고 B는 쳐다도안보게되어 B를 출력하지 않음. !!! 단, 주의해야할점은 이경우에 A의 반환값을 falsy 표현식으로 표현함. 만약 false가 0이면 falsy 표현식중 0을 출력하고, 만약 falsy 표현식 중에서 null, false, undefined 가 렌더링되는 경우라면 출력자체를하지않아 아무것도 나타내지 않는다. !!!

Inline If-Else: ?연산자인 삼항연산자를 사용한다. {condition ? true일때expression : false일때expression}의 형태이다.

null의 다른 예시로,
function Hello({ color, name, isSpecial }) {
  return (
    <div style={{ color }}>
      { isSpecial ? <b>Hello</b> : null }
      안녕하세요 {name}
    </div>
  );
}
// isSpecial 값이 true 라면 <b>Hello</b> 를, 그렇지 않다면 null 을 보여주도록 했다. 참고로 JSX 에서 null, false, undefined 를 렌더링하게 된다면 아무것도 나타나지 않게 된다.
// 다만, { isSpecial ? null : <b>Hello</b> } 이거는 어떻게될지 확인을 아직 해보지 못했다. 그리고 또한 이게 truthy 표현식과 falsy 표현식 모두 영향을 받을지에 관해서도 아직 확인해보지 못했다.

< truthy 표현식 >
true
{}  // empty object
[]  // empty array
42  // number, not zero
"0", "false"  // string, not empty

< falsy 표현식 >
false
0, -0  // zero, minus zero
0n  // BigInt zero
'', "", ``  // empty string
null
undefined
NaN  // not a number

< 가독성 좋게 범위를 설명 >

			    / 번외: Element Variables, Component 렌더링 막기
Conditional Rendering -- 일반적인 if-else문 사용 방법
			    \ Inline Conditions -- Inline If 방법: &&연산자 사용하고 condition이 false인경우 falsy 표현식 출력 주의하기
							\ Inline If-Else 방법: ?삼항연산자 사용

-------------------

< 리스트와 map 예시 >

const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);

ReactDOM.render(
  <ul>{number}</ul>,
  document.getElementById('root')
);

이러면 최종적으로 렌더링 되는 코드는

ReactDOM.render(
  <ul>
    <li>{1}</li>
    <li>{2}</li>
    <li>{3}</li>
    <li>{4}</li>
    <li>{5}</li>
  <ul>,
  document.getElementById('root')
);

이다.

< 내가 개인적으로 추천할 map 코드 방식 1 >

function NumberList(props) {
  const numbers = props.numbers;  // 또는 const { numbers } = props;

  const listItems = numbers.map((number) =>
    <li>{number}</li>
  );

  return (
    <ul>{listItems}</ul>
  );
}

const numberslliisstt = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList
    numbers={numberslliisstt}
    // key={numberslliisstt.toString()} 이것처럼 key값도 넣어줘야 warning이 안뜬다.
  />,
  document.getElementById('root')
);

< 내가 개인적으로 추천할 map 코드 방식 2 >

function NumberList(props) {
  const numbers = props.numbers;  // 또는 const { numbers } = props;

  return (
    <ul>
      {
        numbers.map( (number) =>
          {
            return (
              <li>{number}</li>
            );  // 이 return 세줄을 return <li>{number}</li>; 로도 사용이 가능하다.
          }
        )
      }
    </ul>
  );
}

const numberslliisstt = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList
    numbers={numberslliisstt}
    // key={numberslliisstt.toString()} 이것처럼 key값도 넣어줘야 warning이 안뜬다.
  />,
  document.getElementById('root')
);

< map 과 key값 >

key는 꼭 태그 안에 적어주어야한다.
const listItems = numbers.map((number) =>
  <li key={~~}>
    {number}
  </li>
);
이러한 식으로 추후에 map을 사용한 numbers로 키key값을 가져와 부여할때, 가능한 방식들로는

스트링으로 바꿔 부여하는걸 권장하여(필수는 아님)
<li key={number.toString()}>  // 근데 참고로 이건 number값이 전부 각기다른 고유의 값이란게 확신되어야만 쓸수있다.
  {number}
</li>

또는

만약 고유한 id값이 속성으로 첨부되어있다면
<li key={number.id}>
  {number}
</li>

또는

map을 사용할때 numbers.map((number, index) => ~~) 이런식으로 뒷부분에 index를 적어준다면
정안되면 이를 이용하여 최후의 수단으로 
<li key={index}>  // 이 index는 배열내에서 현재 아이템의 인덱스를 의미한다.
  {number}
</li>

이렇게 사용하면 된다.

-------------------

< Controlled Components >

Controlled Components: 제어 컴포넌트 이다. 사용자가 폼form 양식에 입력한 데이터값을 직접 제어할 수 있다.
즉, 값이 리액트의 통제를 받는 Input Form Element 인것이다.
이는 모든 데이터를 state로 관리할 수 있다.
클래스 컴포넌트에선 setState로, 함수 컴포넌트에선 useState 훅으로 말이다.

< 함수 컴포넌트에서의 'arrow function 방법으로 이벤트 정의함 + form과 Controlled Components 사용법' 예시 코드 >

function NameForm(props) {
  const [value, setValue] = useState('');

  const handleChange = (event) => {
    setValue(event.target.value);  // 만약 이를 응용하여 모든 입력값을 대문자로 변경하는 코드를 작성하고싶다면, setValue(event.target.value.toUpperCase()); 로 적어주면 된다.
  }

  const handleSubmit = (event) => {
    alert('입력 제출한 이름: ' + value);
    event.preventDefault();  // a 태그나 submit 태그는 누르게 되면 href를 통해 이동하거나 창이 새로고침하여 실행되는데, 이를 막아주는 역할의 메소드가 preventDefault이다.
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        이름:
        <input type="text" value={value} onChange={handleChange} />
      </label>
      <button type="submit">제출</button>
    </form>
  )
}

< 클래스 컴포넌트에서의 '생성자메소드로 직접 바인딩하는 방법 사용함 + 이벤트 사용법 + form과 Controlled Components 사용법' 예시 코드 >

class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('입력 제출한 이름: ' + this.state.value);
    event.preventDefault();  // a 태그나 submit 태그는 누르게 되면 href를 통해 이동하거나 창이 새로고침하여 실행되는데, 이를 막아주는 역할의 메소드가 preventDefault이다.
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          이름:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <button type="submit">제출</button>
      </form>
    );
  }
}

-------------------

< '일반적인 HTML 에서의 textarea 태그' vs '리액트 에서의 textarea 태그' >

일반적인 HTML 에서의 textarea 태그는
<textarea>가나다</textarea> 이렇게 사용하지만,

리액트 에서의 textarea 태그는 form과 Controlled Components 사용을 위하여
<input type="text" value={value} onChange={handleChange} />와 용도는 유사하되 input태그에서 type="text"를 제외하고
<textarea value={value} onChange={this.handleChange} /> 이렇게 사용한다.

< 일반적인 HTML 에서의 select 태그 vs 리액트 에서의 select 태그 >

참고로 일반적인 HTML에서 option selected value로 적어둔것이 초기값으로 미리 선택하여 보여줄 선택항목이다.

참고로 아마 리액트?에서 select 태그에 multiple 옵션을 허용한다면 value 어트리뷰트에 배열을 전달할 수 있다.
<select multiple={true} value={['B', 'C']}>
이런식으로 작성해주면 된다.

나머지 비교자료는 예시로, 설명관련 사진자료 파일에 첨부해두었음.

< '클래스 컴포넌트 vs 함수 컴포넌트' 에서의 form의 여러 state 데이터 관리 차이 >

클래스 컴포넌트에서는 setState 하나로 모든 state값들을 업데이트하였지만,
함수 컴포넌트에서는 각 useState로 만들어준 각각의 set함수 변수마다 state가 따로 존재하기때문에 각각의 set함수로 분리되어 여러 state 데이터를 따로따로 관리가 가능하다.
이 예시중 함수 컴포넌트의 예시는 설명관련 사진자료 파일에 첨부해두었음.

-------------------

< chapter_11 / SignUp.jsx >
(함수 컴포넌트에서의 'arrow function 방법으로 이벤트 정의함 + form과 Controlled Components 사용법 + 리액트에서의 select 태그 + form의 여러 state 데이터 관리' 예시 코드임.)
(참고로 label 태그에 대한 설명은 MD_html_css_js_study 파일에서 찾아볼것.)

import React, { useState } from "react";

function SignUp(props) {
    const [name, setName] = useState("");
    const [gender, setGender] = useState("남자");

    const handleChangeName = (event) => {
        setName(event.target.value);
    };

    const handleChangeGender = (event) => {
        setGender(event.target.value);
    };

    const handleSubmit = (event) => {
        alert(`이름: ${name}, 성별: ${gender}`);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <label>
                이름:
                <input type="text" value={name} onChange={handleChangeName} />
            </label>
            <br />
            <label>
                성별:
                <select value={gender} onChange={handleChangeGender}>
                    <option value="남자">남자</option>
                    <option value="여자">여자</option>
                </select>
            </label>
            <button type="submit">제출</button>
        </form>
    );
}

export default SignUp;

-------------------

React에서 state를 공유하는 일은 그 값을 필요로 하는 컴포넌트 간의 가장 가까운 공통 조상(상위 컴포넌트)으로 state를 끌어올림으로써 이뤄낼 수 있는데, 이는 props 등등을 활용하여 값을 전달하고 동기화시킬 수 있다.

위 설명의 예시로
두 TemperatureInput라는 컴포넌트가 각각의 다른 입력값을 각자의 state에 독립적으로 저장하고 있는데,
이를 따로 저장하기보다 서로 동기화시켜 섭씨온도 입력값을 변경할 경우 화씨온도 입력값 역시 변환된 온도를 반영할 수 있어야 하며, 그 반대의 경우에도 마찬가지여야 하는 코드를 짜야하는경우가 있다고 하자.
이 예시 코드는 코드들중에서 chapter_12 파트 부분을 보면 된다.

-------------------

컴포넌트 합성(Composition)의 예시 코드로 두가지 컴포넌트의 특정 부분을 가져와보았다.

< 예시코드 >
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {props.title}
      </h1>
      <p className="Dialog-message">
        {props.message}
      </p>
      {props.children}
    </FancyBorder>
  );
}

function SignUpDialog(props) {
  // useState훅이랑 이벤트 메소드들 정의 등등 생략
  return (
      <Dialog title="화성 탐사 프로그램"
              message="닉네임을 입력해주세요.">
        <input value={nickname}
               onChange={handleChange} />
        <button onClick={handleSignUp}>
          가입하기
        </button>
      </Dialog>
    );
}

props.children 은 원래 리액트에 내장되어있어 사용이 가능하며, 이는 해당 컴포넌트의 하위 컴포넌트의 태그 부분들을 가져온다.
이는 컴포넌트 합성(Composition) 방법들 중에서 Containment 방법에 속한다.
Dialog 컴포넌트의 {props.children} 부분이며,
SignUpDialog 컴포넌트의 input태그, button태그 부분을 가져온다.

또다른 컴포넌트 합성(Composition) 방법으로는 Specialization 방법도 있다.
Dialog 컴포넌트의 {props.title}와 {props.message} 부분이며,
SignUpDialog 컴포넌트의 <Dialog name="~~" message="~~"> 부분의 값을 가져온다.

또다른 예시 코드는 코드들중에서 chapter_13 파트 부분을 보면 된다.

결론: 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 만들고, 만든 컴포넌트들을 조합해서 새로운 컴포넌트를 만들자!

-------------------

< context 란? >
일반적인 React 애플리케이션에서 데이터는 위에서 아래로 (즉, 부모로부터 자식에게) props를 통해 전달되지만,
props를 통해 전달 전달 전달 이렇게 연속적으로 쭉 내려가며 데이터를 전달하는 등의
애플리케이션 안의 여러 컴포넌트들에 전해줘야 하는 props의 경우 (예를 들면 선호 로케일, UI 테마) 이 과정이 번거로울 수 있다.
이는 context를 이용하면, 트리 단계마다 명시적으로 props를 넘겨주지 않아도 많은 컴포넌트가 이러한 값을 공유하도록 할 수 있다.
context는 React 컴포넌트 트리 안에서 전역적(global)이라고 볼 수 있는 데이터를 공유할 수 있도록 고안된 방법이다.

Context에 저장된 데이터를 사용하기 위해서는
Context 변수를 만들어주고 거기에 내장된 메소드를 사용하여
공통 부모 컴포넌트에 Context의 Provider 메소드를 사용하여 데이터를 제공해야 하며
데이터를 사용하려는 컴포넌트에서 Context의 Consumer 메소드를 사용하여 실제로 데이터를 사용한다.

< context 내장 메소드를 import하여 사용하는 방법 1 >
import React, { createContext } from 'react';
const MyContext = createContext();
< context 내장 메소드를 import하여 사용하는 방법 2 >
import React from 'react';
const MyContext = React.createContext();  // const MyContext = React.createContext('초기값');

< context 를 사용하지않아 비효율적인 연속적인 props 데이터 전달 예시 코드 >

function App(props) {
  return <Toolbar theme="dark" />;
  // Toolbar컴포넌트에 theme데이터값 전달함
  // 즉, 이는 굳이 나타내자면, theme="dark"
}

function Toolbar(props) {  // 여기서 props는 App컴포넌트의 theme="dark"
  // 이 Toolbar 컴포넌트는 ThemeButton에 theme를 넘겨주기 위해서 'theme' prop을 가져야만 한다.
  // 현재 테마를 알아야 하는 모든 버튼에 대해서 props로 전달하는 것은 굉장히 비효율적이다.
  return (
    <div>
      <ThemedButton theme={props.theme} />
    </div>
  );
  // {App컴포넌트.theme}
  // 즉, 이는 굳이 나타내자면, theme={App컴포넌트props.theme}
}

function ThemedButton(props) {  // 여기서 props는 Toolbar컴포넌트의 theme={props.theme}
  return <Button theme={props.theme} />;
  // {Toolbar컴포넌트.theme}
  // 즉, 이는 굳이 나타내자면, theme={App컴포넌트props.theme.theme}
}

// 최상위 컴포넌트: App, 중간 컴포넌트: Toolbar, 최하위 컴포넌트: ThemedButton
// 코드 목적: 최상위 컴포넌트에서 데이터를 최하위 컴포넌트로 전달하고 싶음.
// context 사용하지않아 비효율적인 데이터 전달 과정: 최상위App -> 중간Toolbar -> 최하위ThemedButton  // 바로 전달 불가능

< context 를 사용하여 효율적인 데이터 전달 예시 코드 >

import React from 'react';
const ThemeContext = React.createContext('light');  // context 변수 생성

function App(props) {
  // context 변수에 Provider 메소드를 사용하여 하위 컴포넌트들에게 테마 데이터값을 전달한다.
  // 아무리 깊숙히 있어도, 모든 컴포넌트가 이 값을 읽을 수 있다.
  // 아래 예시에서는 dark를 현재 선택된 테마 값으로 보내고 있다.
  // 참고로 value="dark" 로 주었기때문에 나중에 Consumer메소드로 사용할때도 {value}이다.
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

// 이젠 중간에 있는 컴포넌트가 중간매개체 역할로 일일이 테마를 넘겨줄 필요가 없기에 그저 선언만 해주면된다.
function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton(props) {
  // Provider 메소드로 전달되었던 데이터를 직접 Consumer 메소드를 사용하여 데이터값을 사용한다.
  // 만약 해당되는 Provider가 없을 경우 기본값(여기에서는 'light')을 사용하지만,
  // 여기에서는 상위 Provider가 존재하기때문에 현재 테마의 값은 'dark'가 된다.
  return (
    <ThemeContext.Consumer>
      {value => <Button theme={value} />}
    </ThemeContext.Consumer>
  );
}

// 최상위 컴포넌트: App, 중간 컴포넌트: Toolbar, 최하위 컴포넌트: ThemedButton
// 코드 목적: 최상위 컴포넌트에서 데이터를 최하위 컴포넌트로 전달하고 싶음.
// context 사용하여 효율적인 데이터 전달 과정: 최상위App -> 최하위ThemedButton  // 바로 전달 가능

< context 사용시 고려해야할점 >
context의 주된 용도는 다양한 레벨에 많은 컴포넌트에게 데이터를 전달하는 것이다. context를 사용하면 컴포넌트의 재사용성이 떨어지므로 꼭 필요할 때만 쓰는것이 좋다.
그렇기에 위의 경우가 아니라면, 여러 레벨에 걸쳐 props 넘기는 걸 대체하는 데에 'context' 방법보다 '컴포넌트 합성(Composition)' 방법이 더 좋을것이다.
또는 렌더링해야될 컴포넌트를 변수처럼 다루고 싶을때 리액트의 엘리먼트를 변수처럼 다루는 방법인 'Element Variables(엘리먼트 변수)'도 활용해보면 좋다.

-------------------

```
