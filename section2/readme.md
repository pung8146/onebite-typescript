# 🎂 원시타입과 리터럴 타입

## 🔨 원시타입

- number: 숫자를 나타내는 타입
- string: 문자열을 나타내는 타입
- null: 값이 없음을 나타내는 타입
- boolean: 참 또는 거짓을 나타내는 타입
- undefined: 값이 할당되지 않은 상태를 나타내는 타입

### strict

- strict 옵션이 상위 옵션이기 때문에 true로 설정하면 strict 하위 옵션들도 true가 됩니다.
- 특정 옵션을 예외로 처리하려면 해당 옵션을 개별적으로 false로 설정해야 합니다.

### "strictNullChecks": false

- 엄격한 null 검사를 비활성화하는 옵션입니다.
- true일 때는 오류 발생, false일 때는 오류 미발생

## 🌳 리터럴 타입

- 값이 무조건 지정된 타입을 나타냅니다.
- let numA: 10 = 10;과 같이 변수의 타입을 10으로 지정하면, numA에 다른 값인 12를 할당할 수 없습니다.

# 🌳 배열과 튜플

## 기본 배열

```ts
let numArr: number[] = [1, 2, 3];
let strArr: string[] = ["hello", "hi"];
```

## 제네릭 배열

```ts
let boolArr: Array<boolean> = [true, false, true];
```

# 🔮 배열에 다양한 타입이 있는 경우

- (number | string)[]와 같이 유니온 타입을 사용하여 여러 타입의 요소를 가진 배열을 정의할 수 있습니다.

```ts
let multiArr: (number | string)[] = [1, "hello"];
```

# 🤖 다차원 배열의 타입 정의

- 대괄호를 중첩하여 다차원 배열을 정의할 수 있습니다.

```ts
let doubleArr: number[][] = [
  [1, 2, 3],
  [4, 5],
];
```

# 👾 튜플 타입

- 길이와 타입이 고정된 배열을 나타냅니다.

```ts
let tup1: [number, number] = [1, 2];
// 길이와 타입이 고정된 튜플

let tup2: [number, string, boolean] = [1, "2", true];
// 길이와 타입이 고정된 튜플

// 튜플은 JavaScript의 배열 메서드(push, pop 등)를 사용할 수 있습니다.
tup1.push(3);
tup1.pop();
```

## 튜플 사용 시 주의점

- 튜플도 결국 JavaScript의 배열로 취급되기 때문에 push()와 pop() 등의 배열 메서드를 사용할 수 있습니다

.

- 하지만 튜플은 길이와 타입이 고정되어 있으므로 push()로 요소를 추가하거나 pop()으로 요소를 제거하는 것은 튜플의 타입 안정성을 해치는 행동입니다.
