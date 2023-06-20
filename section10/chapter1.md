[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 Partial<T>

> - 부분적인, 일부분의
> - 특정 객체 타입의 모든 프로퍼티를 선택적 프로퍼티 바꿔주는 타입

## 예시 1

파셜타입 사용하기

```tsx
interface Post {
  title: string;
  tags: string[];
  content: string;
  thumbnailURL?: string;
}

const draft: ①Partial<②Post> = {
  title: "제목은 나중에 짓자",
  content: "초안 1...",
};
```

> ①Partial<T>는 ** ②타입변수로 전달한 모든 프로퍼티를 선택적 프로퍼티로 전환합니다 **

## 예시2

파셜타입 직접 구현하기

```tsx
interface Post {
  ⑤title: string;
  ⑤tags: string[];
  ⑤content: string;
  ⑤thumbnailURL?: string;
}

②type Partial<③T> = {
  ④[key in keyof T]⑧? : ⑥T[⑦key];
};

const draft: ①Partial<Post> = {
  title: "제목은 나중에 짓자",
  content: "초안 1...",
};
```

> 특정 객체 타입을 새로운 객체 타입을 변경할때 맵드타입을 사용합니다
> draft에 정의된①Partial타입이 새롭게정의한 ②타입으로 변경합니다.
> ③T에 객체타입이 들어오고, 그 객체타입의 모든프로퍼티를 선택적 프로퍼티로 전환해야될때 (특정 객체 타입을 새로운 객체타입으로 변환하는 작업이 필요 => 맵드타입 작업이 필요합니다)
> ④ keyof 연산자는 특정 객체 타입으로 부터 모든 키를 유니온타입으로 추출하는 연산자
> ③에 해당되는게 <Post>타입일 경우에 -
> ④ keyof T 는 ⑤들의 유니온 타입이 됩니다.
> ④ [key in keyof T] in 을 기준으로 왼쪽의 키가 오른쪽 의 유니온타입에 하나씩 매핑됩니다.
> ⑥T[key] 벨류의 타입 정의 => 인덱스드 엑섹스 타입 => 특정객체나 배열로 부터 특정 프로퍼티의 타입을 추출하는 타입
> ⑦key 해당하는 벨류 타입을 추출 합니다.
> ①Partial<Post> 포스트가 들어간다면 ⑤의title,tags..등 대입됩니다.
> ⑧? 를 추가함으로 모든 프로퍼티가 선택적 프로퍼티가 됩니다.

# Required<T>

①②③④⑤⑥⑦⑧⑨⑩⑪⑫⑬⑭⑮

> - 필수의, 필수적인
> - 특정 객체 타입의 모든 프로퍼티를 필수 프로퍼티로 바꿔주는 타입

## 예시 1

```tsx
const withThumbanilPost: ①Required<Post> = {
  title: "한입 타스 후기",
  tags: ["ts"],
  content: "",
  thumbnailURL: "https://...",
};
```

> ① 모든 프로퍼티를 필수 프로퍼티로 바꿔줍니다.

## 예시2 직접 만들어보기

```tsx
type Required<T> = {
  [key in keyof T]①-?: T[key];
};

const withThumbanilPost: Required<Post> = {
  title: "한입 타스 후기",
  tags: ["ts"],
  content: "",
  thumbnailURL: "https://...",
};
```

> ① -? 하면 필수프로퍼티가 됩니다

# Readonly<T>

> - 읽기전용 수정불가
> - 특정 객체 타입에서 모든 프로퍼티를 읽기 전용 프로퍼티로 만들어주는 타입

```tsx
const readonlyPost: Readonly<Post> = {
  title: "보호된 게시글 입니다",
  tags: [""],
  content: "",
};
```

## 예시2 직접 만들어보기

```tsx
type Readonly<T> = {
  readonly [key in keyof T]: T[key];
};

const readonlyPost: Readonly<Post> = {
  title: "보호된 게시글 입니다",
  tags: [""],
  content: "",
};
```
