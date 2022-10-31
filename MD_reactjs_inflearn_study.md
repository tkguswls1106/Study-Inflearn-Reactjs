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

// arrow function expression을 사용
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

-------------------

백틱 `: https://developerjm.tistory.com/25
사용법은 영문으로 ₩키를 누르면 된다.

-------------------

```
