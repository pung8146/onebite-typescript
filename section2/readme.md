# 😣 원시타입과 리터럴 타입

## (이모지)원시타입

number, string, null, boolean, undefined

### strict

- ** strict 옵션이 상위 옵션이기에 true시 strict 하위 옵션들도 true가 됩니다. **
- 예외 처리를 해줄경우 특정 옵션을 불러와서 false 해주어야합니다.

### "strictNullChecks": false,

** 엄격한 null 검사 **
let numA: number = null;

- true 이면 오류발생/false 일때 오류미발생

## (이모지)리터럴 타입

- ** 값이 무조건 지정된 타입 **
  let numA: 10 = 10;
  numA = 12는 성립이 되지 않습니다.

# (이모지)배열과 튜플
