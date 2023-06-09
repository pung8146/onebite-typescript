[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 타입좁히기

> 조건문 등을 이용해 넓은 타입에서 좁은 타입으로 타입을 상황에 따라 좁히는 방법
> 어떤 변수가 특정 조건 내에서 좁은 타입임을 보장할 수 있음 때에는 더 좁은타임으로 추론해줍니다.

```tsx
// value 타입에 따라 메소드 다르게 적용시키기
// value => number : toFixed()
// value => string : toUpperCase()
function func(value: number | string) {
  value;
  value.toUpperCase(); 오류가 출력됩니다.
  value.toFixed();// 오류가 출력됩니다.

  if (typeof value === "number") { // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toFixed()); // 넘버타입으로 추론
  } else if (typeof value === "string") { // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toUpperCase()); // 스트링 타입으로 추론
  }
}
```

## 타입 가드1

> 특정한 조건내에서 타입을 한정 짓게 해줍니다

```tsx
// value => Date : getTime
function func(value: number | string | Date | null) {
  if (typeof value === "number") {
    // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toFixed()); // 넘버타입으로 추론
  } else if (typeof value === "string") {
    // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toUpperCase()); // 스트링 타입으로 추론
  } else if (typeof value === "object") {
    console.log(value.getTime()); // null 을 추가할 경우 오류가 나옵니다
  }
}
```

## 타입가드2

> typeof 가 아닌 instanceof 를 사용합니다.

```tsx
// value => Date : getTime
// value => Person : name 은 age살입니다
function func(value: number | string | Date | null | Person) {
  if (typeof value === "number") {
    // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toFixed()); // 넘버타입으로 추론
  } else if (typeof value === "string") {
    // 타입가드 (타입을 한정짓게해줌)
    console.log(value.toUpperCase()); // 스트링 타입으로 추론
  } else if (value instanceof Date) {
    console.log(value.getTime()); // tpyeof 를 사용했을때 null타입 을 추가할 경우 오류가 나옵니다
    // } else if (value instanceof Person) { typeof Person 을 사용할 경우 오류가 출력됩니다
  } else if (value && "age" in value) {
    // in연산자 뒤에는 null,undefined가 들어오면안됩니다
    // 해결 하기 위해 value &&  를 앞에 붙여주고 value가 null 아님 알려줍니다
    console.log(`${value.name}은 ${value.age}살입니다`);
  }
}
```
