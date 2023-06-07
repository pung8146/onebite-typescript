# 🥇 타입계층도

# 🥇 Unknown 타입(전체 집합)

> 타입 계층도 최상단의 위치하고 있는 Unknown 타입 (전체 집합)

```tsx
function unknwonExma() {
  let a: unKnown = 1;
  let b: unKnown = true;
  let c: unKnown = null;
  /// ... 모든 값을 넣을 수 있습니다.
  //  업캐스팅
  let unknownVar: unknown;

  let num: number = unknownVar;
  let str: string = unknownVar;
  // 모든 값을 넣을 수 없습니다.
  // 다운 캐스팅
}
```

# 🥇 Never 타입(공집합)

```tsx
function neverExam() {
  function neverFunc(): never {
    while (true) {}
  }

  let num: number = neverFunc();
  let str: string = neverFunc();
  // never 타입은 모든 타입의 sub 타입이기때문에 그 어떤 타입 변수에도 넣을수있습니다
  // 업캐스팅
}
```

# 🥇 Void 타입

```tsx
function voidExam() {
  function voidFunc(): void {
    console.log("hi");
    return undefined;
  }

  let voidVar: void = undefined;
}
```

# 🥇 Any 타입

> 모든 타입의 다운캐스팅 업캐스팅 가능합니다 (단! never 타입을 제외하고)

```tsx
function anyExam() {
  let unknownVar: unknown;
  let anyVar: any;
  let undefinedVar: undefined;
  let neverVar: never;
  anyVar = unknownVar;
  //  다운 캐스팅 해도 문제가 없습니다.
  undefinedVar = anyVar;
  //  다운 캐스팅 해도 문제가 없습니다.
  neverVar = anyVar;
  // 네버 타입에는 그 어떤 타입도 다운 캐스팅 할 수 없습니다.
}
```

# 🥈 타입 호환성
