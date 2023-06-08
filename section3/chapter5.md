[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 타입 추론

> - 타입스크립트는 자동으로 변수를 추론합니다. (추론 하는 기준은 변수의 초기값 입니다.) - 함수의 초기값은 return 문의 기준으로 정해집니다

### 타입을 리터럴 타입이 아닌 number,string 등 기본타입으로 추론하는것을 ** 타입 넓히기 ** 라고 합니다.

```tsx
let a = 10;
let b = "hello"; // 기본타입도
let c = {
  // 복잡한 객체도
  id: 1,
  name: "상훈",
  profile: {
    nickname: "hoon",
  },
  urls: ["https://naver.com"],
};

let { id, name, profile } = c; // 구조 분해 할당

let [one, two, three] = [1, "hello", true]; // 구조 분해 할당

function func(message = "hello") {
  return "hello";
}
```

## 애니 타입의 진화

> 직접 Any 타입을 지정하면 모든 함수 메소드를 사용 할 수 있지만, 암묵적 Any 타입은 계속 진화합니다. ** 그렇기에 별로 추천되는 방식은 아닙니다 **

```tsx
let d; // 암묵적 Any 타입으로 지정됩니다
d = 10; // 숫자로 추론합니다.
d.toFixed();

d = "hello"; // 문자로 추론됩니다
d.toUpperCase(); // 문자 메소드 사용가능
d.toFixed(); // 에러 출력
```

## const 상수 는 리터럴 타입으로 추론됩니다.

```tsx
const num = 10; // number타입이아님 리터럴 10으로 추론합니다.
const str = "hi"; // string 타입이 아닌 리터럴 'hi'로 추론됩니다.
```

## 배열의 타입을 추론 하면 어떻게 될까

> 모든 배열 요소들을 비교해서 최적의 공통 타입으로 추론해줍니다

```tsx
let arr = [1, "string"]; // 추론시 <number|string>[]
```

##
