# strict mode

## strict mode란?

```javascript
function foo() {
  x = 10;
}
foo();

console.log(x); // ?
```

foo 함수 내에서 선언하지 않은 x 변수에 값 10을 할당했다. x 변수를 찾아야 x에 값을 할당할 수 있기 때문에 자바스크립트 엔진은 x변수가 어디에서 선언되었는지 스코프 체인을 통해 검색하기 시작한다.

먼저 foo 함수의 스코프에서 검색을 하고 foo 함수의 스코프에는 x 변수 선언이 없으므로 검색에 실패할 것이고, foo 함수 컨텍스트의 상위 스코프에서 x 변수의 선언을 검색한다.

전역 스코프에도 x 변수의 선언이 존재하지 않기 때문에 **ReferenceError**를 발생시킬 것 같지만 자바스크립트 엔진은 암묵적으로 전역 객체에 x 프로퍼티를 동적 생성한다. 이러한 현상을 **암묵적 전역**이라 한다.

개발자의 의도와는 상관없이 발생한 암묵적 전역은 오류를 발생시키는 원인이 될 가능성이 크다.

- 반드시 var, let, const 키워드를 사용하여 변수를 선언한 다음 사용해야 한다.

이를 지원하기 위해 ES5부터 strict mode가 추가되었다. strict mode는 자바스크립트 언어의 문법을 좀 더 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 잇는 코드에댈해 명시적인 에러를 발생시킨다.

## strict mode의 적용

strict mode를 적용하려면 전역의 선두 또는 함수 몸체의 선두에 'use strict'; 를 추가한다. 전역의 선두에 추가하면 스크립트 전체에 strict mode가 적용된다.

```javascript
'use strict';

function foo() {
  x = 10; // referenceError: x is not defined
}
foo();
```

함수 몸체의 선두에 추가하면 해당 함수와 중첩 함수에 strict mode가 적용된다.

## 전역에 strict mode를 적용하는 것은 피하자.

전역에 적용한 strict mode는 스크립트 단위로 적용된다.

strict mode 스크립트와 non-strict mode 스크립트를 혼용하는 것은 오류를 발생시킬 수 있다.

이러한 경우 즉시 실햄 함수로 스크립트 전체를 감싸서 스코프를 구분하고 즉시 실행 함수의 선두에 strict mode를 적용한다.

```javascript
// 즉시 실행 함수의 선두에 strict mode 적용
(function () {
  'use strict';

  // Do something...
})();
```

## 함수 단위로 strict mode를 적용하는 것도 피하자

- 함수 단위로 strict mode를 적용할 수도 있다.

어떤 함수는 strict mode를 적용하고 어떤 함수는 strict mode를 적용하지 않는 것은 바람직하지 않으며 모든 함수에 일일이 strict mode를 적용하는 것은 번거로운 일이다.

- strict mode는 즉시 실행 함수로 감싼 스크립트 단위로 적용하는 것이 바람직하다.

## strict mode가 발생시키는 에러

- ### 암묵적 전역
  선언하지 않은 변수를 참조하면 ReferenceError가 발생한다.

```javascript
(function () {
  'use strict';

  x = 1;
  console.log(x); // ReferenceError : x is not defined
})();
```

- ### 변수, 함수, 매개변수의 삭제
  delete 연산자로 변수, 함수, 매개변수를 삭제하면 SyntaxError가 발생한다.

```javascript
(function () {
  'use strict';

  var x = 1;
  delete x; // SyntaxError: Delete of an unqualified identified in strict mode.

  function foo(a) {
    delete a; // SyntaxError: Delete of an unqualified identified in strict mode.
  }
  delete foo; // SyntaxError: Delete of an unqualified identified in strict mode.
})();
```

- ### 매개변수 이름의 중복
  중복된 매개변수 이름을 사용하면 SyntaxError가 발생한다.

```javascript
(function () {
  'use strict';

  // SyntaxError: Duplicate parameter name not allowed in this context
  function foo(x, x) {
    return x + x;
  }
  console.log(foo(1, 2));
})();
```

- ### with 문의 사용

  with 문을 사용하면 SyntaxError가 발생한다. with 문은 전달된 객체를 스코프 체인에 추가한다. with 문은 동일한 객체의 프로퍼티를 반복해서 사용할 때 객체 이름을 생략할 수 있어서 코드가 간단해지는 효과가 있지만 성능과 가독성이 나빠지는 문제가 있다

- 따라서 with 문은 사용하지 않는 것이 좋다.

```javascript
(function () {
  'use strict';

  // SyntaxError: Strict mode code may not include a with statement
  with ({ x: 1 }) {
    console.log(x);
  }
})();
```

## strict mode 적용에 의한 변화

- ### 일반 함수의 this

  strict mode에서 함수를 일반 함수로서 호출하면 this에 undefined가 바인딩된다. 생성자 함수가 아닌 일반 함수 내부에서는 this를 사용할 필요가 없기 때문이다.

- ### arguments 객체
  strict mode에서는 매개변수에 전달된 인수를 재할당하여 변경해도 arguments 객체에 반영되지 않는다.

```javascript
(function (a) {
  'use strict';
  // 매개변수에 전달된 인수를 재할당하여 변경
  a = 2;

  // 변경된 인수가 arguments 객체에 반영되지 않는다.
  console.log(arguments); // { 0 : 1, length: 1 }
})(1);
```
