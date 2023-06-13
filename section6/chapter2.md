[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 접근제어자(access modifier) => public private proteced

> - 생성자 내에서도 설정할 수 있습니다.

    - 생성자에서 접근제어자를 사용시 필드가 자동으로 생성됩니다.(기존에 필드가 적혀있다면 오류가 출력될수도 있습니다.)
    - 필드에 값도 자동으로 초기화되서 this.변수 = 변수 설정을 할 필요가 없습니다.

- 객체지향코드 작성에서 중요합니다.

## public

> const employee 의 외부에서 값을 변하게 할 수 있는건 class 타입 선언시 적혀있지 않아도 기본으로 public 설정이 되어있습니다.

## private

> 필드의 접근 제어자로 private 을 설정하면 점표기법으로 읽을수도 없습니다.
> readonly 와 다른점으로 아예 읽을수가 없습니다.
> 내부(메소드) 안에서는 접근을 할 수 있습니다.

## protected

> 파생 클래스 내부에서 접근하고싶을때 사용합니다

```tsx
class Employee {
  // 필드 : 클래스가 만들어낼 프로퍼티들을 의미합니다.
  public name: string;
  private age: number;
  protected position: string;

  //생성자 : 클래스를 호출하면 실제로 객체를 생성하는 메소드
  constructor(name: string, age: number, position: string) {
    this.name = name;
    this.age = age;
    this.position = position;
  }

  // 메서드
  work() {
    console.log(`$(this.name) 입니다.`);
  }
}

const employee = new Employee("박상훈", 30, "developer");
// 수정이 가능한이유는 class public 이 붙어있기 때문입니다.
employee.name = "홍길동";
employee.age = 27;
employee.position = "rich";
```

## 파생 클래스 내부에서 접근

> 파생 클래스 내부에서도 오류가 출력됩니다.

```tsx
class ExecuitveOffidar extends Employee {
  // 필드
  officeNumber: number;
  //생성자
  constructor(
      name: string,
      age:numbe.
      postition:string,
      office: numb~
  ) {
    super(name,age,position);
    this.officeNumber = officeNumber;
  }

  // 메서드
  func() {
    this.name
    // 파생클래스 내부에서도 오류가 출력됩니다.
  }
}


```
