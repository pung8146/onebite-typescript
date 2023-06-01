# 😣 원시타입과 리터럴 타입

## (이모지)원시타입

number, string, null, boolean, undefined

### strict

- ** strict 옵션이 상위 옵션이기에 true시 strict 하위 옵션들도 true가 됩니다. **
- 예외 처리를 해줄경우 특정 옵션을 불러와서 false 해주어야합니다.

### "strictNullChecks": false,

** 엄격한 null 검사 **

```ts
let numA: number = null;
```

- true 이면 오류발생/false 일때 오류미발생

## (이모지)리터럴 타입

- ** 값이 무조건 지정된 타입 **
  ```ts
  let numA: 10 = 10;
  ```
  numA = 12는 성립이 되지 않습니다.

# (이모지)배열과 튜플

## 기본 방식

```ts
let numArr: number[] = [1, 2, 3];
let strArr: string[] = ["hello", "hi"];
```

## 제네릭 방식

```ts
let boolArr: Array<boolean> = [true, false, true];
```

# 배열에 들어가는 종류가 여러개인 경우

- tip: 마우스 위에 올리면 예시를 알려줍니다.

```ts
let multiArr: (number | string)[] = [1, "hello"];
```

# 다차원 배열의 타입을 정의하는 방법

- 대괄호[]를 늘려줍니다.

```ts
let doubleeArr: number[][] = [
  [1, 2, 3],
  [4, 5],
];
```

# 튜플타입

- ** 길이와 타입이 고정된 배열 **

```ts
let tup1: [number, number] = [1, 2];
// 길이를 추가 , 다른타입을 넣을 수 없습니다

let tup2: [number,string,boolean]: [1, "2", true];
// 길이, 타입 순서 변경불가
```

## 그러나 튜플도 결국은 JS

- tup1.push() / tup1.pop 둘 다 실행 가능

## 그럼 언제 튜플을 써야될까?

```ts
const users = [string][number][
  ["이정환", 1],
  ["거북이", 2],
  ["코끼리", 3],
  ["얼룩말", 4],
  [5, "최아무개"],
];
```

- ** 인덱스 위치 와 순서에 넣어야 하는 값이 중요할때 사용합니다! **
