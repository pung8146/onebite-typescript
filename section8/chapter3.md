[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇맵드 타임

> 맵드타입은 인터페이스에서 사용할 수 없습니다

## 선택적으로 프로터피를 수정하고싶을때

```tsx
interface User {
  id: number;
  name: string;
  age: number;
}
⑴interface PartialUser {
  id?: number;
  name?: string;
  age?: number;
}
// 한명의 유저 정보를 불러오는 기능
function fetchUser(): User {
  // ... 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

// 한명의 유저 정보를 수정하는 기능
function updateUser(user: ⑴PartialUser) {
  // ... 수정하는기능 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

updateUser({
  //   id: 1,
  //   name: "박상훈",
  age: 27,
});
```

> ⑴ updateUser 를 실행시키기위해 ⑴ 새로운 타입을 만들고 옵셔널 프로퍼티들로 수정하였음 (그러나 중복이 생김)

## 맵드 타입 사용

```tsx
interface User {
  id: number;
  name: string;
  age: number;
}
type PartialUser = {
    ⑴[key in 'id'|'name'|'age'|]⑷?:⑵User[⑶key]
}
// 한명의 유저 정보를 불러오는 기능
function fetchUser(): User {
  // ... 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

// 한명의 유저 정보를 수정하는 기능
function updateUser(user: PartialUser) {
  // ... 수정하는기능 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

updateUser({
  //   id: 1,
  //   name: "박상훈",
  age: 27,
});
```

> ⑴ [] 인덱스 시그니쳐와 마찬가지로 key 무엇이 될수있는지 정의합니다,
> ⑴ in과 union 타입이 사용됩니다. key 값이 id,name,age 가 될수도 있다는걸 알려줍니다.
> ⑵ value 가 무엇이 될지 정의합니다
> ⑶ key 한번은 id,name,age가 됩니다 => id:user['id'] = number타입 ... 이런식으로 객체타입으로 설정됩니다
> ⑷ ?붙임으로써 모든프로퍼티가 선택적 프로퍼티가 됩니다.

## 맵드 타입 사용 2

> - keyof 사용하기
> - readOnly로 설정하기

```tsx
interface User {
  id: number;
  name: string;
  age: number;
}
type PartialUser = {
    [key in 'id'|'name'|'age'|]?:User[key]
}

type BooleanUser = {
    [key in ⑴keyof User]: boolean
}

⑵type ReadonlyUser = {
    readonly [key in keyof User]: User[key]
}

// 한명의 유저 정보를 불러오는 기능
function fetchUser(): ⑵ReadonlyUser {
  // ... 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

// 한명의 유저 정보를 수정하는 기능
function updateUser(user: PartialUser) {
  // ... 수정하는기능 기능
  return {
    id: 1,
    name: "박상훈",
    age: 30,
  };
}

updateUser({
  //   id: 1,
  //   name: "박상훈",
  age: 27,
});
```

> ⑴ 맵드타입에 keyof타입을 사용할 수 있습니다.
> ⑵ Readonly 타입을 설정하고 fetchUser(): 뒤에 타입을 지정해줍니다.
