[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 클래스

> ** JavaScript 클래스는 객체를 생성하기 위한 템플릿으로, 속성과 메서드를 포함하는 코드 블록입니다. **
> class 변수명 작성할때 변수명은 처음 대문자인 파스칼 문법을 자주 사용합니다.
> class를 이용해서 만든 객체를 인스턴스 라고 부릅니다.
> ** class 안 필드,메소드에선 쉼표를 찍지 않습니다 **
> this 는 객체를 가리킵니다

```tsx
let student A = {
    name: '이정환',
    grade: 'A+',
    age:27,
    study() {
        console.log('열심히공부함');
    },
    introduce() {
        console.log('안녕하세요')
    }
};

class Student {
    // 필드 : 클래스가 만들어낼 프로퍼티들을 의미합니다
    name;
    grade;
    age;

    //생성자 : 클래스를 호출하면 실제로 객체를 생성하는 메소드
    constructor(name,grade,age){
        this.name = name;
        this.grade = grade;
        this.age = age;
    }

    // 메서드
    study() {
        console.log('열심히 공부함 ')
    }
    introduce(){
        console.log(`안녕하세요 ${this.name} 입니다`)
    }
}

let studentB = new Student('박상훈','B+',30);
// 인스턴스 student 라고 부를수 있습니다.
studentB.study();
studentB.introduce();


```

## 확장

> 확장을 해주면 필드,매서드 등이 그대로 가져옵니다.

### super

> 부모 클래스가 호출이 되고 생성자에 this.프로퍼티로 들어옵니다.

```tsx
class StudentDeveloper extends Student {
  // 필드
  favoriteSkill;
  // 생성자
  constructor(name, grade, age, favoriteSkill) {
    super(name, grade, age);
    this.favoriteSkill;
  }
  // 메서드
  programming() {
    console.log(`${(this, favoriteSkill)}로 프로그래밍 함`);
  }
}

const studentDeveloper = new StudentDeveloper("박상훈", "B+", 30, "TypeScript");
studentDevevloper.programming();
```
