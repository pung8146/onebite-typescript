[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 객체 타입의 호환성

> 어떤 객체 타입을 다른 객체 타입으로 취급해도 괜찮은가? ** 추가프로퍼티가 없는 / 조건이 더적은 타입이 슈퍼타입이됩니다. **

# 🥇 타입 호환표와 계층표 둘중 편한걸로 이해하면 됩니다.

## 🥈 타입 계층표

![](https://velog.velcdn.com/images/pung8146/post/27174401-b113-4a8d-a8ff-c27b19b1478b/image.png)

## 🥈 타입 호환표

![](https://velog.velcdn.com/images/pung8146/post/5aa82306-35fb-4995-8773-7717f2e21160/image.png)

```tsx
type Animal = {
  name: string;
  color: string;
};

type Dog = {
  name: string;
  color: string;
  breed: string;
};

let animal: Animal = {
  name: "기린",
  color: "yellow",
};

let dog : Dog ={
    name:'돌돌이',
    color:'brown',
    breed:"푸들'
}

animal = dog;// 에러가 일어나지 않습니다
dog = animal;// 에러가 일어 납니다.
```

## 🥈 추가 프로퍼티검사

> 객체타입의 변수를 초기화할때 skill같은 초과프로퍼티가 book에서는 없기에 작동되지 않습니다.

```tsx
type Book = {
    name:string,
    price:number
}

type ProgrammingBook = {
    name:string,
    price:number,
    skill:string,
}

let book:Book;
let programmingBook:ProgrammingBook = {
    name:'한 입 크기로 잘라 먹는 리액트',
    number:33000,
    skill:'reactjs',
}

book = programmingBook; // 업 캐스팅 가능합니다
programmingBook = book; // 다운 캐스팅 불가능합니다

let book2: Book = {
    name:'한 입 크기로 잘라 먹는 리액트',
    number:33000,
    skill:'reactjs',// 오류가 출력됩니다
  }

let book3: book = programmingBook; // 초과 프로퍼티 검사가 발동하지 않습니다.

function func(book :Book) { // 함수의 매개변수에도 타입이 지정 가능합니다.
    name:'한 입 크기로 잘라 먹는 리액트',
    number:33000,
    skill:'reactjs',// 오류가 출력됩니다
}
// 만약에 사용한다면
func(programmingBook)
```

### 🥉 기본 타입간의 호환성

```tsx
let num1: number = 10;
let num2: 10 = 10;

num1 = num2; // 허용됩니다 (업캐스팅)
```
