# 함수

- 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의한 것
- 함수는 값이며, 여러개 존재할 수 있으므로 특정 함수를 구별하기 위해 식별자인 함수 이름을 사용 할 수 있다. <br/><br/>
  함수는 **함수 정의**를 통해 생성한다. 자바스크립트의 함수는 다양한 방법으로 정의할 수 있다. 다음은 함수 선언문을 통해 함수를 정의한 예다.

```javascript
function add(x, y) {
  return x + y;
}
```

함수 정의만으로 함수가 실행되는 것은 아니다.<br/><br/>
인수를 매개변수를 통해 함수에 전달하면서 함수의 실행을 명시적으로 지시해야한다.  
이를 **함수 호출**이라 한다. 함수를 호출하면 코드 블록에 담긴 문들이 일괄적으로 실행되고 실행결과, 즉 반환값을 반환한다.

```javascript
// 함수 호출
var result = add(2, 5);

// 함수 add에 인수 2, 5를 전달하면서 호출하면 반환값 7을 반환한다.
console.log(result); // 7
```

---

## 함수를 사용하는 이유

함수는 몇 번이든 호출할 수 있으므로 **코드의 재사용**이라는 측면에서 매우 유용하다.  
코드의 중복을 억제하고 재사용성을 높이는 함수는 유지보수의 편의성을 높이고 실수를 줄여 **코드의 신뢰성**을 높이는 효과가 있다.

- 함수는 객체 타입의 값이다. 따라서 이름(식별자)를 붙일 수 있다.
- 적절한 함수 이름은 함수의 내부 코드를 이해하지 않고도 함수의 역할을 파악할 수 있게 돕는다. 이는 **코드의 가독성**을 향상시킨다.
  <br/>

## 함수리터럴

- function 키워드, 함수 이름, 매개 변수 목록, 함수 몸체로 구성된다.

```javascript
// 변수에 함수 리터럴을 할당
var f = function add(x, y) {
  return x + y;
};
```

- 함수 리터럴의 구성요소는 다음과 같다. <br/>

| 구성요소      | 설명                                                                                                                                                                                                                                                                                                       |
| :------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 함수 이름     | 1. 함수 이름은 식별자다. 따라서 식별자 네이밍 규칙을 준수해야 한다.<br/> 2. 함수 몸체 내에서만 참조할 수 있는 식별자다.<br/>3. 생략 할 수 있다. 이름이 있는 함수를 **기명함수**, 이름이 없는 함수를 무명/익명함수라 한다.                                                                                  |
| 매개변수 목록 | 1. 0개 이상의 매개변수를 소괄호로 감싸고 쉼표로 구분<br/>2. 각 매개변수에는 함수를 호출할 때 지정한 인수가 순서대로 할당된다. 즉, 매개변수 목록은 순서에 의미가 있다.<br/>3. 매개변수는 함수 몸체 내에서 변수와 동일하게 취급된다. 따라서 매개변수도 변수와 마찬가지로 식별자 네이밍 규칙을 준수해야 한다. |

- 리터럴은 값을 생성하기 위한 표기법이다.
  <br/>따라서 함수 리터럴도 평가되어 값을 생성하며, 이 값은 객체다.즉 **함수는 객체다**
- 일반 객체는 호출 할 수 없지만 함수는 호출할 수 있다.

## 함수 정의

함수를 호출하기 이전에 인수를 전달받을 매개변수와 실행할 문들, 그리고 반환할 값을 지정하는 것

- 함수를 정의하는 방법에는 4가지가 있다.

1. 함수 선언문

```javascript
function add(x, y) {
  return x + y;
}
```

2. 함수 표현식

```javascript
var add = function (x, y) {
  return x + y;
};
```

3. Function 생성자 함수

```javascript
var add = new Function('x', 'y', 'return x + y');
```

4. 화살표 함수(ES6)

```javascript
var add = (x, y) => x + y;
```

- 모든 함수 정의 방식은 함수를 정의한다는 면에서는 동일하지만 미묘하지만 중요한 차이가 있다.

- ### 함수 선언문

```javascript
// 함수 선언문
function add(x, y) {
  return x + y;
}
```

함수 선언문은 함수 리터럴과 형태가 동일하다. 단, 함수 리터럴은 함수 이름을 생략할 수 있으나<br/> **함수 선언문은 함수 이름을 생략할 수 없다.**

- 함수 선언문은 표현식이 아닌 문이다.<br/>크롬 개발자 도구의 콘솔에서 함수 선언문을 실행하면 완료 값 undefined가 출력된다.<br/>만약 표현식인 문이라면 표현식이 평가되어 생성된 함수가 출력되어야 한다.
- 함수 선언문도 표현식이 아닌 문이므로 변수에 할당할 수 없다.<br/>

- 코드의 문맥에 따라 동일한 함수 리터럴을 표현식이 아닌 문인 함수 선언문으로 해석하는 경우와 표현식인 문인 함수 리터럴 표현식으로 해석하는 경우가 있다.

예를들어 { }은 블록문일 수도 있고 객체 리터럴일 수도 있다. <br/>
{ }이 단독으로 존재하면 블록문으로 해석하고, 값으로 평가되어야 할 문맥에서 피연산자로 사용되면 객체 리터럴로 해석한다.

- 생성된 함수를 호출하기 위해 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하고, 거기에 함수 객체를 할당한다.
- 함수 이름으로 호출 하는 것이 아니라 함수 객체를 가리키는 식별자로 호출

- ### 함수 표현식

- 일급 객체
  - 값의 성징를 갖는 객체

함수는 일급 객체이므로 함수 리터럴로 생성한 함수 객체를 변수에 할당할 수 있다.<br/>
이러한 함수 정의 방식을 **함수 표현식**이라 한다.

함수 리터럴의 함수이름은 생략가능 이를 익명함수라 함. 생략하는 것이 일반적.

함수 선언문은 "표현식이 아닌 문"이고 함수 표현식은 "표현식인 문"이다.

- ### 함수 생성 시점과 함수 호이스팅
  함수 표현식으로 정의한 함수는 함수 표현식 이전에 호출 할 수 없다. 함수 선언문으로 정의한 함수와 함수 표현식으로 정의한 삼수의 생성 시점이 다르기 때문.

함수 선언문은 런타임 이전에 자바스크립트 엔진에 의해 먼저 실행. 런타임 이전에 함수 객체가 먼저 생성. 함수 이름과 동일한 이름의 식별자를 암묵적으로
생성하고 생성된 함수 객체를 할당한다.

함수 선언문을 통해 암묵적으로 생성된 식별자는 함수 객체로 초기화된다.
함수 표현식은 변수에 할당되는 값이 함수 리터럴인 문이기 때문에 함수 호이스팅이 아닌 변수 호이스팅이 발생한다.
함수 표현식으로 정의한 함수는 반드시 함수 표현식 이후에 참조 또는 호출해야한다.

- ### Function 생성자 함수

  new를 생략가능 클로저로 쓸수 없어서 리턴에 new Function을 넣을수 없는 단점이 존재
  선언문이랑 표현식이랑은 다르게 동작한다.

- ### 화살표 함수
  생성자 함수로 사용할 수 없으며, 기존 함수와 this 바인딩 방식이 다르고, prototype 프로퍼티가 없으며 arguments 객체를 생성하지 않는다.

## 함수 호출

함수는 함수를 가리키는 식별자와 한 쌍의 소괄호인 함수 호출 연산자로 호출한다. 함수 호출 연산자 내에는 0개 이상의 인수를 쉼표로 구분해서 나열한다.

매개변수에 인수가 순서대로 할당되고 함수 몸체의 문들이 실행되기 시작한다.

- ### 매개변수와 인수
  함수를 실행하기 위해 필요한 값을 함수 외부에서 함수 내부로 전달할 필요가 있는 경우, 매개변수를 통해 인수를 전달.

함수가 호출되면 함수 몸체 내에서 암묵적으로 매개변수가 생성되고 일반 변수와 마찬가지로 undefined로 초기화된 이후 인수가 순서대로 할당된다.

매개변수의 스코프는 함수 내부다. 매개변수보다 인수가 더 많은 경우 초과된 인수는 무시된다.
모든 인수는 암묵적으로 arguments 객체의 프로퍼티로 보관된다.

- ### 인수 확인

1. 자바스크립트 함수는 매개변수와 인수의 개수가 일치하는지 확인하지 않는다.
2. 자바스크립트는 동적 타입 언어다. 따라서 자바스크립트 함수는 매개변수의 타입을 사전에 지정할 수 없다.

- 인수가 전달되지 않은 경우 단축 평가를 사용해 매개변수에 기본값을 할당하는 방법도 있다.
- 매개변수에 인수를 전달하지 않았을 경우와 undefined를 전달한 경우에만 유효

- ### 매개변수의 최대 개수
  매개변수는 순서에 의미가 있다. 이상적인 매개변수 개수는 0개이며 적을수록 좋다.

함수는 한가지 일만 해야하며 가급적 작게 만들어야 한다. 최대 3개 이상을 넘지 않는 것을 권장한다.

- 매개변수의 개수가 많다는 것은 함수가 여러가지 일을 한다는 증거이므로 바람직하지 않다.
- 주의할 것은 함수 외부에서 함수 내부로 전달한 객체를 함수 내부에서 변경하면 함수 외부의 객체가 변경되는 부수 효과가 발생한다는 것

- ### 반환문
  return 키워드 뒤에 반환값으로 사용할 표현식을 명시적으로 지정하지 않으면 undefined가 반환된다.
  반환문은 함수 몸체 내부에서만 사용할 수 있다. 전역에서 반화문을 사용하면 문법에러가 발생한다.

## 참조에 의한 전달과 외부 상태의 변경

원시 값은 값에 의한 전달, 객체는 참조에 의한 전달방식으로 동작한다.
매개변수도 함수 몸체 내부에서 변수와 동일하게 취급, 매개변수 또한 타입에 따라 값에 의한 전달, 참조에 의한 전달 방식을 그대로 따른다.

- 원시 타입 인수는 값 자체가 복사되어 매개변수에 전달되기 때문에 함수 몸체에서 그 값을 변경해도 원본은 훼손되지 않는다.
- 여러 변수가 참조에 의한 전달 방식을 통해 참조 값을 공유하고 있다면 이 변수들은 언제든지 참조하고 있는 객체를 직접 변경할 수 있다.

- 순수함수
  - 외부 상태를 변경하지 않고 외부 상태에 의존하지도 않는 함수

## 다양한 함수의 형태

- ### 즉시 실행 함수

  단 한번만 호출되며 다시 호출할 수 없다. 기명 함수는 함수 선언문이 아니라 함수 리터럴로 평가되며 함수 이름은 함수 몸체에서만 참조할 수 있는 식별자이므로 즉시 실행 함수를 다시 호출할 수는 없다.

- 즉시 실행 함수는 반드시 그룹 연산자 (...) 로 감싸야 한다.
- 그룹 연산자의 피연사는 값으로 평가되므로 기명 또는 무명 함수를 그룹 연산자로 감사면 함수 리터럴로 평가되어 함수 객체가 된다.

- ### 재귀 함수
  함수가 자기 자신을 호출하는 것을 재귀 호출이라 한다.
- 반복되는 처리를 위해 사용한다.
- 함수 외부에서 함수를 호출할 때는 반드시 함수를 가리키는 식별자로 해야 한다.
- 재귀 호출을 멈출 수 있는 탈출 조건을 반드시 만들어야 한다.

반복문 없이 구현할 수 있다는 장점이 있지만 무한 반복에 빠질 위험이 있고, 이로 인해 stack overflow error를 발생시킬 수 있으므로 주의해서 사용해야 한다.
더 직관적으로 이해하기 쉬울 때만 한정적으로 사용하는 것이 바람직.

- ### 중첩 함수
  함수 내부에 정의된 함수를 중첩 함수 또는 내부 함수라 한다. 중첩 함수를 포함하는 함수는 외부 함수라 부른다.
  중첩 함수는 외부 함수 내부에서만 호출할 수 있다.
- 단, 호이스팅으로 인해 혼란이 발생할 수 있으므로 if 문이나 for 문 등의 코드블록에서 함수 선언문을 통해 함수를 정의하는 것은 바람직하지 않다.

- ### 콜백 함수
  함수의 매개변수를 통해 다른 함수의 내부로 전달되는 함수
- 매개변수를 통해 함수의 외부에서 콜백 함수를 전달받은 함수를 고차 함수라고 한다.
- 고차 함수는 콜백 함수를 자신의 일부분으로 합성한다.

고차 함수는 매개변수를 통해 전달받은 콜백 함수의 호출 시점을 결정해서 호출한다.

콜백함수는 고차 함수에 의해 호출되며 이대 고차 함수는 필요에 따라 콜백 함수에 인수를 전달할 수 있다.

- 콜백 함수를 호출하지 않고 함수 자체를 전달해야 한다.
- 콜백 함수는 비동기 처리뿐 아니라 배열 고차 함수에서도 사용된다.

- ### 순수 함수와 비순수 함수
- 순수 함수

  - 어떤 외부 상태에 의존하지도 않고 변경하지도 않는, 즉 부수 효과가 없는 함수
  - 동일한 인수가 전달되면 언제나 동일한 값을 반환한다.
  - 인수를 변경하지 않는 것이 기본이다. 인수의 불변성을 유지.
  - 함수의 외부 상태를 변경하지 않는 것이 기본.

- 비순수 함수
  - 외부 상태에 의존하거나 외부 상태를 변경하는, 즉 부수 효과가 있는 함수
  - 인수를 전달받지 않고 함수 내부에서 외부 상태를 직접 참조하면 외부 상태에 의존하게 되어 반환값이 변할수 있고, 외부 상태도 변경할 수 있다.
  - 비순수 함수를 최대한 줄이는 것은 부수 효과를 최대한 억제하는 것과 같다.

함수형 프로그래밍은 순수 함수와 보조 함수의 조합을 통해 외부 상태를 변경하는 부수 효과를 최소화해서 불변성을 지향하는 프로그래밍 패러다임이다.

조건문과 반복문을 제거해서 복잡성을 해결하며, 변수 사용을 억제하거나 생명주기를 최소화해서 상태 변경을 피해 오류를 최소화하는 것을 목표로 한다.
