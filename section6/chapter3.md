[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 인터페이스와 클래스

> 보통 인터페이스로 먼저 만들일은 없지만, 라이브러리의 구현이나 복잡하거나 정교한 설계도를 필요한 과정에 요구되기도합니다.

> implements : 구현하다

```tsx
interface characterInterface {
  name: string;
  moveSpeed: number;
  move(): void;
}

class Character implements CharacterInterface {
  name: string;
  moveSpeed: number;
  // 필드 정의
  constructor(
    public name: string,
    public moveSpeed: number,
    private extra: string
  ) {}
  // 메서드
  move(): void {
    console.log(`${this.moveSpeed} 속도로이동!`);
  }
}
```
