#### 스코프(Scope)란?
- 변수또는 함수의 식별자가 사용되는 유효범위이다.

```javascript
let name = "Lee";

function Hello () {
  let H = 'Hello!"
  console.log(H + name);
}
console.log(H);

// JS 코드 결과
Hello! Lee
참조오류(ReferenceError) // H 변수를 찾지 못한다.
```

####스코프의 규칙
1. 내부에서 정의된 변수는 외부 스코프에서 접근이 불가능
2. 외부에서 정의된 변수는 내부 스코프에 접근 가능
3. 지역 스코프가 전역 스코프보다 더 높은 우선순위를 가진다.
