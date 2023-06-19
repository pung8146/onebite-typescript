[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다
①②③④⑤⑥⑦⑧⑨⑩⑪⑫⑬⑭⑮

# 🥇 유틸리티 타입

> 유틸리티타입 : 제네릭,맵드타입,조건부타입 등의 타입 조작 기능을 이용해 실무에서 자주 사용되는 타입을 미리 만들어 놓은것

## 유틸리티 타입

> 가장 자주 활용되는 유틸리티 타임 #사진

## 예시

```tsx
interface Person {
  name: string;
  age: number;
}

const person: Readonly<Person> = {
    name:"이정환',
    age:30
}

```

## Partial<T>

```tsx
interface Person {
  name: string;
  age: number;
}

const person: Partial<Person> = {
    name:"이정환',
}
```

- Readonly 라는 유틸리티 타입을 사용하면 타입변수로 전달한
  모든프로퍼티들이 Readonly 속성이 됩니다.

- ** Partial<T> ** 모든 프로퍼티들을 유틸리티 타입으로 변경합니다
