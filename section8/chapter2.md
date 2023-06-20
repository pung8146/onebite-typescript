[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 Pick<T>

> - 뽑다 고르다
> - 객체 타입으로부터 특정 프로퍼티만 딱 골라내는 타입

## 예시 1

```tsx
interface Post {
  title: string;
  tags: string[];
  content: string;
  thumbnailURL?: string;
}

const legacyPost: Pick<Post, "title" | "content"> = {
  title: "옛날 글",
  content: "옛날 컨텐츠",
};
```

## 예시2

Pick 타입 직접 구현하기

> K타입변수의 적어도 객체의 프로퍼티 키만 넣을 수 있다는 조건을 만들어줍니다

```tsx
interface Post {
  title: string;
  tags: string[];
  content: string;
  thumbnailURL?: string;
}

type Pick<①T, ⑦K ⑧exnteds keyof T> = {
  [③key in ④K]: ⑥T[key];
};

const legacyPost: Pick<②Post, ⑤"title" | "content"> = {
  title: "옛날 글",
  content: "옛날 컨텐츠",
};
```

> ①T타입에 ②Post 같은 객체 타입이 들어갑니다
> 새롭게 만들어진 객체타입 ③key는 ④K에 들어있는⑤"title" | "content" 가 됩니다
> ⑥T[key] 각각 벨류의 타입은 원본타입이 됩니다.
> in 연산자 오른쪽엔 유니온타입이 들어올 수 있습니다
> 타입변수 ⑦K(모든타입이 들어올수있어 문제가 발생할 수 있습니다)
> ⑧exnteds keyof T 로 제한해줍니다.
> ⑧exnteds keyof T ②Post를 전달해버리면
> K extneds 'title' | 'tags' | 'content' | 'thumbnailURL' === keyof T 치환됩니다
> 타입변수 ⑦K에 ⑤"title" | "content" 할당되면
> 'title' | 'content' extneds 'title' | 'tags' | 'content' | 'thumbnailURL' 가 최종적으로 되고 참이 됩니다.

# Omit<T , K> 타입

> - 생략하다,빼다
> - 객체 타입으로 특종 프로퍼티를 제거 하는 작업

```tsx
const noTiltePost: Omit<Post, "title"> = {
  cotent: "",
  tags: [[]],
  thumbnailURL: "",
};
```

## Omit 예시 직접구현하기

```tsx
type Omit<①T, ②K extends keyof T> = ③Pick<T, Exclude<keyof T, K>>;

const noTiltePost: Omit<Post, "title"> = {
  cotent: "",
  tags: [[]],
  thumbnailURL: "",
};
```

진행과정

> ①T=Post타입이 들어오며 ②K = 'title' 이들어옵니다
> ③Pick<Post, Exclude<keyof Post, 'title'>> 로 변형됩니다
> ③Pick<Post, Exclude<'title'| 'content'|'tags'|'thumbnailURL' , 'title'>> 로 변형됩니다
> ③Pick<Post, Exclude< 'content'|'tags'|'thumbnailURL' > 로 변형됩니다

# Record<K , V> 타입

> ** 객체 타입을 만들어주는 유틸리티 타입 **
> 객체타입을 새롭게 정의할때 인덱스 시그니쳐 처럼 유연하지만 좀더 제한적인 객체 타입을 정의할때 사용합니다 (사용빈도 높음)
> 중복된 코드가 많을때 사용됩니다

```tsx
type ThumbnailLegacy = {
  large: {
    url: string;
  };
  medium: {
    url: string;
  };
  small: {
    url: string;
  };
  wathc: {
    url: string;
  };
};

type Thumbnail = Record①<"large" | "medium" | "small", ②{ url: string, ③size:number }>;
```

> 첫번째 ①타입변수로 <"large" | "medium" | "small" 객체의 프로퍼티키를 유니온으로 받습니다.
> 두번째 타입변수로 ②{ url: string } 키들의 벨류타입을 받습니다.
> 버전별로 새로운 프로퍼티가 추가되어야할때 ③,size:number 등 추가적으로 적어줍니다.

## Record 예시 직접구현하기

```tsx
type Record<①K extends keyof any, V> = {
  [key in K]: V;
};

type Thumbnail = Record<
  "large" | "medium" | "small" | "watch",
  { url: string; size: number }
>;
```

> 적어도 타입변수①K 에 들어오는 타입은 어떤객체타입의 키를 추출해논 유니온 타입입니다
