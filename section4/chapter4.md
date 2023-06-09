[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 사용자 정의 타입 가드

> - 여러가지 유형으로 나뉠때는 서로소 타입을 사용하지만
> - 서로소 타입을 이용하지 않고 타입좁히기 하는방법

```tsx
type Dog = {
  name: string;
  isBark: bollean;
};

type Cat = {
  name: string;
  isScratch: boolean;
};

type Animal = Dog | Cat;

2. 가독성이 떨어지는걸 막아주기 위해 isBark 검사 함수를 만들어줍니다.
3. return animal 뒤에 as 타입을 적어줍니다. // as가 없이 쓰인다면 오류가 출력됩니다
4. 함수타입뒤에 animal is Dog 를 적어줍니다.
function isDog(animal: Animal): animal is Dog {
  return (animal as Dog).isBark !== undefined;
}


1. 가독성이 떨어지는 방식
function warning(animal: Animal) {
  if ("isBark" in animal) {
    // 강아지
  } else if ("isScratch" in nimal) {
  }
}
3. 함수를 새롭게만들고 가독성을 높인 방식
function warning(animal: Animal) {
  if (isDog(animal)) {
    // 강아지
    animal;
  } else if ("isScratch" in nimal) {
  }
}

```

> animal is Dog 라는 표현이 타입 가드를 만드는 부분이며, 이 표현이 있는 함수는 해당 타입의 확인을 진행하게 됩니다. 이 경우 isDog 함수는 인자로 받은 animal이 Dog 타입인지를 확인하는 함수입니다.

그러므로 if (isDog(animal)) 구문은 animal이 Dog 타입인지 확인하고, 만약 그렇다면 그 블록 안에서 animal을 Dog 타입으로 처리합니다. 따라서 그 블록 안에서는 animal이 가진 name과 isBark 속성에 자유롭게 접근할 수 있게 됩니다.

반면에 if ("isBark" in animal) 처럼 쓰는 경우, 이는 타입 가드의 역할을 하지 않아서 animal의 타입이 그 블록 안에서 더 구체적으로 한정되지 않습니다. 따라서 이런 방식을 사용하면 TypeScript의 타입 체크 기능을 제대로 활용하지 못하게 됩니다.

즉, animal is Dog와 같은 타입 가드를 활용하면 코드의 가독성을 높이는 동시에 타입 안정성도 강화할 수 있습니다. 이로써 TypeScript의 장점을 더욱 활용할 수 있게 됩니다.
