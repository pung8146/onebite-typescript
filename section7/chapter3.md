[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 제네릭 인터페이스와 제네릭타입별칭

## 제네릭 인터페이스

> ** 제네릭 인터페이스는 타입으로 변수를 정의할때(타입으로 사용할때) 꺽쇠를 열고 타입을 직접 할당해줘야합니다 **

```tsx
// <K,V> 를 타입변수,타입파라미터,제네릭 타입변수,제네릭 타입 파라미터 로 부릅니다
interface KeyPair<K, V> {
  key: K;
  value: V;
}
// 제네릭 인터페이스는 타입으로 변수를 정의할때 꺽쇠를 열고 타입을 직접 할당해줘야합니다
let keyPair: KeyPair<string, number> = {
  key: "key",
  value: 0,
};

let keyPair2: KeyPair<boolean, string[]> = {
  key: "key",
  value: 0,
};
```

## 인덱스 시그니쳐

> 프로퍼티에 키와 벨류에 타입에 관련된 규칙만 만족하면 어떤 객체든 허용하는 유연한 객체타입을 허용하는 ** 인덱스 시그니쳐**

```tsx
interface NumberMap {
  [key: string]: number;
}

let numberMap1: NumberMap = {
  key: -123,
  key2: 12312,
};

interface Map<V> {
  [key: string]: V;
}

let string Map: Map<string> = {
    key : 'value',
}

let booleanMap : Map<boolean> = {
    key:true
}
```

## 제네릭 타입 별칭

> 제네릭인터페이스랑 문법만 다를뿐 거의 비슷한 형식입니다.

```tsx
type Map2<V> = {
  [key: string]: V;
};

let stringMap2: Map2<string> = {
  key: "hello",
};
```

## 제네릭 인터페이스의 활용예시

** 예시: 유저관리프로그램 **

- 학생유저 / 개발자 유저

```tsx
// interface Student와 Developer 서로소 유니온타입으로 묶을수도있습니다
interface Student {
  type: "student";
  school: string;
}

interface Developer {
  type: "developer";
  skill: string;
}

interface User<T> {
  name: string;
  profile: T;
}

function goToSchool(user: User<Student>) {
  if (user.profile.type !== "student") {
    console.log("잘 못 오셨습니다");
    return;
  }
  user.profile;

  const school = user.profile.school;
  console.log(`${school}로 등교완료`);
}

const developerUser: User<Developer> = {
  name: "이정환",
  profile: {
    type: "developer",
    skill: "TypeScript",
  },
};

const studentUser: User<Student> = {
  name: "홍길동",
  profile: {
    type: "student",
    school: "가톨릭대학교",
  },
};
```
