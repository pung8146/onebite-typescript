[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다
①②③④⑤⑥⑦⑧⑨⑩⑪⑫⑬⑭⑮

# 🥇 조건부 타입 기반의 유틸리티 타입들

> -Exclude<T,U>,Extract<T,U>,ReturnType<T>

# Exclude

> - 제외하다, 추방하다
> - T 에서 U 를 제거하는 타입

## 예시

```tsx
type Exclude<T,U> = T extends U? never | T;
// T 가 U를 확장하면 never 아니면 T를 반환하는 코드

type A = Exclude<string | boolean,boolean>

```

1단계
하나씩 대입합니다.

> Exclude<string,boolean> // string
> Exclude<boolean,boolean> // never

2단계
유니온 으로 묶어줍니다.

> stirng | never => string // never 는 공집합이라 사라집니다.

# Extract <T , U>

> - T에서 U 를 추출 하는 타입
> - 예시코드는 ** boolean 만 남게됩니다 **

```tsx
type Extract<T, U> = T extends U ? T : never;

type B = Extract<string | boolean, boolean>;
```

# ReturnType<T>

> 함수의 반환값 타입을 추출하는 타입

```tsx
type ReturnType<T extends (...args:any) => =
infer R

function funcA {
  return 'hello'
}

function funcB() {
  return 10;
}

type ReturnA = ReturnType<typeof funcA> // stirng타입 이됩니다
type ReturnB = ReturnType<typeof funcB> // number타입 가됩니다
```
