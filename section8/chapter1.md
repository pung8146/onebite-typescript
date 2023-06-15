[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇인덱스드 엑세스 타입

> 인덱스란걸 이용해서 다른 타입내에서 특정 프로퍼티 타입을 추출
> 객체,배열,튜플 모두에서 사용가능합니다.

## 객체 예시

> 객체타입으로부터 특정 프로퍼티에 타입을 쏙 뽑아서 변수에 정의해줄수있습니다.

```tsx
// 커뮤니티 게시글 상황
interface Post {
  title: string;
  content: string;
  author: {
    id: number;
    name: string;
    ⑵location:string;
  };
}

function printAuthorInfo(⑴author: Post["⑶author"]) {
  console.log(`${author.name}-${author.id}`);
}

const post: Post = {
  title: "게시글 제목",
  content: "게시글 본문",
  author: {
    id: 1,
    name: "박상훈",
  },
};

printAuthorInfo(post.author);
```

> ⑴ Post 타입의 특정 프로퍼티만 가져올수있습니다.
> ⑵ 새로운 프로퍼티 추가 되거나, 기존프로퍼티가 변경됬을때에도 추가적인 수정이 필요가 없습니다
> ⑶ ** 인덱스 ** 를 이용해서 특정 타입에 접근한다해서 인덱스드 엑세스 타입이라고 불립니다.
> ⑶ 주의할점으로 값이 아니라 타입입니다.
> ⑷ 특정 프로퍼티만 가져오는 방법으로 Post["author"]["id"] 처럼 []연속 사용합니다.

## 배열 타입

```tsx
// 커뮤니티 게시글 상황
type PostList =  {
  title: string;
  content: string;
  author: {
    id: number;
    name: string;
    location:string;
  };
}[],

function printAuthorInfo(author: PostList⑶[number]["author"]) {
  console.log(`${author.name}-${author.id}`);
}

⑵const num = 0

const post: PostList⑴[number] = {
  title: "게시글 제목",
  content: "게시글 본문",
  author: {
    id: 1,
    name: "박상훈",
  },
};

printAuthorInfo(post.author);
```

> ⑴ 배열타입에서 하나의 요소의 타입만 가져오는 방법입니다.
> ⑴ [number] === [0] 숫자를 넣어도 똑같이 가져옵니다.
> ⑵ 값이 아니라 타입을 넣어야하기 때문에 ⑴에서 변수를 넣으면 오류가 발생합니다.
> ⑶ 요소의 타입을 먼저 가져오고 author 타입을 가져오는 방식입니다

## 튜플 타입

```tsx
// 커뮤니티 게시글 상황
type PostList =  {
  title: string;
  content: string;
  author: {
    id: number;
    name: string;
    location:string;
  };
}[],

function printAuthorInfo(author: PostList[number]["author"]) {
  console.log(`${author.name}-${author.id}`);
}

const num = 0

const post: PostList[number] = {
  title: "게시글 제목",
  content: "게시글 본문",
  author: {
    id: 1,
    name: "박상훈",
  },
};

printAuthorInfo(post.author);

type Tup = [number, string, boolean];

type Tup0 = Tup[0]; // 튜플에 number 가져옵니다
type Tup1 = Tup[1]; // 튜플에 string 가져옵니다
type Tup2 = Tup[2]; // 튜플에 boolean 가져옵니다
type Tup3 = Tup[3]; // 길이에 넘는 튜플을 가져오면 오류가 납니다
type TupNum = Tup[number] // 튜플 타입 최적의 공통 타입을 가져옵니다
// 이경우 각 각 있기에 세개의 유니온타입을 가져옵니다.
```
