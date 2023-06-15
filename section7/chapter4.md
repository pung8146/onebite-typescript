[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 제네릭 클래스

```tsx
class NumberList {
  constructor(private list: T[]) {

    push(data:T){
      this.ist.push(data);
    }

    pop() {
      return this.list.pop();
    }

    print(){
      console.log(This.list);
    }
  }

  const numberList = new NumberList([1,2,3 ])
  numberList.pop();
  numberList.push(4)
  numberList.print() // [1,2,4] 로 출력됩니다
}
```

## 기존 만든 class를 다른 타입으로 변경하고싶을때

> - List 클래스를 제네릭 클래스로 변경
> - ** 생성자에 넘버타입 배열을 넣어주면 넘버타입의 리스트가 만들어집니다 **
> - 제네릭 클래스는 제네릭인터페이스,제네릭타입변수와 다르게 클래스 생성자를 호출할때 인수값 의 기준으로 추론합니다.

- 그렇기에 앞에 타입을 굳이 명시할 필요가 없어집니다

```tsx
class List<T> {
  constructor(private list: T[]) {

    push(data:T){
      this.ist.push(data);
    }

    pop() {
      return this.list.pop();
    }

    print(){
      console.log(This.list);
    }
  }

  const numberList = new List([1,2,3 ])
  numberList.pop();
  numberList.push(4)
  numberList.print() // [1,2,4] 로 출력됩니다
}
```
