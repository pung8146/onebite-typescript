# 함수타입의 호환성

> 특정 함수 타입을 다른 함수 타입으로 취급해도 괜찮은가를 판단합니다.

1. 반환값의 타입이 호환되는가?
2. 매개변수의 타입이 호환되는지?
   두개가 성립할경우 호환된다라고 할 수 있습니다

## 1. 반환값이 호환되는가?

> 어떤 매개변수를 받고, 어떤 결과값을 반환하는지 이야기
> ** 반환 값을 기준으로 업캐스팅 다운캐스팅 정해집니다 **

```jsx
type A = () => number;
type B = () => 10;

let a: A = () => 10;
let B: A = () => 10;

a = b 허용이 됩니다. // 업캐스팅이라 허용됩니다
b = a 오류가 발생합니다. // 다운캐스팅
```

## 2. 매개 변수가 호환되는가

### 2.1 매개변수의 개수가 같을 때

```tsx
type C = (value: number) => void;
type D = (value: 10) => void;

let c: C = (value) => {};
let d: D = (value) => {};

c = d; // 오류가 발생 합니다 / 업캐스팅이지만 '매개변수'기준으로 오류가 발생합니다.
d = c; // 다운캐스팅 이지만 매개변수 기준이라 가능합니다.
```

#### 매개변수가 객체 타입일때

```tsx
type Animal = {
  name: string;
};

type Dog = {
  name: string;
  color: string;
};

let animalFunc = (animal: Animal) => {
  console.log(animal.name);
};
let dogFunc = (dog: Dog) => {
  console.log(dog.name);
  console.log(dog.color);
};
```

#### 업 캐스팅이 안되는이유

```tsx
animalFunc = dogFunc; // 오류가 발생합니다 // 업 캐스팅 상황 이지만

let tsetFunc = (animal: Animal) => { 업캐스팅 코드를 풀어쓴 코드입니다.
  console.log(animal.name);
  console.log(animal.color); // 업 캐스팅 일때 안되는 이유
}
```

#### 다운 캐스팅이 동작 하는 이유

```tsx
dogFunc = animalFunc ;   다운 캐스팅 상황입니다

let tsetFunc2 = (dog: Dog) => { 다운 캐스팅 코드를 풀어쓴 코드입니다.
  console.log(dog.name);
}
```

### 2.2 매개변수의 개수가 다를 때

> 할당 할려고 하는 함수의 타입의 매개변수의 갯수가 더 적을때 호환이 됩니다.
> 적어도 매개변수의 타입이 같은 타입어야 합니다.

```tsx
type Func1 = (a: number, b: number) => void;
type Func2 = (a: number) => void;

let func1: Func1 = (a, b) => {};
let func2: Func2 = (a) => {};

func1 = func2; 허용이 됩니다
func2 = func1; 오류가 발생합니다
```
