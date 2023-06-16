[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 분산적인 조건부 타입

> 조건부 타입이라는건 조건부타입을 유니온타입과 함께 사용할때 조건부타입이 분산적으로 동작하게 업그레이드되는것

```tsx
type StringNumberSwitch<T> = T extends number ? string : number;

let a: StringNubmerSwitch<number>; // string출력이됩니다
let b: StringNubmerSwitch<string>; // number출력됩니다
let c: StringNubmerSwitch①<number | string>; //<string|number> 타입으로 출력됩니다
let d: StringNubmerSwitch②<boolean | number | string>; //<string|number> 타입으로 출력됩니다
```

> ① 유니온타입을 넣을경우 한번은 number, 다른한번 string 타입이 .들어가고 과정으로 두개의 결과가나옵니다
> ① StringNumberSwitch<number> | StringNumberSwitch<stirng>
> ① 이후 다시 유니온타입으로 묶이고 <string|number> 가 됩니다.

> ② 1단계 세개의 결과로 분리됩니다.
> ② 이후 유니온으로 묶이게 됩니다 <number | string | number>
> ② 중복을 제거하면 <number | string >가 됩니다

## 실용적인 예제

> 유니온에서 특정 타입만 제거 하는 방법

```tsx
type Exclude<T, U> = T extends U ? never : T;

type A = Exclude<number | string | boolean, string>;
 1 단계
 Exclude<number , string> |
 Exclude<string , string> |
 Exclude<boolean, string>

 2 단계
 T:number U:string 넘버는 스트링의 서브타입이 아니므로 거짓 T => number |
 never |
 boolean이 출력

 3 결과
 number | never | boolean 이 됩니다

 4 최종결과
 never 는 공집합이므로 number | boolean 이 됩니다
```

## 실용적인 예제2

> U 에 해당되는거만 출력합니다

```tsx
type Extract<T, U> = T extends U ? T : nerver;

type B = Extract<number | string | boolean, string>;
```

## 분산적인 조건부 타입이 되지 않을려면

```tsx
type StringNumberSwitch<T> = T extends ①[number] ? string : number;

let a: StringNubmerSwitch<number>; // string출력이됩니다
let b: StringNubmerSwitch<string>; // number출력됩니다
let c: StringNubmerSwitch<number | string>; //<string|number> 타입으로 출력됩니다
let d: StringNubmerSwitch<boolean | number | string>; //<string|number> 타입으로 출력됩니다
```

> ① extends 옆에 [] 감싸두면 분산되지 않습니다.
