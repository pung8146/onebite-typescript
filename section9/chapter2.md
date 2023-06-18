[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다
①②③④⑤⑥⑦⑧⑨⑩⑪⑫⑬⑭⑮

# 🥇 infer

> 조건부타입내에서 특정타입만 추론할수있습니다.

## 첫 번째 예시

```tsx
type Func = ③(⑤) => string;

type ReturnType<T> = ②T extends ④(⑤) => string ? string : never;

type A = ReturnType①<Func>;

```

진행과정

> 타입변수②T에 ①<Func> 타입이 들어갑니다.
> ① === ③() => string 입니다.
> ④ () => string 이 비교하는 타입입니다.
> ③펑크타입이 ④의 서브타입인지 비교 가 진행됩니다.
> 같다면 string , 다르다면 nerver 타입이 됩니다.
> ③,④ 두 타입의 관계를 보면 ⑤()매개변수는 없으니 비교할게 없고
> 반환값만 보면되는데 반환값이 더큰함수가 슈퍼타입이 됩니다.
> 지금 ③,④ 타입이 동일하기에 서브타입이라고 취급할수있습니다.
> 그렇기에 string 이라고 할 수 있습니다.

## 두번 째 예시

```tsx
type FuncA = () => string;
type FuncB = ③() => number;

type ReturnType<T> = ①T extends ④() => string ? string : never;

type A = ReturnType<FuncA>;
type B = ReturnType②<FuncB>; 네버타입이 추론이 됩니다

```

> ①타입변수T에는②<FuncB>가 들어갑니다.
> T는 ③()=>number 가 됩니다.
> 그리고 T는 ④() => string 과 비교하게 되고
> ③④를 비교하니 서로소 집합 입니다.(둘중 누구도 서브,슈퍼 타입아님)
> 그러므로 조건식은 거짓이되고 never 가 출력됩니다.

## 세번 째 예시

** infer 사용 **

```tsx
type FuncA = () => ③string;
type FuncB = () => number;

type ReturnType<T> = ④T extends ①() => ②infer R ? ⑤R : never;

type A = ReturnType<FuncA>; 스트링 이 출력됩니다.
type B = ReturnType<FuncB>; 넘버가 출력됩니다.

```

> 한수의 반환값 타입을 ① infer R : R로 변경해줍니다.
> ②infer R 이라고 선언한것은 일단 R이라고 생각합니다.
> A 타입의 상황을보면 타입변수T에 FuncA가 들어갔습니다.
> ③ === ④ 이 되었고 ④가 () => infer R 인지 비교합니다.
> R타입은 `FuncA === () =>R` 참으로 만드는 타입을 추론하도록 동작합니다.
> `FuncA === () =>R` 참이 될려면 R이 string 타입으로 추론됩니다(서브타입이 되야하므로).
> 참이되면 ⑤R 이 반환되고 R은 string 이므로 string 이 출력됩니다.

## 네번 째 예시

infer다음에 오는 조건식을 추론 할 수 없는 경우를 ** 조건식이 거짓이 됩니다 **

```tsx
type FuncA = () => string;
type FuncB = () => number;

type ReturnType<T> = T extends ②() => infer R ? R : never;

type A = ReturnType<FuncA>;
type B = ReturnType<FuncB>;
type C = ReturnType<①number>;

```

> ①넘버타입이 이`②() => infer R`타입의 서브 타입이 될 수 있는 R타입의 조건을 만족할수 없어 ** 추론 불가 ** 상태가 됩니다.
> 조건식이 거짓이라 판단되어 never 가 출력됩니다.

## 다섯 번째 예시

```tsx
type RromiseUnpack<T> = ②T extends ③Promise<infer R> ? R : never;
1. T는 프로미스 타입어야한다. `T extends Promise<any> ? any : never;` 이럴 경우 프로미스 타입이면 무조건 any를 반환합니다.

2. 프로미스 타입의 결과값 타입을 반환해야 한다.
3.

type RromiseA = PromiseUnpack<①Promise<number>>; // number 타입이 되길 희망합니다
type RromiseA = PromiseUnpack<①Promise<string>>; // string 타입이 되길 희망합니다
```

> RromiseUnpack<T> 역할은 Promise<number> 의 결과값만 가져오는 기능을 구현합니다.
> ①Promise<number>을 ②T에 제공하는 상황
> ①Promise<number> 타입이 ③Promise<infer R> 타입에 서브타입이 되는 R타입을 추론하게 합니다.
> 즉 number 타입이 됩니다.
