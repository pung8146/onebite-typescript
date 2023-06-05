# 🥇 타입 별칭 / 인덱스 시그니쳐

## 🥈 타입 별칭

```ts
type User = {
  id: number;
  name: string;
  nickname: string;
  birth: string;
  bio: string;
  location: string;
};

let user1: User = {
  id: 1,
  name: "박상훈",
  nickname: "hoon",
  birth: "11.30",
  bio: "타입스크립트",
  location: "서울",
};

let user2: User = {
  id: 2,
  name: "홍길동",
  nickname: "hong",
  birth: "01.30",
  bio: "타입스크립트",
  location: "서울",
};
```

> 타입 별칭을 사용함으로써 공통적 부분을 반복하지 않게 해줍니다.

### 🥉 함수 내 타입

```ts
function func() {
  type User = {};
}
```

> 함수내 타입이 있으면 함수내 User타입은 {}가 됩니다. 함수 밖에서는 타입 별칭으로 지정해둔 타입이 사용됩니다.

## 🥈 인덱스 시그니쳐

```ts
type CountryCodes = {
  Korea: string;
  UnitedState: string;
  Japan: string;
  // 너무많거나 추가될 경우 부적합한 코드
};

let countryCodes = {
  Korea: "ko",
  UnitedState: "us",
  Japan: "jp",
};
```

만약에 국가가 너무 많을경우,혹은 추가 해야 될경우

> 키와 밸류 의 규칙을 정의 할 수 있는 문법이 ** 인덱스 시그니쳐** 라 합니다.

## 인덱스 시그니쳐 사용

```ts
type CountryCodes = {
  [key: string]: string;
};

let countryCodes: CountryCodes = {
  Korea: "ko",
  UnitedState: "us",
  Japan: "jp",
};
```

## 인덱스 시그니쳐의 조심할점

> 규칙을 위반 하지 않으면 모든객체를 허용하는데, 빈객체일경우 오류가 나오지 않습니다.

```ts
type CountryCodes = {
  [key: string]: string;
};

let countryCodes: CountryCodes = {};
// 오류가 나오지 않습니다.
```

## 추가적인 프로퍼티를 정의할려면

> 추가적인 벨류의 타입이 인덱스 시그니쳐 벨류의 타입과 같아야 합니다

```ts
type CountryCodes = {
  // 시그니처 벨류의 타입 string
  [key: string]: string;
  // 추가 프로퍼티
  Korea: string;
};

let countryCodes: CountryCodes = {
  korea: "ko",
};
```
