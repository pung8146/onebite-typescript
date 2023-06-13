[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 제네릭

> 제네릭 뜻 : ** 일반적/포괄적인 **
> Any 가 안되는이유 : 반한 값이 무조건 Any 로 나와 모든 함수메소드를 사용가능합니다.
> unknown 가 안되는이유 : 반한 값이 무조건 unknown 로 나와 모든 함수메소드를 사용 불가합니다.

```tsx
적절치 않은 함수예시들
function func1(value: unknwon) {
  return value;
}

function func2(value: any) {
  return value;
}
```

## 제네릭 함수

> - ** 인수로 특정타입을 넣으면 반환값으로 특정타입을 인출하고싶을때 **
> - 함수에 인수에 따라서 가변적으로 정의해줄 수 있습니다.
> - ** 모든 타입에 두루 두루 사용할 수 있는 범용 함수 **
> - **<T> 타입변수라고 합니다 **
> - 함수변수에 어떤 타입이 담기는지는 우리가 ** 함수를 호출할때 정의됩니다 **

```tsx
function func<T>(value: T): T {
  return value;
}

let num = func(10);
num.toFixed();

let bool = func(true);
```

## 넘버 배열 타입

```tsx
function func<T>(value: T): T {
  return value;
}
let arr = func([1, 2, 3]);
```

### 튜플타입으로 출력하고싶을때

```tsx
function func<T>(value: T): T {
  return value;
}
let arr1 = func<[number, number, number]>([1, 2, 3]);
let arr2 = func([1, 2, 3] as [number, number, number]);
```
