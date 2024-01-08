# 15장. let, const 키워드와 블록 레벨 스코프

## 15.1 var 키워드로 선언한 변수의 문제점

### 15.1.1 변수 중복 선언 허용

var 키워드로 선언한 변수는 중복 선언이 가능하다.  
만약 동일한 이름의 변수가 이미 선언되어 있는 것을 모르고 변수를 중복 선언하면서 값까지 할당했다면, 의도치 않게 먼저 선언한 변수 값이 변경되는 부작용이 발생한다.

### 15.1.2 함수 레벨 스코프

var 키워드로 선언한 변수는 오로지 함수의 코드 블록만을 지역 스코프로 인정한다.  
따라서 함수 외부에서 var 키워드로 선언한 변수는 코드 블록 내에서 선언해도 모두 전역 변수가 된다.

### 15.1.3 변수 호이스팅

```javascript
// 이 시점에 변수 호이스팅에 의해 이미 foo 변수가 선언되었다. (1. 선언 단계)
// 변수 foo는 undefined로 초기화된다. (2. 초기화 단계)
console.log(foo); // undefined

// 변수에 값을 할당 (3. 할당 단계)
foo = 123;

console.log(foo); // 123

// 변수 선언은 런타임 이전에 자바스크립트 엔진에 의해 암묵적으로 실행된다.
var foo;
```

변수 선언문 이전에 변수를 참조하는 것은 변수 호이스팅에 의해 에러가 발생하진 않지만,  
프로그램의 흐름상 맞지 않을뿐더러 가독성을 저하시키고 오류를 발생시킬 여지를 남긴다.

---

## 15.2 let 키워드

let 과 const 키워드는 ES6에서 var 키워드의 단점을 보완하기 위해 도입됐다.

### 15.2.1 변수 중복 선언 금지

let 키워드로 이름이 같은 변수를 중복 선언하면 문법 에러가 발생한다.

### 15.2.2 블록 레벨 스코프

let 키워드로 선언한 변수는 모든 코드 블록을 지역 스코프로 인정하는 블록 레벨 스코프다.

```javascript
let foo = 1; // 전역변수

{
  let foo = 2; // 지역변수
  let bar = 3; // 지역변수
}

console.log(foo); // 1
console.log(bar); // ReferenceError: bar is not defined
```

### 15.2.3 변수 호이스팅

let 키워드로 선언한 변수를 변수 선언문 이전에 참조하면 참조 에러가 발생한다. 때문에 변수 호이스팅이 발생하지 않는 것처럼 보인다.

**let 키워드로 선언한 변수는 "선언 단계"와 초기화 단계"가 분리되어 진행** 되기 때문에 나타나는 현상이다.  
즉, 런타임 이전에 자바스크립트 엔진에 의해 선언 단계가 먼저 실행되지만 초기화 단계는 변수 선언문에 도달했을 때 실행된다.  
스코프의 시작 지점부터 초기화 단계 시작 지점(변수 선언문)까지 변수를 참조할 수 없다. 이 구간을 일시적 사각지대TDZ, Temporal Dead Zone이라 한다.

```javascript
// 런타임 이전에 선언 단계가 실행된다. 아직 변수가 초기화되지 않았다.
// 초기화 이전의 일시적 사각지대에서는 변수를 참조할 수 없다.
console.log(foo); // ReferenceError: foo is not defined

let foo; // 변수 선언문에서 초기화 단계 진행
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계 진행
console.log(foo); // 1
```

ES6에서 도입된 let, const, class를 사용한 선언문은 호이스팅이 발생하지 않는 것처럼 동작하지만 let, const 를 포함한 모든 선언을 호이스팅한다.

### 15.2.4 전역 객체와 let

var 키워드로 선언한 전역 변수와 전역 함수, 그리고 선언하지 않은 변수에 값을 할당한 암묵적 전역은 전역객체 window의 프로퍼티가 된다. 전역 객체의 프로퍼티를 참조할 때 window를 생략 가능하다.

```javascript
// 브라우저 환경에서 실행해야 한다.

// 전역 변수
var x = 1;
// 암묵적 전역
y = 2;
// 전역 함수
function foo() {}

// var 키워드로 선언한 전역 변수는 전역 객체 window의 프로퍼티다.
console.log(window.x); // 1
console.log(x); // 1

console.log(window.y); // 2
console.log(y); // 2

console.log(window.foo); // ƒ foo() {}
console.log(foo); // ƒ foo() {}
```

반면 let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.  
let 전역 변수는 보이지 않는 개념적인 블록(전역 렉시컬 환경의 선언적 환경 레코드) 내에 존재한다.

```javascript
let x = 1;

console.log(window.x); // undefined
console.log(x); // 1
```

---

## 15.3 const 키워드

const 키워드는 상수를 선언하기 위해 사용하지만 반드시 상수만을 사용하지는 않는다.

### 15.3.1 선언과 초기화

**const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.**

```javascript
const foo; // SyntaxError: Missing initializer in const declaration
```

let 키워드와 마찬가지로 블록 레벨 스코프를 가지며, 변수 호이스팅이 발생하지 않는 것처럼 동작한다.

### 15.3.2 재할당 금지

**재할당이 금지된다.**

```javascript
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable.
```

### 15.3.3 상수

const 키워드로 선언된 변수에 원시 값을 할당한 경우 원시 값은 변경할 수 없는 값이고 const 키워드에 의해 재할당이 금지되므로 할당된 값을 변경할 수 있는 방법은 없다.

```javascript
let preTaxPrice = 100;

// 세후 가격
// 0.1의 의미를 명확히 할 필요가 있다
let afterTaxPrice = preTaxPrice + preTaxPrice * 0.1;

console.log(afterTaxPrice); // 110

// 세율을 의미하는 0.1은 변경할 수 없는 상수로서 사용될 값이다.
// 변수 이름을 대문자로 선언해 상수임을 명확히 나타낸다.

const TAX_RATE = 0.1;

let afterTaxPrice = preTaxPrice + preTaxPrice * TAX_RATE;

console.log(afterTaxPrice); // 110
```

일반적으로 상수의 이름은 대문자로 선언해 상수임을 나타낸다.  
여러 단어로 이뤄진 경우에는 언더스코어(\_)로 구분해서 스네이크 케이스로 표현하는 것이 일반적이다.

### 15.3.4 const 키워드와 객체

const 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다.

```javascript
const person = {
  name: "Lee",
};

// 객체는 변경 가능한 값이다. 따라서 재할당 없이 변경이 가능하다.
person.name = "Kim";

console.log(person); // {name: 'Kim'}
```

이처럼 const 키워드는 재할당을 금지할 뿐 '불변'을 의미하지는 않는다.  
프로퍼티 동적 생성, 삭제, 프로퍼티 값의 변경을 통해 객체를 변경하는 것은 가능하다.  
이때 객체가 변경되더라도 변수에 할당된 참조 값은 변경되지 않는다.

---

## 15.4 var VS let VS const

- 권장사항
  1. ES6를 사용한다면 var 키워드는 사용치 않는다.
  2. 재할당이 필요한 경우에 한정 let 키워드를 사용한다. 이때 변수의 스코프는 최대한 좁게 만든다.
  3. 재할당이 필요없는 상수와 객체에는 const 키워드를 사용한다. const 키워드는 재할당을 금지하므로 var, let 키워드보다 안전하다.

---
