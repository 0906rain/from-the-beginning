## JavaScript란 ?
- HTML과 CSS로 구성된 웹 페이지를 동적으로 만들어주는 언어

기본 문법

변수
변수 선언 방법 3가지

var의 특징
- var의 Scope(범위)는 전역 혹은 함수 범위로 지정된다. 즉 함수 외부에서 var 선언하면 전역변수로 사용이 되고, 함수 내에서 선언하면 그 함수의 지역변수로 사용된다.
ex)
var x = 1; // x는 전역변수로 값은 1이다.

function F() {
  var y = 2; // y는 지역변수로 값은 2이다.
}
console.log(x); // x의 값인 1 출력
console.log(y); // y를 찾을 수 없다고 에러가 발생한다. y is not defined

- 변수가 재선언과 업데이트가 가능
ex)
var x = 1; // x는 1로 선언
var x = 2; // x는 2로 재선언
x = 3; // x는 3으로 업데이트

- 변수의 재선언과 업데이트가 가능하여 의도치 않게 재선언 혹은 업데이트가 된다.
ex)
var name = "Lee"; // name을 Lee로 선언
var x = 1; // x를 1로 선언
if(x == 1) { // if문 x의 값이 1이랑 같을 때 
  var name = "Kim"; // name을 Kim로 선언
  console.log(name); // name이 Kim 출력
};
예시와 같이 할 경우 name 변수에 할당된 값이 원래 Lee 였으나 if문에 들어가서 name이 재선언 되어 기존에 변수 name이 정의되어 있다는 것을 인식이 안된다.
만약 의도적으로 재선언은 괜찮지만 의도적으로 한게 아니라면 원치 않은 결과 값이 나올수있어서 문제가 된다.

- var의 호이스팅은 var변수가 범위 내에서 맨 위로 올려지고 값은 undefined(정의되지 않음)으로 초기화된다. // 여기서 호이스팅이란? - 변수와 함수 선언이 맨 위로 이동되는 자바스크립트 매커니즘이다.
ex.1)
console.log (name); // 로그에 name 변수 출력
var name = "Lee"; // name을 Lee로 선언
ex.2)
var name;
console.log(name); // name 변수 값 undefined
name = "Lee"; // name 변수 값 Lee로 업데이트
위 1번 예시를 자바스크립트는 2번 예시로 해석하게된다.  

let의 특징
- 변수가 업데이트는 가능, 재선언은 불가능
ex)
let x = 1; // x는 1로 선언
let x = 2; // 코드 에러가 뜬다. Reference Error(참조 오류)
x = 2; // x는 2로 업데이트는 에러가 없다.

- var와 다르게 let은 범위 내에서 재선언이 안된다. 단 동일한 변수가 다른 범위내에서 정의된다면, 에러는 발생하지 않는다.
ex) 
let name = "Lee"; // name에 Lee로 선언
let name = "Kim"; // Identifier 'name' has already been declared. 이미 선언되어 있다고 에러가 발생
if ( x == 2){
  let name = "Kim"; // name을 kim으로 선언
};
예시와 같이 할 경우 name 변수가 선언되고 같은 범위에 다시 재선언 하였을 때 이미 선언되어 있다고 에러가 떳지만 다른 블럭 범위(if문)안에 선언한 경우 에러 없이 실행이 된다.  // 블럭이란 {}로 바인딩된 코드 청크이다. 하나의 블록은 중괄호 속에서 존재하고 중괄호 안에 있는 것은 모두 블록 범위이다.

- let의 호이스팅은 var와 마찬가지로 let 선언은 맨 위로 올려지고 undefined로 초기화되는 var와 다르게 let은 초기화되지 않습니다. 선언 이전에 let 변수를 사용하려고 한다면 Referene Error(참조 오류)가 발생한다.

const의 특징
- 변수가 업데이트, 재선언 불가능 일정한 상수 값을 유지 // 상수란 수식에서 변하지 않는 값을 뜻한다.
ex)
const x = 1; // x는 1로 선언
const x = 2; // 코드 에러가 뜬다. Identifier 'x' has already been declared 식별자가 이미 선언되어있다고 에러가 발생한다.
x = 2; // 코드 에러가 뜬다. Assignment to constant variable.  상수의 변수에 할당되었다고 에러가 발생한다.

- const선언도 let선언처럼 선언된 블록 범위 내에서만 접근이 가능하다.

- 다른 변수와 다르게 다소 특이한 점이 있는데 const개체는 업데이트는 할 수 없지만, 개체의 요소나 속성은 업데이트가 가능하다 단 예시와 같이 선언한 경우. // 속성이란 객체, 요소, 또는 파일의 성질이다. 속성은 또한 이들의 인스턴스(instance)에 주어진 특정 값을 지정하거나 나타내는 데에도 쓰인다.
  const가 변수 자체를 불변으로 만드는 것이 아니라 변수가 참조하는 값의 변경을 막는 것이기 때문이다. 배열이나 객체는 참조 타입이고, const로 선언된 변수가 참조하는 메모리 공간 자체는 변경되지 않는다. 따라서 변수가 참조하는 배열이나 객체의 요소나 속성은 여전히 변경 가능하다.
ex)
const get = {
    name : "Lee", // get.name Lee 선언
    x : 1 // get.x 1 선언
};
console.log(get.name); // get.name값인 Lee 출력
console.log(get.x); // get.x값인 1 출력

get.x=2; // 속성값은 변경이 가능하므로 get.x는 2로 업데이트
console.log(get.x); // get.x값이 업데이트된 2로 출력

get = {
  name2 : "Kim";
  y : 2
}; 코드 에러가 뜬다. Assignment to constant variable.  상수의 변수에 할당되었다고 에러가 발생한다.

const arr = [1, 2];
arr.push(3);
console.log(arr); // [1, 2, 3]로 배열 출력

const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
arr1 = arr2; // 코드 에러가 뜬다. Assignment to constant variable.  상수의 변수에 할당되었다고 에러가 발생한다.

- const의 호이스팅은 let과 마찬가지로 const 선언도 맨 위로 올려지고, 초기화되지 않습니다.

3개의 변수 선언법의 총정리
1. var 선언은 전역 범위 또는 함수 범위이며, let과 const는 블록 범위이다.
2. var 변수는 범위 내에서 업데이트 및 재선언이 가능하며 let 변수는 업데이트만 가능하고, 재선언 불가능하다. const 변수는 업데이트와 재선언 둘 다 불가능하다. 단 업데이트는 예외가 있다.
3. 3가지 선언 방법 모두 최상위로 호이스팅 되지만, var 변수만 undefined(정의되지 않음)으로 초기화 되고 let 변수와 const 변수는 초기화되지 않는다.
4. var 변수와 let 변수는 초기화하지 않은 상태에서 선언할 수 있지만, const는 선언 중에 초기화해야한다.





