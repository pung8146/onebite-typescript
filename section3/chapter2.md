# 🥇 객체 타입의 호환성

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
