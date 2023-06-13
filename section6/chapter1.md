[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 타입스크립트의 클래스

> - 필드에서 타입 지정이 없다면 자동으로 any 타입으로 추론합니다

- 이니셜라이저(초기값) , 생성자 할당을 해줘야합니다

1.  타입 뒤에 ? 선택적 타입으로만든다 (추천되지 않는방식)
2.  기본값(초기값)을 그냥 넣어줍니다.
3.  초기값 넣기 힘든경우 ** 생성자 ** 를 만들어줍니다
    > - JS에서 클래스 취급이 되면서,** 타입 ** 으로도 취급이 됩니다
    > - 타입스크립트는 ** 구조적 타입 시스템 ** 으 따르며 필드와 메소드를 보고 타입으로 취급될 수 있습니다.

```tsx
let exmployee = {
  name: "박상훈",
  age: 30,
  position: "developer",
  work() {
    console.log("일함");
  },
};

class Employee {
  // 필드 : 클래스가 만들어낼 프로퍼티들을 의미합니다.
  name: string;
  age: number;
  position: string;

  //생성자 : 클래스를 호출하면 실제로 객체를 생성하는 메소드
  constructor(name: string, age: number, position: string) {
    this.name = name;
    this.age = age;
    this.position = position;
  }

  // 메서드
  work() {
    console.log("열심히 일함 ");
  }
}

class ExecuitveOffidar extends Employee {
  // 필드
  officeNumber: number;
  //생성자
  name: string,
  age:numbe.
  postition:string,
  office: numb~
}

let employeeB = new Employee("박상훈", 30, "개발자");
// 인스턴스 student 라고 부를수 있습니다.
employeeB.study();

const employeeC: Employee = {
  name: "",
  age: 0,
  position: "",
  work() {},
};
```
