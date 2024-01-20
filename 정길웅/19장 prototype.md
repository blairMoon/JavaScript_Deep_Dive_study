## <span style="color:#f58f00;">19.1 객체지향 프로그래밍</span>
<span style="color:red">red</span>
---

객체지향 프로그래밍이란 `속성`값들을 사용하여 프로그램을 인식하거나 구별하려는 방향성을 의미한다. 예를 들어 사람에게는 성별, 나이, 체중, 학력, 성격 등 다양한 속성이 있다. 그 중 "이름"과 "주소"만 관심이 있다고 가정해보자. 이처럼 다양한 속성 중 몇 가지만 추려서 표현해내는 것을 `추상화`라고 한다.

```javascript
const person = {
	name:'lee'
  	address: 'seoul'
}

console.log(person) // {name: 'lee', address: 'seoul'}

const circle = {
  radius: 5,
  getDiameter(){
    return 2 * this.radius;
  }
}
console.log(circle); // {radius:5, getDiameter: f}
console.log(circle.getDiameter()); // 10
```

이처럼 속성을 통해 여러 개의 값을 하나의 단위로 구성한 복합적인 자료구조를 객체라 한다.

예제 중 circle 부분을 확인해보자. radius 부분은 상태로, getDiameter부분을 동작으로 볼 수 있다. 이때 객체의 상태 데이터를 `프로퍼티`, 동작 데이터를 `메서드`라고 부른다. 
## <span style="color:#f58f00;">19.2 상속과 프로토타입</span>

---

상속은 불필요하게 반복되는 데이터를 줄여주고 가독성을 높여준다는 데에 있어 의미가 있다. 아래의 예시를 살펴보자

```javascript
function Circle(radius){
  this.radius = radius;
  this.getDouble = function() {
    return this.radius * 2
  }
}
Circle.prototype.getArea = function () {
  return Math.PI * this.radius ** 2;
};


const circle1 = new Circle(1);
const circle2 = new Circle(2);

console.log(circle1.getDouble() === circle2.getDouble()) // false
console.log(circle1.getArea() === circle2.getArea()) // true

```
위 예시에 있는 getDouble 메서드와 getArea 메서드는 circle1이나 circle2에 공통적으로 있기에 같은 메서드를 공유한 것처럼 보이지만 실제로는 일반적인 방식을 사용했을 시 메서드가 복사가 되고 prototype을 활용한 메서드는 바인딩되어 상속으로 유지되고 있음을 알 수 있다. 

## <span style="color:#f58f00;">19.3 프로토타입 객체</span>

---
모든 객체는 `[[Prototype]]`이라는 내부 슬롯을 가지며 이 내부 슬롯의 값은 프로토타입의 참조이다. 객체가 생성될 때 객체 생성 방식에 따라 프로토타입이 결정되고 `[[Prototype]]`에 저장이 된다.

### <span style="color:#87CEEB;">19.3.1 __proto__ 접근자 프로퍼티</span>

모든 객체는 `__proto__` 접근자 프로퍼티를 통해 자신의 프로토타입, 즉 [[Prototype]] 내부 슬롯에 간접적으로 접근할 수 있다.

<span style="color:#008000">`__proto__`는 접근자 프로퍼티다.</span>


