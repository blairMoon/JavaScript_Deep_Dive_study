오타나 문법 지식의 미비로 인한 실수는 항상 존재하는법이다. 이럴 때 오류를 발생시키기 어려운 개발 환경을 만들고 그 환경에서 개발하는 것이 근본적인 해결책이 될 수 있다.
## <span style="color:#f58f00;">20.1 strict mode의 적용</span>
전역의 선두 또는 함수 몸체의 선두에 'use strict'를 추가한다. 
```js
'use strict'

// Reference Error: x is not defined
function foo() {
 x=100;
}
```
## <span style="color:#f58f00;">20.2 strict mode 피해야 하는 사례</span>
### <span style="color:#87CEEB;">20.2.1 전역사용</span>
이러한 strict mode를 전역에 적용하는 것은 왜 피해야 할까? 그 이유는 strict mode 와 non-strict mode 스크립트를 혼용하는 것이 오류를 발생시킬 수 있기 때문이다.

### <span style="color:#87CEEB;">20.2.2 함수 단위 사용</span>
어떤 함수에는 strict mode를 적용하고 어떤 함수에는 빼는 방식으로 접근한다면 굉장히 번거롭고 불편한 문제가 발생할 수 있다. 

## <span style="color:#f58f00;">20.3 strict mode가 발생시키는 에러</span>
### <span style="color:#87CEEB;">20.3.1 암묵적 전역</span>

```js
// 선언하지 않은 변수를 참조하면 Reference Error가 발생한다
(function(){
  'use strict'
  x=1;
  console.log(x);
}());

//delete 연산자로 변수, 함수, 매개변수를 삭제하면 syntax error가 발생한다.
(function(){
  'use strict'
  var x=1;
  delete x; //SyntaxError: Delete of an unqualified identifier in strict mode
  
  function foo(a) {
    delete a; //SyntaxError: Delete of an unqualified identifier in strict mode
  }
  delete foo; //SyntaxError: Delete of an unqualified identifier in strict mode
}());

//매개변수가 중복되면 syntax error가 발생한다
(function(){
  'use strict'
  //SyntaxError: Duplicate parameter name not allowed in this context
  function foo(x,x){
    return x+x;
  }
  console.log(foo(1,2));
}())

//with문을 사용하면 syntax error가 발생한다.
(function(){
  'use strict'
  //SyntaxError: Duplicate parameter name not allowed in this context
  with({ x: 1 }) {
    console.log(x);
  }
}())
```

