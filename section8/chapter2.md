[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 keyof 연산자

> - ** 특정개채 타입으로 부터 프로퍼티의키들을 스트링 유니온타입으로 추출합니다. **
> - 무조건 타입에만 사용 가능합니다.

```tsx
interface Person {
  name: string;
  age: number;
}

function getPropertyKey(person: Person, key: ⑴keyof ⑵Person ) {
  return person[key];
}

const person: Person = {
  name: "박상훈",
  age: 30,
};

getPropertykey(person, "name"); // 박상훈이 출력
```

> ⑴ Person 객체 타입에 모든 프로퍼티의 키를 유니온타입으로 추출합니다.(수정 추가 될때 일일히 변경할 필요가없어집니다.)
> ⑵ keyof 뒤에 무조건 타입(대문자) 가 와야됩니다

```tsx
type Person = ⑴typeof person;

function getPropertyKey(person: Person, key: ⑴keyof ⑵Person ) {
  return person[key];
}

const person: Person = {
  name: "박상훈",
  age: 30,
};

getPropertykey(person, "name"); // 박상훈이 출력

```

> ⑴ typeof 를 사용하면 변수person 의 타입을 추론해서 타입 별칭에 정의해줍니다.

```tsx
type Person = ⑴typeof person;

function getPropertyKey(person: Person, key: keyof ⑴typeof person ) {
  return person[key];
}

const person: Person = {
  name: "박상훈",
  age: 30,
};

getPropertykey(person, "name"); // 박상훈이 출력

```

> ⑴ typeof person 은 객체 타입이 됩니다.

## opitoanl 선택지

```tsx
interface Person {
  name: string;
  age: number;
  favoriteFood?: string; // optional property
}

const person: Person = {
  name: "박상훈",
  age: 30,
};

// "name" | "age" | "favoriteFood"
type PersonKeys = keyof Person;

function printPersonProperty(key: PersonKeys) {
  console.log(person[key]);
}

printPersonProperty("name"); // "박상훈"
printPersonProperty("age"); // 30
printPersonProperty("favoriteFood"); // undefined
```

> 이 예제에서 keyof 연산자를 사용하여 Person 인터페이스의 모든 키를 PersonKeys라는 타입으로 선언했습니다. 이를 사용하여 printPersonProperty 함수를 정의하였는데, 이 함수는 Person 객체의 모든 속성값을 인쇄할 수 있습니다. 이 예제는 keyof가 어떻게 동작하는지, 그리고 TypeScript에서 이를 어떻게 활용할 수 있는지를 보여주고 있습니다.

> 또한, 이 예제는 keyof가 optional property를 포함하는지에 대해서도 보여주고 있습니다. 여기서 "favoriteFood"은 optional property입니다. 따라서 keyof 연산자는 이 optional property를 포함한 모든 키를 반환합니다.
