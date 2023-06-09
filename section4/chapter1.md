# 타입 별칭

## 함수타입 표현식(공식문서 명칭)

#### === (호출 시그니쳐, 함수 시그니쳐)

> 어떤 매개변수를 받고, 어떤 결과값을 반환하는지 이야기

```jsx
const add = (a: number, b: number): number => a + b;
// 기존 함수선언식에서 타입표기
type Add = (a: number, b: number) => number;
// 타입 별칭을 지정
const add: Add = (a, b) => a + b;
// 타입 별칭을 사용하면 선언식에서 생략가능합니다
```

## 타입 별칭의 재활용

```jsx
type Operation = (a: number, b: number) => number;
// 타입 별칭을 지정
const add: Operation = (a, b) => a + b;
const sub: Operation = (a, b) => a - b;
const multiply: Operation = (a, b) => a *+* b;
const divide: Operation = (a, b) => a / b;
// 타입 별칭을 사용하면 선언식에서 생략가능합니다
```

## 호출 시그니쳐(콜 시그니쳐)

> 함수도 객체임을 이용해 프로퍼티를 추가해줄수 있습니다

```tsx
type Operation2 = {
  (a: number, b: number): number;
  name: string;

};

const add2: Operation2 = (a, b) => a + b;
const sub2: Operation2 = (a, b) => a - b;
const multiply2: Operation2 = (a, b) => a *+* b;
const divide2: Operation2 = (a, b) => a / b;

add2.name 사용가능합니다
```
