[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 대수 타입

> 여러개의 타입을 합성해서 새롭게 만들어낸 타입 1.합집합 타입 2.교집합 타입이 존재합니다

# 🥇 합집합 타입(Union Type)

> | 를 이용해서 연결할 수 있고 연결갯수의 제한은 없습니다.

```tsx
let a: string | number;
a = 1;
a = "hello";

let arr: (number | string | boolean)[] = [1, "hello", true];
```

## 객체 타입을 이용해 만드는 타입

```tsx
type Dog = {
  name: string;
  color: string;
};

type Person = {
  name: string;
  language: string;
};

type Union1 = Dog | Person;

let union1: Union1 = {
  name: "",
  color: "",
};

let union2: Union1 = {
  name: "",
  language: "",
};

let union3: Union1 = {
  name: "",
  color: "",
  language: "",
};

let union4: Union1 = {
  // 오류가 출력됩니다.
  name: "",
};
```

# 교집합 타임 (Intersection Type)

> 기본타입으로 교집합 타입을 만들면 거의 Never 타입이 됩니다.

```tsx
let variable: number & string;

type Dog = {
  name: string;
  color: string;
};

type Person = {
  name: string;
  language: string;
};

type Intersection = Dog & Person;

let intersection1: Intersection = {
  name: "",
  color: "",
  language: "",
};
```
