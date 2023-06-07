# 🥇 void타입

> 아무것도 없음을 의미 하는 타입

## 🥈 타입스크립트는 함수의 반환 값에도 타입을 지정해줄수있습니다.

> 방법은 함수() 매개변수 뒤에 타입을 지정해줍니다.

```ts
function func1(): string {
  return "hello";
}

function func2(): void {
  return "hello";
}
```

## 🥈 변수에도 타입을 void타입을 지정해줄수없습니다.

> - 어떤 값도 넣을수 없지만 ** undefined ** 만은 지정해 줄수 있습니다.

- tscofing.json 에서 strictNullChecks 를 끄면 null 을 집어넣어줄수 있습니다.

## 🥈 타입으로 undefined / null 을 사용하지 않고 void를 쓰는이유

> void 를 사용 하지 않으면 무조건 undefined / null 타입에 맞게 리턴값도 동일 해야합니다.

# never 타입

> - 존재 하지 않는 불가능한 타입

- 이 함수에 반환값이 있는게 모순이다 할때 사용합니다.

```ts
function func3(): never {
  while (true) {}
}

function func4(): never {
  throw new Error();
}
```

## 🥈 변수에 타입을 지정해줄수없음

- void 타입 과 다른점으로 undefined/null/(any타입의 값) 값들을 어떻게해도 담을 수 없습니다.
