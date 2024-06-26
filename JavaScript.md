## JavaScript란 ?
- HTML과 CSS로 구성된 웹 페이지를 동적으로 만들어주는 언어

### 기본 문법

#### 1.변수
변수 선언 방법 3가지

#### var의 특징
- var의 Scope(범위)는 전역 혹은 함수 범위로 지정된다. 즉 함수 외부에서 var 선언하면 전역변수로 사용이 되고, 함수 내에서 선언하면 그 함수의 지역변수로 사용된다.
``` javascript
ex)
var x = 1; // x는 전역변수로 값은 1이다.

function F() {
  var y = 2; // y는 지역변수로 값은 2이다.
}
console.log(x); // x의 값인 1 출력
console.log(y); // y를 찾을 수 없다고 에러가 발생한다. y is not defined
```
- 변수가 재선언과 업데이트가 가능
``` javascript
ex)
var x = 1; // x는 1로 선언
var x = 2; // x는 2로 재선언
x = 3; // x는 3으로 업데이트
```
- 변수의 재선언과 업데이트가 가능하여 의도치 않게 재선언 혹은 업데이트가 된다.
``` javascript
ex)
var name = "Lee"; // name을 Lee로 선언
var x = 1; // x를 1로 선언
if(x == 1) { // if문 x의 값이 1이랑 같을 때 
  var name = "Kim"; // name을 Kim로 선언
  console.log(name); // name이 Kim 출력
};
```
예시와 같이 할 경우 name 변수에 할당된 값이 원래 Lee 였으나 if문에 들어가서 name이 재선언 되어 기존에 변수 name이 정의되어 있다는 것을 인식이 안된다.
만약 의도적으로 재선언은 괜찮지만 의도적으로 한 게 아니라면 원치 않은 결과 값이 나올 수 있어서 문제가 된다.

- var의 호이스팅은 var변수가 범위 내에서 맨 위로 올려지고 값은 undefined(정의되지 않음)으로 초기화된다.
``` javascript
ex.1)
console.log (name); // 로그에 name 변수 출력
var name = "Lee"; // name을 Lee로 선언
ex.2)
var name;
console.log(name); // name 변수 값 undefined
name = "Lee"; // name 변수 값 Lee로 업데이트
위 1번 예시를 자바스크립트는 2번 예시로 해석하게된다.  
```
#### let의 특징
- 변수가 업데이트는 가능, 재선언은 불가능
``` javascript
ex)
let x = 1; // x는 1로 선언
let x = 2; // 코드 에러가 뜬다. Reference Error(참조 오류)
x = 2; // x는 2로 업데이트는 에러가 없다.
```
- var와 다르게 let은 범위 내에서 재선언이 안된다. 단 동일한 변수가 다른 범위내에서 정의된다면, 에러는 발생하지 않는다.
``` javascript
ex) 
let name = "Lee"; // name에 Lee로 선언
let name = "Kim"; // Identifier 'name' has already been declared. 이미 선언되어 있다고 에러가 발생
if ( x == 2){
  let name = "Kim"; // name을 kim으로 선언
};
```
예시와 같이 할 경우 name 변수가 선언되고 같은 범위에 다시 재선언 하였을 때 이미 선언되어 있다고 에러가 떳지만 다른 블럭 범위(if문)안에 선언한 경우 에러 없이 실행이 된다.  // 블럭이란 {}로 바인딩된 코드 청크이다. 하나의 블록은 중괄호 속에서 존재하고 중괄호 안에 있는 것은 모두 블록 범위이다.

- let의 호이스팅은 var와 마찬가지로 let 선언은 맨 위로 올려지고 undefined로 초기화되는 var와 다르게 let은 초기화되지 않습니다. 선언 이전에 let 변수를 사용하려고 한다면 Referene Error(참조 오류)가 발생한다.

#### const의 특징
- 변수가 업데이트, 재선언 불가능 일정한 상수 값을 유지 // 상수란 수식에서 변하지 않는 값을 뜻한다.
``` javascript
ex)
const x = 1; // x는 1로 선언
const x = 2; // 코드 에러가 뜬다. Identifier 'x' has already been declared 식별자가 이미 선언되어있다고 에러가 발생한다.
x = 2; // 코드 에러가 뜬다. Assignment to constant variable.  상수의 변수에 할당되었다고 에러가 발생한다.
```
- const선언도 let선언처럼 선언된 블록 범위 내에서만 접근이 가능하다.

- 다른 변수와 다르게 다소 특이한 점이 있는데 const개체는 업데이트는 할 수 없지만, 개체의 요소나 속성은 업데이트가 가능하다 단 예시와 같이 선언한 경우. // 속성이란 객체, 요소, 또는 파일의 성질이다. 속성은 또한 이들의 인스턴스(instance)에 주어진 특정 값을 지정하거나 나타내는 데에도 쓰인다.
  const가 변수 자체를 불변으로 만드는 것이 아니라 변수가 참조하는 값의 변경을 막는 것이기 때문이다. 배열이나 객체는 참조 타입이고, const로 선언된 변수가 참조하는 메모리 공간 자체는 변경되지 않는다. 따라서 변수가 참조하는 배열이나 객체의 요소나 속성은 여전히 변경 가능하다.
``` javascript
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
```
- const의 호이스팅은 let과 마찬가지로 const 선언도 맨 위로 올려지고, 초기화되지 않습니다.

3개의 변수 선언법의 총정리
1. var 선언은 전역 범위 또는 함수 범위이며, let과 const는 블록 범위이다.
2. var 변수는 범위 내에서 업데이트 및 재선언이 가능하며 let 변수는 업데이트만 가능하고, 재선언 불가능하다. const 변수는 업데이트와 재선언 둘 다 불가능하다. 단 업데이트는 예외가 있다.
3. 3가지 선언 방법 모두 최상위로 호이스팅 되지만, var 변수만 undefined(정의되지 않음)으로 초기화 되고 let 변수와 const 변수는 초기화되지 않는다.
4. var 변수와 let 변수는 초기화하지 않은 상태에서 선언할 수 있지만, const는 선언 중에 초기화해야한다.

#### 2.타입(자료형)

#### 1) 기본 자료형 3가지

#### 문자열(Strint)
- 문자의 집합으로 인용부호를 사용o, 숫자도 인용부호를 사용하면 문자열로 취급 // 인용부호란 "",''따옴표를 뜻함
``` javascript
ex)
let str1 = "Lee"; // str1의 자료형은 String 데이터값은 Lee
let srt2 = 'Kim'; // str2의 자료형은 String 데이터값은 Kim
let str3 = "Park'; // 에러가 발생한다. 이때 인용부호를 큰따옴표는 큰따옴표끼리, 작은따옴표는 작은따옴표끼리 해줘야한다.
```

#### 숫자(Number)
- 숫자는 인용부호를 사용x,  Javascript에서는 정수와 실수를 통합해서 사용함. 단 다른 언어들은 정수형, 실수형으로 분리될 수 있음.
``` javascript
ex)
let x = 1; // x의 자료형은 Number 데이터값은 1
let y = 3.141592; // y의 자료형은 Number 데이터값은 3.141592  Javascript에서는 정수와 실수를 통합해서 사용함
let z = -10; // z의 자료형은 Number 데이터값은 -10
```

#### 불리언(Boolean)
- 함과 거짓 두가지만 있는 타입, 인용부호 사용x
``` javascript
ex)
let T = true; // T의 자료형은 Boolean 데이터값은 true(참)
let F = false; // F의 자료형은 Boolean 데이터값은 false(거짓)
```

#### 2)복합 자료형 3가지

#### 배열(Array)
- 여러 값을 하나의 단일 참조로 저장하는 구조를 가진 타입
``` javascript
ex)
let arr1 = [1, 2, 3]; // arr1의 자료형은 Array 데이터값은[1, 2, 3]
console.log(arr1); // arr1의 배열 [1, 2, 3]이 출력
console.log(arr1[0]); // arr1의 배열 1번째의 1을 출력, 원하는 배열의 위치의 인덱스값을 입력 단 첫번째가 0부터 시작함

let arr2 = ["Lee", "Kim", " Park"]; // arr2의 자료형은 Array 데이터값은 ["Lee", "Kim", " Park"], 문자열도 배열에 사용 가능
console.log(arr2); // arr2의 배열 ["Lee", "Kim", " Park"]이 출력
console.log(arr2[1]); // arr2의 배열 2번째의 "Kim"을 출력

let arr3 = [1, "Lee", 2, true]; // arr3의 자료형은 Array 데이터값은 [1, "Lee", 2], 숫자나 문자열 혹은 불리언 혼합 사용가능
console.log(arr3); // arr3의 배열 [1, "Lee", 2, true]이 출력
console.log(arr3[3]); // arr3의 배열 4번째의 true을 출력
```

#### 객체(Object)
- 여러 속성을 하나의 변수에 저장할 수 있도록 해주는 데이터 타입으로 Key / Value Pair를 저장할 수 있는 구조이다.
``` javascript
ex)
var user = {
  name: "Lee", // name은 key, Lee는 value
  age : 25  // age은 key, 25는 value
};
```

#### 함수(Funtion)
- 다른 복합 자료형처럼 속성 및 method를 가질 수 있기에 일급(first-class)객체이며 인자를 가질 수 있는 코드 블록이다.
``` javascript
ex)
function add(x, y) { // 함수 선언식
  var z = x + y; // x의 값과, y의 값을 받아 변수 z에 저장한다.
  return z; // 변수 z의 값을 리턴한다.
}

const add = function(x, y) { // 함수 표현식
  var z = x + y; // x의 값과, y의 값을 받아 변수 z에 저장한다.
  return z; // 변수 z의 값을 리턴한다. 리턴을 안 할 경우도 있다. 단 리턴을 안 할 경우 혹은 리턴값을 지정해주지 않으면 undedfined가 반환된다.
};
// 함수 선언식과 함수 표현식의 차이점은 JavaScript는 Script를 실행하기 전, 준비 단계에서 전역에 선언된 함수 선언문을 찾고 해당 함수를 생성한다. 즉 선언식은 Script 실행하기 전에 해방 함수를 생성하고 표현식은 실행하고 흐름이 함수에 도달했을 때 함수를 생성한다.
```
