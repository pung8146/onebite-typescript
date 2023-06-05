# 객체 타입

## 타입 어떻게 적어야될까?

#### 잘못된 예시 1

```ts
let user: object = {
  id: 1,
  name: "상훈",
};
user.id; // 오류가 출력되게 됩니다.
```

오류가 출력 되는 이유는 object(객체) 라는 것만 주어지고
안에 어떠한 타입들이 있는지 정보를 모르기 때문에 발생하는 오류입니다.

#### 옳바른 예시 1

```ts
// 예시 1
let user: {
  id: number;
  name: string;
} = {
  id: 1,
  name: "상훈",
};
```

프로퍼티의 타입들까지 정의 해줍니다.
{} 를 이용한 방식을 객체 리터럴 타입 이라고 합니다.

```ts
let dog: {
  // 예시 2번
  name: string;
  color: string;
} = {
  name: "하트",
  color: "brown",
};
```

## 구조적 타입 예시

> 타입스크립트는 구조 기준으로 정의되며 ** 구조적 타입 예시 ** 라고 합니다. -> Property Based TS

## 명목적 타입 시스템

> 구조적 타입 시스템에 반대로 ** 명목적 타입 시스템** 이 있습니다.

## 선택적 타입

```ts
let user: {
  id?: number;
  name: string;
} = {
  name: "상훈",
};
```

> 타입뒤에?를 붙임으로써 프로퍼티가 있어도 되고 없어도 됩니다. (OptionalProperty)

## 값이 바뀌지 않아야 할 경우

```ts
let config: {
  readonly apiKey: string;
} = {
  apiKey: "MY API KEY",
};
config.apiKey = "hacked";
```

> 절대 수정 되지 않아야 될게 있다면 ** readonly ** 를 앞에 적어줍니다.
