[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 타입변수 응용하기

## 첫번째 사례

> - 타입변수의 종류가 여러개일때

```tsx
fucntion swap<T, U>(a:T,b:U){
  return [b,a]
}

const [a,b] = swap("1",2)
```

## 두번째 사례

> - 타입변수의 종류가 객체 배열일때
> - T[],T{} 를 써줘야 unknown배열 , unknown객체 라고 인식합니다

```tsx
fucntion returnFirstValue<T>(T[]){
  return [b,a]
}

let num= returnFirstValue([0,1,2])
// 0 :number 추론
let str1 = returnFirstValue(["hi","bye"])
// hi : string 추론
let str2 = returnFirstValue([1,"hi","bye"])
// 1 : <number|string> 추론
```

### 인덱스 첫번째 값 만 타입추론이 하고싶을경우

> - 튜플을 만들고 첫번째요소 T로만들고 나머지는 unknown으로 취급합가.

```tsx
fucntion returnFirstValue<T>(data:[T,...unknown[]]){
  return [b,a]
}

let num= returnFirstValue([0,1,2])
// 0 :number 추론
let str1 = returnFirstValue (["hi","bye"])
// hi : string 추론
let str2 = returnFirstValue([1,"hi","bye"])
// 1 : number 추론
```

## 세번째 사례

> - T의 타입을 제한하는 방식
> - number타입의 프로퍼티 length를 가지고있는 객체를 확장하고있는 타입
> - 즉 length 프로퍼티 를 가지고만 있어야 합니다
> - extends 이용해서 타입변수의 조건을 달아서 제한할 수 있습니다.

```tsx
function getLength<T extends { length: number }>(data: T) {
  return data.length;
}

let var1 = getLength([1, 2, 3]);
// 3
let var2 = getLength("12345");
// 5
let var3 = getLength({ length: 10 });
// 10
let var4 = getLength(10);
// length프로퍼티가 없기에 오류가 출력됩니다.
```
