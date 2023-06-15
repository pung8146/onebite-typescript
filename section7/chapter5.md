[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 프로미스

> - TS제네릭을 이용해서 비동기를 처리를 돕는 프로미스 객체의 타입을 정의하는 방법
> - 비동기의 처리의 타입을 직접 설정할 수 있습니다.
> - 프로미스는 제네릭클래스 기반으로 타입이 선언되어있기 때문에 ** 타입변수로 비동기 처리의 결과값의 타입을 지정해줄수있습니다. **
> - 지정하지 않았을경우 unknown 타입으로 취급됩니다

## 성공했을때 코드

```tsx
const promise = new Promise<number>((resolve, reject) => {
  setTimeout(() => {
    resolve(20);
  }, 3000);
});

promise.then((response) => {
  console.log(response * 10);
});
```

## 실패했을때 코드

> - 실패했을때 타입은 정의 할 수 없기에 타입좁히기 등을 사용합니다.
> - 지정하지 않았을경우 any 타입으로 취급됩니다

```tsx
const promise = new Promise<number>((resolve, reject) => {
  setTimeout(() => {
    reject("~때문에 실패");
  }, 3000);
});

promise.then((response) => {
  console.log(response * 10);
});
prmise.catch((err) => {
  if (typeof err === "string") {
  }
});
```

## 프로미스를 반환하는 함수의 타입을 정의

서버로부터 하나의 게시글을 불러와야 되는 상황일때

```tsx
interface Post {
  id: number;
  title: string;
  content: string;
}

function fetchPost() {
  return new Promise<Post>((resolve,reject) => {
    setTimeout(() => {
      resolve(
        id:1,
        title:'임시 게시글',
        content:'임시 게시글 내용'
      );
    }, 3000);
  });
}

const postRequest = fetchPost();

postRequest.then((post) => {
  post.id
})
```
