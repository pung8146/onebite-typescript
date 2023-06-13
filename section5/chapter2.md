[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 선언 합침

> 인터페이스는 동일한 이름으로 중복선언해도 문제 없습니다.
> 결국 합쳐지기 때문에 문제가 되지 않습니다.

```tsx
interface 선언합침 {
  프로퍼티1: string;
}

interface 선언합침 {
  프로퍼티2: number;
}

const 선언합침: 선언합침 = {
  프로퍼티1: "",
  프로퍼티2: 0,
};
```

## 충돌

> 타입을 같게 선언한다면 문제가 되지 않습니다.
> 타입을 다르게 정의하는 경우를 ** 충돌 ** 문제가 발생합니다

```tsx
interface 선언합침 {
  프로퍼티1: string;
}

interface 선언합침 {
  프로퍼티1 : number; 다른타입을 정의시 에러가 발생합니다
  프로퍼티2: number;
}

const 선언합침: 선언합침 = {
  프로퍼티1: "",
  프로퍼티2: 0,
};
```

## 확장과 선언합침의 차이점

> ** 확장은 다시 정의되는 타입이 서브타입 ** 이기만하면 에러가 나오지 않습니다
> ** 선언합침은 서브타입 ** 여도 에러가 발생합니다
> ** 반드시 동일한 타입이어야합니다 **
> 간단한 프로젝트보다 모듈보강작업할때 사용됩니다.

```tsx
interface 선언합침 {
  프로퍼티1: string;
}

interface 선언합침 {
  프로퍼티1: 'hello'; 서브타입이여도 에러가 발생합니다.
  프로퍼티2: number;
}

interface 확장 extneds 선언합침 {
  프로퍼티1: 'hello';
}

const 선언합침: 선언합침 = {
  프로퍼티1: "",
  프로퍼티2: 0,
};
```

### 모듈보강

```tsx
interface LIb {
  a: number;
  b: number;
}

interface Lib {
  c:string
}
const lib: LIb = {
  a: 1,
  b: 2,
  c: 'hello'
  c를 추가하고싶다면
};

```
