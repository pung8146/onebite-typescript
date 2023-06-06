# 🥇 Any 타입 과 Unknown 타입

> 특정 변수의 타입을 우리가 확실히 모를 때

## 어떠한 값이 들어갈 수 있습니다.(할당 받을 수 있습니다.)

```ts
let anyVar: any = 10;
anyVar = "hello";

anyVar = true;
anyVar = {};
anyVar = () => {};
```

## 어떠한 메소드든 사용가능합니다.

```ts
anyVar.toUpperCase();
anyVar.toFixed();
```

## 이미 정해진 타입이여도 anyVar 가 사용가능합니다.

```ts
let num: number = 10;
num = anyVar;
```

## 애니 타입은 런타입 에러가 잃어 날 수 있습니다.

> 그렇기에 최대한 any타입을 사용하지 말아야 합니다

# unknown

> 아무 타입의 값이나 넣을수 있습니다 그러나 ** 메소드를 넣을수도 없고 , 다른 타입에 집어넣을수 없습니다 **

## 값은 아무거나 넣을수 있습니다

```ts
let nuKnownVar: unknown;
unknownVar = "";
unKnownVar = 1;
```

## 메소드를 넣을 수는 없습니다.

```ts
unKnownVar.toUpperCase();
```

> 오류 메시지가 출력됩니다.

## 언노운 타입은 다른 타입에 집어넣을수 없습니다.

```ts
num = unKnownVar;
```

> 오류메시기자 출력됩니다.

## 언노운 타입을 활용하고싶다면 '타입정제'를 사용해야 합니다.

```ts
if (typeof unKnownVar === "number") {
  num = unKnownVar;
}
```
