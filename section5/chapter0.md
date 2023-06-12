[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 인터페이스

> - 타입에 이름을 지어주는 또 다른 문법
> - 상호간의 약속된 규칙이란 뜻입니다.
> - 객체의 구조를 정의하는데 특화된 문법(상속, 합칩 등의 특수한 기능을 제공함)

```tsx
interface Person {
  name: string;
  age?: number;
  sayHi: () => void;// 함수타입표현식
  sayBye() :void; // 호출 시그니쳐
}

const person: Person {
  name:'박상훈',
  age:30,
  sayHi:function() {
    console.log('hi')
  }
}
```

## 함수에 인수를 받는 버전 / 안받는 버전

> 함수타입표현식이 아닌 ** 함수 호출 시그니쳐 ** 를 사용해야 합니다.

```tsx
 interface 인수를받고싶을때 {
  함수표현식: () => void;
  함수표현식: (a:number,b:number)
  // 함수표현식으로 사용시 오버로드할때 중복문제로 에러가 발생하게 됩니다.
  호출시그니쳐() : void;
  호출시그니쳐(a:number,b:number):void
  // 권장 되는 방법 입니다
 }
```

## 인터섹션이나 유니온이 필요할때

```tsx
interface 유니온 {
  name: string;
}:number

interface 인터섹션 {
  name: string;
} & number
// 둘다 옳바르지 않은 방식입니다

interface 옳바른방식{
  name:string
}

type Type1 = number | string | 옳바른방식;
type Type1 = number & string & 옳바른방식;

const 옳바른방식 : 옳바른방식 | number = {
  name:'박상훈'
}
```

## 헝가리안 표기법

> 대문자I를 붙여서 interface를 알려주는 방식도있지만 정답이 아닌 회사와 프로젝트 규칙에 따라가는걸 추천합니다.

```tsx
interface IPerson {
  name: string;
}
```
