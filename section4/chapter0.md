# 함수 타입 정의

## JS에서 함수를 설명하는 가장 좋은방법은?

> 어떤 매개변수를 받고, 어떤 결과값을 반환하는지 이야기

```jsx
function func(a, b) {
  return a + b;
}
```

## TS에서 함수를 설명 하는 가장 좋은 방법은?

> 어떤 [타입의] 매개 변수를 받고, 어떤 [타입의] 결과값을 반환 하는지 이야기
> 매개변수 뒤에 타입이 없어도 return 값 기준으로 타입을 추론해줍니다

```tsx
function func(a: number, b: number): number {
  return a + b;
}
```

## 화살표 함수의 타입을 정의하는 방법

> 자동으로 추론해줍니다

```tsx
const add = (a: number, b: number) => a + b;
```

## 함수의 매개변수

### 선택적 매개변수

> 따로 ?가 없는 매개변수를 필수 매개변수라고 합니다.
> tall?number 같이 ?가 있는걸 ** 선택적 매개변수 ** 라고 합니다
> ** 선택적 매개 변수는 필수 매개변수 앞에 있으면 안됩니다 **

```tsx
function introduce(name = "박상훈", age: number, tall?: number) {
  console.log(`name:${name}`);
  console.log(`tall:${tall}`); // tall 은 undefinend일수도있어서 숫자 연산은 따로 처리를 해줘야합니다.
  if (typeof tall === "number") {
    console.log(`tall:${tall + 10}`); // 타입 좁히기로 number을 확실히 해줍니다
  }
}
introduce("박상훈", 30, 170);
introduce("박상훈");
```

## rest 파라미터

> 몇개의 파라미터가 들어올지 모를때 ...rest 를 이용합니다

```tsx
function getSum(...rest: number[]) {
  let sum = 0;
  rest.foreach((it) => (sum += it));

  return sum;
}

getSum(1, 2, 3); //6
```
