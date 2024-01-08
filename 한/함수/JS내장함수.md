---
tistoryBlogName: ruukr8080
tistoryTitle: JS내장함수
tistoryTags: js 내장함수, js, 자바스크립트, 내장함수
tistoryVisibility: "3"
tistoryCategory: "0"
tistorySkipModal: true
tistoryPostId: "27"
tistoryPostUrl: https://ruukr8080.tistory.com/27
---
# 1) Object 객체

- 자바스크립트의 최상위 객체

- 생성

var object={};

var object=new Object();

- Object 객체의 메소드

constructor() : 객체의 생성자 함수를 나타냄

hasOwnProperty(name) : 객체가 name 속성을 가지고 있는지 확인

isPrototypeof(object) : 객체가 object의 프로토타입인지 검사

propertyIsEnumerable(name) : 반복문으로 열거 가능 여부 확인

toLocaleString() : 객체를 호스트 환경에 맞는 언어의 문자열로 변경

toString() : 객체를 문자열로 변경

valueOf()  : 객체의 값을 표시

# 2) Number 객체

- 숫자를 표현할 때 사용하는 객체

- 생성

var num = 1;

var num = new Number(1);

- Number 객체의 메소드

toExponential() : 숫자를 지수 표시로 나타낸 문자열 리턴 // 유효 숫자의 자릿수

toFixed() : 숫자를 고정 소수점 표시로 나타낸 문자열 리턴 // 소수점 자릿수

toPrecision() : 숫자를 길이에 따라 지수 표시 혹은 고정 소수점 표시로 나타낸 문자열 리턴

- Number 생성자 함수의 속성

MAX_VALUE : 자바스크립트에서 표현 가능한 최대 숫자

MIN_VALUE : 자바스크립트에서 표현 가능한 최소 숫자

NaN : Not a Number

POSITIVE_INFINITY : 양의 무한대 수

NEGATIVE_INFINITY : 음의 무한대 수

# 3) String 객체

- 문자열을 표현할 때 사용하는 객체

- String 객체의 속성

length : 문자열의 길이를 표시

- String 객체의 메소드

charAt(position) : 해당 인덱스 문자 반환

charCodeAt(position) : 해당 인덱스 문자를 유니코드로 반환

concat(args) : 매개변수로 입력한 문자열을 결합

indexOf(searchString, position) : 앞에서부터 일치하는 문자열의 인덱스 반환

lastIndexOf(searchString, position) : 뒤에서부터 일치하는 문자열의 인덱스 반환

match(regExp) : 문자열 안에 regExp가 있는지 확인

replace(regExp, replacement) : 문자열 안의 regExp를 replacement로 바꾼 뒤 리턴

search(regExp) : regExp와 일치하는 문자열의 위치 반환

slice(start, end) : 특정 위치의 문자열을 반환

split(separator, limit) : separator로 문자열을 자른 후 배열로 반환

substr(start, count) : start부터 count까지 문자열을 잘라서 반환

substring(start, end) : start부터 end까지 문자열을 잘라서 반환

toLowerCase() : 문자열을 소문자로 바꾸어 반환

toUpperCase() : 문자열을 대문자로 바꾸어 반환

- String 객체의 HTML 관련 메소드

anchor() : 문자열에 a태그 추가

big() : big태그 추가

blink() : blink 태그 추가

bold() : b 태그 추가

fixed() : tt 태그 추가

fontcolor(colorString) : font 태그와 color 속성을 추가

fontsize(fontSize) : font 태그와 size 속성을 추가

italics() : i 태그 추가

link(linkRef) : a 태그와 href 속성 추가

small() : small 태그 추가

strike() : strike 태그 추가

sub() : sub 태그 추가

sup() : sup 태그 추가

*String 객체는 문자열의 내용을 바꾸지 않고 반환하기 때문에 메소드 체이닝 가능

# 4) Array 객체

- 배열을 표현할 때 사용하는 객체

- 생성

var array=[값1, 값2...]; // 생성과 동시에 초기화

var array=new Array(); // 배열을 생성하기만 함

var array=new Array(배열크기); // 생성과 동시에 공간을 만들어 둠

var array=new Array(값1, 값2); // 생성과 동시에 초기화

- Array객체의 속성

length : 배열의 크기를 반환

- Array 생성자 함수의 메소드

Array.isArray() : 배열인지 확인

- Array객체의 메소드

속성을 변화시키는 메소드

pop() : 배열의 마지막 요소를 제거 후 리턴

push() : 배열의 마지막에 새로운 요소 추가

reverse() : 배열의 요소 순서 반전

sort() : 배열 요소 정렬// 기본값은 문자열 오름차순

*내림 차순으로 정렬: array.sort((a,b)=>{return b-a});

*셔플: arr.sort(()=>{return 0.5-Math.random()});

splice() : 요소의 지정된 부분 삭제 후 삭제한 요소 리턴

속성을 변화시키지 않는 메소드

slice() : 요소의 지정한 부분 반환

concat() : 매개변수로 입력한 배열의 요소를 모두 합쳐서 배열 생성 후 반환

join() : 배열 안의 모든 요소를 문자열로 변환 후 반환

indexOf() : 배열의 앞쪽부터 특정 요소의 위치 검색

lastIndexOf() : 배열의 뒷쪽부터 특정 요소의 위치 검색

반복 메소드

forEach() : 배열을 for in 반복문처럼 사용 가능

*사용 형태 array.forEach(function (element, index, array) {});  // 배열요소, 인덱스, 배열자체

map() : 기존의 배열에 특정 규칙을 적용해서 새로운 배열 생성

*사용 형태 var array2= array.map(function (element) {return element + 연산 });

조건 메소드

filter() : 특정 조건을 만족하는 요소를 추출해 새로운 배열 생성

*사용 형태 array = array.filter(function (element, index, array) { return element < 5; });

every() : 배열의 요소가 조건을 만족하는지 확인

some() : 배열의 요소가 특정 조건을 적어도 하나는 만족하는지 확인

*사용 형태 array.every(function (element, index, array) { return element < 10; });

-> every는 모든 요소, some은 단 하나라도 조건에 부합하는지 확인 후 true or false 반환

연산 메소드

reduce() : 배열의 요소가 하나가 될 때까지 요소를 왼쪽부터 두 개씩 묶는 함수 실행

*객체를 1:1로 짝지으며 기존 배열을 수정하지 않는 함수

reduceRight() : 위와 같으나 오른쪽부터 실행

*사용 형태 array.map((element, index, array) => { return 요소 } iniNum);

*Array 객체에는 특정 요소를 제거하는 객체가 없음

Array.//prototype//.remove =function (i) { this.splice(i, 1); } // 프로토타입에 remove 함수 추가

arr.remove(i); // 해당 인덱스 값 제거

# 5) Date 객체

- 날짜와 시간을 표시하는 객체

- 생성

var date = new Date(); // 매개변수를 입력하지 않으면 현재 시각으로 초기화

- 매개변수 예시

문자열: new Date('December 11, 2018');

숫자: new Date(2018, 12, 11, 2, 24, 23); // 연, 월-1, 일, 시, 분, 초, 밀리초 순서

Unix time: new Date(1351511); // 1970년 1월 1일 12시 자정 기준으로 경과한 시간(밀리초)

- Date 객체의 메소드

getTime() : Unix time 반환, 날짜 간격 계산시 사용

*메소드가 매우 많지만 대부분 get, set으로 이루어져 있으며 메소드명으로 기능 유추 가능

*getYear()메소드는 브라우저에 따라 다른 결과를 반환하기도 하니 getFullYear() 사용

# 6) Math 객체

- 수학과 관련된 속성과 메소드를 가진 객체

- Math 객체는 함수가 아닌 변수 // Math.속성 형태로 사용

- 기본 내장 객체 중 유일하게 생성자를 사용하지 않음

- Math 객체의 메소드

abs() : 절대값 반환

acos() : 아크 코사인 값 반환

asin() : 아크 사인 값 반환

atan() : 아크 탄젠트 값 반환

atan2(y, x) : x와 y의 비율로 아크 탄젠트 값 반환

ceil() : 크거나 같은 가장 작은 정수 반환

cos() : 코사인 값 반환

exp() : 자연로그의 제곱 반환

floor() : 작거나 같은 가장 큰 정수 반환

log() : 로그 값 반환

max() : 매개변수 중 가장 큰 값 반환

min() : 매개변수 중 가장 작은 값 반환

pow(x, y) : x의 y제곱 반환

random() : 0부터 1까지의 임의의 수 반환

round() : 반올림해서 반환

sin() : 사인 값 반환

sqrt() : 제곱근 반환

tan() : 탄젠트 값 반환

# 7) JSON(Javascript Object Notation) 객체

- 자바스크립트 객체 형태를 갖는 문자열

- JSON 객체의 메소드

JSON.stringify() : 자바스크립트 객체를 JSON 문자열로 변환

*객체 속성을 object 등이 아닌 문자열로 전체 다 확인 가능

jSON.parse() : JSON 문자열을 자바스크립트 객체로 변환

toJSON: function() {return 객체}; : 객체 내에 toJSON 메소드가 있으면 해당 메소드의 리턴값만 반환, 없으면 모든 키와 속성 반환