---
tistoryBlogName: ruukr8080
tistoryTitle: var,let,const 차이
tistoryTags: var, let, const, 자바스크립트
tistoryVisibility: "3"
tistoryCategory: "0"
tistorySkipModal: true
tistoryPostId: "30"
tistoryPostUrl: https://ruukr8080.tistory.com/30
---

# var,let,const 차이

> 이 세가지 키워드의 차이를 이해하기 위해선 우선 스코프와 호이스팅을 이해해야한다.


# var
## 스코프
 
1.  기본적으로 "static" 전역 변수임
2. var 키워드로 선언된 변수가 함수 내부에서 선언 될 경우 그 변수는 함수 내에서만 사용 가능.

## 호이스팅
 >var로 선언한변수는 범위 내에서 맨 위로 올려지고, 값은 `undefined`로 초기화됨

예를 들어 아래와 같이 코드를 짬
```js

console.log(hi);
var hi = "hello"

```

그럼 js엔진은 우선 선언 키워드를 먼저 훑어보기 때문에 hi를 먼저 인식함. 값을 인식 안한채 콘솔로그 찍어버려서 초기값이 나옴옴
```js

var hi;
console.log(hi) // undefined
hi= "hello"

```


___


# let

## 스코프

1. `let`으로 선언된 변수는 해당 블록 내에서만 사용가능
2. `var`와 달리 `let`으로 선언하는 변수는 범위 내에서 다시 선언할 수 없음
3.  하지만 동일한 변수더라도 다른 범위 내에서 정의된다면 오류 안남. 다른 범위에 있으면 동일하게 생겼어도 다른 변수인거임

```js

let times = 4;

if ( times > 3 ) {
let say = "hi" 
console.log(say); //hi
}

console.log(say); //say is not defined 
```

> if문 블록 내에서 선언한 say는 console.log를 통해 잘 작동 했다.
> 밑에  블록 외부에서 console.log(say)는 오류가 났다.
> 왜냐면 let으로 선언한 say는 블록 내부에서만 유효하기 때문이다.

## 호이스팅
`var`와 마찬가지로 `let` 선언은 맨 위로 끌어올려짐
근데 `undefined(정의되지 않음)`으로 초기화되는 `var`와 다르게 `let`의 키워드는 초기화되진 않음. 선언 이전에 `let` 변수를 사용하려고 시도한다면 `Reference Error(참조 오류)`가 남.


---

# const 

>let이랑 거의 같음.
>let과의 차이는 `immutable`의 여부임 const는 불변객체, 즉 상수를 선언할 때 쓰임. let은 변수에 다른 값을 재할당할 수 있지만 const는 재할당 안됨.


