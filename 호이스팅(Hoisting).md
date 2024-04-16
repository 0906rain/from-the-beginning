#### 호이스팅(Hoisting)란?
##### 함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효 범위의 최상단에 선언하는 것을 말한다.
- 자바스크립트는 구문분석(Parser)을 함수 실행 전 해당 함수를 한 번 흝는다.
- 함수 안에 존재하는 변수/함수선언에 대한 정보를 기억하고 있다가 실행한다.
- 범위는 함수 블록{}안에서 유효하다.

##### 함수 내에서 아래쪽에 존재하는 내용 중 필요한 값들을 끌어올리는 것이다.
- 실제로 코드가 끌어올려지는 건 아니며, 자바스크립트 구문분석(Parser) 내부적으로 끌어올려서 처리하는 것이다.
- 실제 메모리에서는 변화가 없다.

##### 호이스팅의 대상
1. Var 변수 선언
- Var 변수 선언만 끌어 올려지며, 할당은 끌어 올려지지 않는다.
``` javascript
ex)
console.log("Test");
var x = 1; // 변수 var
let y = 2; // 변수 let
const z = 3; // 변수 const

// JS에서 구문분석(Parser) 내부의 호이스팅(Hoisting)의 결과 - 결과는 같음

var x; // 호이스팅(Hoisting) 선언
console.log("Test");
x = 1; // x에 1 할당
let y = 2; // 호이스팅(Hoisting) 발생x
const z = 3; // 호이스팅(Hoisting) 발생x
```

2. 함수선언문
- 함수선언문은 코드를 구현한 위치와 관계없이 자바스크립트의 특징인 호이스팅에 따라 브라우저가 자바스크립트를 해석할 때 맨 위로 끌어 올려진다.
- 함수표현식은 함수선언문과 달리 선언과 호출 순서에 따라서 정상적으로 함수가 실행되지 않을 수 있다.
``` javascript
ex)
Fun();
Fun2();

function Fun() { // 함수선언문
  console.log("Fun");
}

var Fun2 = function() { // 함수표현식
  console.log("Fun2");
}

// JS에서 구문분석(Parser) 내부의 호이스팅(Hoisting)의 결과 - 결과는 같음

var Fun2; // 호이스팅(Hoisting) 함수표현식의 변수 선언

function Fun() { // 호이스팅(Hoisting) 함수선언문
  console.log("Fun");
}
Fun();
Fun2(); //ERROR

var Fun2 = function() {
  console.log("Fun2");
}
// 호이스팅(Hoisting)은 함수선언문과 표현식에서 서로 다르게 동작하기 때문에 주의해야한다.
// 변수에 할당된 함수표현식은 끌어 올려지지 않기 때문에 이때 변수의 스코프 규칙을 그대로 따른다. 
```

