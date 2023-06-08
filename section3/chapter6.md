[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 타입 단원 (assertion)

```tsx
type Person = {
  name: string;
  age: number;
};

let person: Person = {}; // 오류가 출력됩니다
let person = {} as Person; // as 키워드 뒤에 원하는 타입을 단원합니다
person.name = "이정환";
person.age = 27;
```

## 추가 프로퍼티에서 타입 단원

```tsx
type Dog = {
  name: string;
  color: string;
};

let dog: Dog = {
  name: "쪼코",
  color: "brwon",
  breed: "포메", // 추가 프로포티 검사로 인해 허용되지 않아 오류가 나옵니다.
};

let dog = {
  name: "쪼코",
  color: "brwon",
  breed: "포메", // 추가 프로포티 검사로 인해 허용되지 않아 오류가 나옵니다.
} as Dog;
```

## 타입 단원의 규칙

> - 값 as 단언 <- 단언식

- A as B
- A가 B 의 슈퍼타입이거나
- A가 B 의 서브타입이어야 함

```tsx
let num1 = 10 as never;
let num2 = 10 as unknown;

let num3 = 10 as string; // 겹치는 부분이 없기에 오류가 출력됩니다.
```

### 다중 단언

> 언노운을 중간으로 걸쳐서 사용할 수 있게 하지만 사용하는것은 별로 선호되지 않습니다.

```tsx
let num3 = 10 as unknown as string;
```

## const 단원

> 변수를 선언한것을 const 로 선언한것으로 바꿔줍니다. 보통 ** 객체 타입 ** 에서 사용됩니다.

```tsx
let num4 = 10 as const;

let cat = {
  name: "야옹이",
  color: "yellow",
} as const; // 모든 프로퍼티가 readonly가 되어버립니다.

cat.name = ""; // 변경 할 수 없는 프로퍼티가 됩니다
```

## Non Null 단언

### 옵셔널 체이닝

> - 값뒤에 물음표가 뒤에 저절로 붙음

- 널이나 언디파인일 경우에 .(점표기법)을 오류가 발생하니까
- ? 붙여주고 그 값이 없다면 undefind로 바꿔줍니다

```tsx
type Post = {
  title: string;
  author?: string;
};

let post: Post = {
  title: "게시글1",
  author: "박상훈",
};

const len: number = post.author?.length; // 이럴경우 number타입에 undefined가 들어갈수있어 오류가 나옵니다
const len: number = post.author!.length; // 느낌표 연산자는 이값이 무조건 있다고 알려줍니다.
```
