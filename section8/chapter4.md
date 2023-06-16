[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇템플릿 리터럴타입

> - 스트링 리터럴 타입 기반으로 특정 패턴을 갖는 문자열 타입들을 만드는 기능입니다.
> - 문자열로 여러 상황들을 만들때 사용합니다

```tsx
type Color = "red" | "black" | "green";
type Animal = "dog" | "cat" | "chicken";
type ColorAnimal = `${Color}-${Animal}`;
```
