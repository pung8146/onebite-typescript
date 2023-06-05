# 🥇 enum 타입

> enum타입이란 여러가지 값들에 각각 이름을 부여해 열거해두고 사용하는 타입 <br/> - 이넘을 사용하면 할당한값을 햇갈리는걸 막아줍니다.

- enum 은 컴파일 결과 사라지지 않고 객체로 변환되어 남아있습니다.

```ts
enum Role {
  ADIN = 0,
  USER = 1,
  GUEST = 2,
}

const user1 = {
  name: "박상훈",
  role: Role.ADMIN, // 0 <- 관리자
};
const user2 = {
  name: "김코딩",
  role: Role.USER, // 1 <- 일반유저
};
const user3 = {
  name: "박해커",
  role: Role.GUEST, // 2 <- 게스트
};
```

## 숫자형 enum

- 숫자를 직접 입력안해도 자동으로 0,1,2,... 가 할당됩니다
- 10으로 지정시 11,12 .. 할당됩니다. 순서는 상관없습니다.
- 숫자가 할당되는 enum을 숫자형 enum 이라고 합니다.

## 문자열 enum

```ts
enum Language {
  korean = "ko",
  english = "en",
}

const user1 = {
  name: "박상훈",
  role: Role.ADMIN, // 0 <- 관리자
  language: Language.korean,
};
const user2 = {
  name: "김코딩",
  role: Role.USER, // 1 <- 일반유저
};
const user3 = {
  name: "박해커",
  role: Role.GUEST, // 2 <- 게스트
};
```
