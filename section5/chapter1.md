[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 인터페이스의 확장

> 익스텐즈를 이용해서 다른 인터페이스로부터 해당인터페이스 모든프로퍼티를 자동으로 다포함하게 해주는문법 확장(속성) 이라고 합니다.

```tsx
interface Animal {
  name: string;
  color: number;
}

interface Dog {
  isBark: boolean;
  name: string;
  color: number;
}

interface Cat {
  name: string;
  color: number;
  isScratch: boolean;
}

interface Chicken {
  name: string;
  color: number;
  isFly: boolean;
}
```

## 중복된 코드를 없앨려면

> inter face 도그는 interface Animal 을 확장하는 타입이다

```tsx
interface Animal {
  name: string;
  color: number;
}

interface Dog extends Animal {
  isBark: boolean;
}

const dog: Dog = {
  name: "",
  color: "",
  isBark: true,
};

interface Cat extends Animal {
  isScratch: boolean;
}

interface Chicken extends Aniaml {
  isFly: boolean;
}
```

## 상속을 받는 인터페이스에서 동일한 동일한 프로퍼티를 다시 정의할수있습니다.

> - 동일한프로퍼티는 새롭게 정의된 타입으로 정해집니다
> - 동일한프로퍼티를 재정의할때는 ** 원본 타입의 서브타입** 이어야 합니다.

```tsx
interface Animal {
  동일한프로퍼티: string;
  color: number;
}

interface Dog extends Animal {
  동일한프로퍼티: "리터럴 타입으로 새롭게 정의";
  isBark: boolean;
}

const dog: Dog = {
  동일한프로퍼티: "", //빈문자열은 오류가 출력됩니다
  color: "",
  isBark: true,
};
```

## 다중확장

> 다중 확장은 모든프로퍼티를 가지고 있습니다.

```tsx
interface Animal {
  name: string;
  color: number;
}

interface Dog extends Animal {
  isBark: boolean;
}

const dog: Dog = {
  name: "",
  color: "",
  isBark: true,
};

interface DogCat extends Dog, Cat {}

const dogcat: DogCat = {
  name: "",
  color: "",
  isBark: true,
  isScratch: true;
}

```
