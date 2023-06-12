[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 함수 오버로딩

> - 하나의 함수를 매개변수의 개수나 타입에 따라 여러가지 버전으로 정의하는 방법
> - JS에는 지원되지 않고 TS에서만 지원됩니다.
> - 만들기전 함수의 버전들을 알려줘야 합니다.
> - 구현식 없이 선언식만 적힌걸 오버로드 시그니쳐 라고 합니다

> 1. 하나의 함수 func
> 2. 모든 매개변수의 타입 number
> 3. Ver1. 매개변수가 1개 -> 이 매개변수의 20을 곱한 값 출력
> 4. Ver2. 매개변수가 3개 -> 이 매개변수를 다 더한 값을 출력

```tsx
오버로드 시그니쳐
function func(a: number): void;
function func(a: number, b: number, c: number): void;

실제 구현부 -> 구현 시그니처
?넣어서 ver1, ver2 둘다 호환되게 작성해줘야 됩니다.
function func(a: number, b?: number, c?: number) {
  if(typeof b === 'number' && typeof c === 'number'){
    console.log(a+b+c)
  } else {
    console.log( a * 20 )
  }
}

오버로드 시그니쳐 따르지 않는 함수들은 오류가 출력됩니다.
func()//오류 출력
func(1)
func(1,2)//오류 출력
func(1,2,3)
```
