---
tistoryBlogName: ruukr8080
tistoryTitle: arguments 프로퍼티
tistoryTags: arguments , 자바스크립트
tistoryVisibility: "0"
tistoryCategory: "0"
tistorySkipModal: true
tistoryPostId: "32"
tistoryPostUrl: https://ruukr8080.tistory.com/32
---
# arguments 객체

> **`arguments`** 객체는 함수에 전달된 인수에 해당하는 `Array` 형태의 객체입니다.

**참고:** "`Array` 형태"란 `arguments`가 [`length`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/length) 속성과 더불어 0부터 인덱스 된 다른 속성을 가지고 있지만, [`Array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)의 [`forEach`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach), [`map`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)과 같은 내장 메서드를 가지고 있지 않다는 뜻입니다.

`arguments` 객체는 모든 함수 내에서 이용 가능한 지역 변수입니다. `arguments` 객체를 사용하여 함수 내에서 모든 인수를 참조할 수 있으며, 호출할 때 제공한 인수 각각에 대한 항목을 갖고 있습니다. 항목의 인덱스는 0부터 시작합니다.

예를 들어, 함수가 세 개의 인수를 받은 경우 다음과 같이 접근할 수 있습니다.


```js
arguments[0];
arguments[1];
arguments[2];
```

각 인수를 설정하거나 재할당할 수도 있습니다.


```js
arguments[1] = "new value";
```

---
<br>
   <br>
   <br>
   <br>

`arguments` 객체는 [`Array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)가 아닙니다. `Array`와 비슷하지만, [`length`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/length) 빼고는 [`pop()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)과 같은 어떤 `Array` 속성도 없습니다. 그러나 실제 `Array`로 변환할 수 있습니다:


```js
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);
```

`arguments`를 실제 `Array`로 변환하기 위해 ES2015의 [`Array.from()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/from) 메서드 또는 [전개 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax)를 사용할 수도 있습니다.


```js
var args = Array.from(arguments);
var args = [...arguments];
```

 >형식상 받기로 선언된 것보다 많은 인수로 함수를 호출하는 경우 `arguments` 객체를 사용할 수 있습니다. 이 기법은 가변 인수가 전달될 수 있는 함수에 유용합니다. 함수에 전달된 인수의 수를 결정하기 위해 [`arguments.length` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments/length "Currently only available in English (US)")를 쓰세요, 그 뒤에 `arguments` 객체를 사용하여 각 인수를 처리하세요. 함수 [signature](https://developer.mozilla.org/ko/docs/Glossary/Signature/Function)에 매개변수의 수를 결정하기 위해서는, [`Function.length`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/length) 속성을 쓰세요.

---
<br><br><br><br>
## [속성](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments#%EC%86%8D%EC%84%B1)

[`arguments.callee`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments/callee)

현재 실행 중인 함수를 가리킵니다.

[`arguments.length`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments/length)

함수에 전달된 인수의 수를 가리킵니다.

[`arguments[@@iterator]`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments/@@iterator)

arguments의 각 인덱스 값을 포함하는 새로운 Array Iterator 객체를 반환합니다.