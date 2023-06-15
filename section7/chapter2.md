[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 map,forEach

## map 메서드

> - 꼭 스트링타입의 인수를 전달한다해서 스트링 타입의 배열이 나올필요가없습니다.
> - 이를 해결할려면 제너릭타입 인수를 하나만 쓰면 안됩니다.

```tsx
const arr = [1, 2, 3];
const newArr = arr.map((it) => it * 2);
// [2,4,6]

function map<T, U>(arr: T[], callback: (item: T) => U) {
  let result = [];
  for (let i = 0; i < arr.length; i++) {
    result.push(callback(arr[i]));
  }
  return result;
}

map(arr, (it) => it * 2);
```

## map 메서드

```tsx
const arr = [1, 2, 3];
const arr2 = [1, 2, 3];
arr2.forEach((it) => console.log(it));

function forEach<T>(arr: T,callback:(item:T) => void){
  for(let i = 0; i < arr.length; i++){
    callback(arr[i])
  }
};

forEach(arr2, it) => {
  console.log(it.toFixed())
}

forEach(['123','456'],(it) =>{
  it
})
```
