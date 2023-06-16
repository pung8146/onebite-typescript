[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇조건부 타입 소개

## 조건부타입 사용법

```tsx
type A = number ①extends string ? string : number;
```

> ① 넘버 타입이 스트링 타입을 확장하는 타입이맞다면 stirng 아니면 number => 타입A 는 number타입이 됩니다.

## 객체 타입

```tsx
type ObjA = {
  a: number; // 슈퍼타입
};

type ObjB = {
  a: number; // 서브타입
  b: number;
};

type B = ObjB extends ObjA ? number : string; // 참이되어 number 타입이 됩니다
```

## 제네릭 과 조건부 타입

```tsx
type StringNumberSwitch①<T> = T extends number ? string : number;

let varA : StringNumberSwitch<number>// string출력
let varB : StringNumberSwitch<string>// number출력

```

> ① 제네릭 타입 과 같이쓰면 타입을 가변적으로 쓰면서도 논리의흐름에 따라 타입을 바꿔줄수있습니다.

## 타입이 string 하나 일 경우 함수사용에 문제가 없습니다.

```tsx
function removeSpaces1(text: string) {
  return text.replaceAll(" ", ""); // 모든 공백을 빈문자로 만들어줌
}

let result1 = removeSpaces1("hi im Psh");
result.toUpperCase(); // 문자열 이기 때문에 사용가능합니다
```

## 유니온 타입으로 사용시

> undefined 가 추가되었기 때문에 오류가 발생합니다.

```tsx
function removeSpaces2(text: string | undefined | null) {
  if (typeof text === "string") {
    return text.replaceAll(" ", ""); // 타입좁히기를 사용해줘야합니다
  } else {
    return undefind;
  }
}

let result2 = removeSpaces2("hi im Psh");
result2.toUpperCase(); // undefined가 추가되어 오류가 나옵니다.
```

## 제네릭 타입과 조건부타입

```tsx
⑤function removeSpaces3①<T>(text: T): ②T extends string ? string : undefined


function removeSpaces3①<T>(text: T): ②T extends string ? string : undefined {
  if (typeof text === "string") {
    return text.replaceAll(" ", "") ④as any;
  } else {
    return undefind;
  }
}

let result3 = removeSpaces3(③"hi im Psh");
result3.toUpperCase(); // unde

let result4 = removeSpaces4(③undefined);
```

> ① <T>제네릭 함수를 만들고 매개변수의 타입도 T로 정의합니다
> ② 반환값의 타입을 조건을 이용하여 string:undefined가 되게합니다
> ③ 조건에 따라 원하는 반환값을 원하는대로 할 수 있습니다.
> ④ T도 함수 내부에선 unknown 타입이라 as any 로 단언을 사용합니다.
> ⑤ 함수오버러드 시그니쳐를 만듭니다.

## 제네릭 타입과 조건부타입 (함수 오버러드 사용하기)

```tsx
①function removeSpaces3<T>(text: T): T extends string ? string : undefined
②function removeSpaces3(text: any){
  if (typeof text === "string") {
    return text.replaceAll(" ", "") as any;
  } else {
    return undefind;
  }
}

let result3 = removeSpaces3("hi im Psh");
result3.toUpperCase(); // unde

let result4 = removeSpaces4(undefined);
```

> ① 복사하여 함수 오버러드 시그니쳐를 생성합니다
> ② 반환값타입 , 타입단원, 지우고 매개변수를 any로 설정합니다
