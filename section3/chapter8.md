[인프런 한입크기로 잘라먹는 타입스크립트 - 이정환](https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%ED%81%AC%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/dashboard)님의 강의를 보고
내용을 정리한 포스팅입니다

# 🥇 서로소 유니온 타입

> 교집합이 없는 타입들로만 만든 유니온 타입을 말함

## 직관적이지 않은코드

> 작동 하는 코드이지만 타인이 보기 어려운 코드입니다.(직관적이지 않음)

```tsx
type Admin = {
  name: string;
  kickCount: number;
};

type Member = {
  name: string;
  point: number;
};

type Guest = {
  name: string;
  visitCount: number;
};
type User = Admin | Member | Guest;

// Admin -> {name}님 현재까지 {kickCount} 명 강퇴했습니다.
// Member -> {name}님 현재까지 {point} 모았습니다.
// Guest -> {name}님 현재까지 {visitCount}번 오셨습니다.
function login(user: User) {
  if ("kickCount" in user) {
    console.log(`${user.name}님 현재까지 ${kickCount} 명 강퇴했습니다.`);
  } else if ("point" in user) {
    console.log(`${user.name}님 현재까지 ${point} 모았습니다.`);
  } else {
    console.log(`${user.name}님 현재까지 ${visitCount}번 오셨습니다.`);
  }
}
```

## 가독성을 수정한 코드

> tag 를 넣어 가독성을 높여줍니다

```tsx
type Admin = {
  tag: "ADMIN";
  name: string;
  kickCount: number;
};

type Member = {
  tag: "MEMBER";
  name: string;
  point: number;
};

type Guest = {
  tag: "GUEST";
  name: string;
  visitCount: number;
};
type User = Admin | Member | Guest;

function login(user: User) {
  if (user.tag === "ADMIN") {
    console.log(`${user.name}님 현재까지 ${kickCount} 명 강퇴했습니다.`);
  } else if (user.tag === "MEMBER") {
    console.log(`${user.name}님 현재까지 ${point} 모았습니다.`);
  } else {
    console.log(`${user.name}님 현재까지 ${visitCount}번 오셨습니다.`);
  }
}
```

## Switch 를 이용하여 가독성 높이기

```tsx
type Admin = {
  tag: "ADMIN";
  name: string;
  kickCount: number;
};

type Member = {
  tag: "MEMBER";
  name: string;
  point: number;
};

type Guest = {
  tag: "GUEST";
  name: string;
  visitCount: number;
};
type User = Admin | Member | Guest;

function login(user: User) {
  switch (user.tag) {
    case ADMIN: {
      console.log(`${user.name}님 현재까지 ${kickCount} 명 강퇴했습니다.`);
      break;
    }
    case MEMBER: {
      console.log(`${user.name}님 현재까지 ${point} 모았습니다.`);
      break;
    }
    case GUEST: {
      console.log(`${user.name}님 현재까지 ${visitCount}번 오셨습니다.`);
      break;
    }
  }
}
```

## 복습겸 한가지 더 사례

> 비동기 작업의 결과를 처리하는 객체를 만들어야 한다 (API,서버처리 등 )

```tsx
type LoadingTask = {
  state: "LOADING";
};
type FaildTask = {
  state: "FAILED";
  error: {
    message: string;
  };
};
type SuccessTask = {
  state:'SUCCESS",
  response: {
    data:string,
  }
};

type AsyncTask = {
  state: "LOADING" | "FAILED" | "SUCCESS";
  error?: {
    message: string;
  };
  response?: {
    data: string;
  };
};

// 로딩중 -> 콘솔에 로딩중 출력
// 실패 -> 실패 : 에러메시지 출력
// 성공 -> 성공 : 데이터를 출력
function processResult(task: AsyncTask) {
  switch (task.state) {
    case "LOADING": {
      console.log("로딩 중");
      break;
    }
    case "FAILED": {
      console.log(`에러 발생 : ${task.error?.message}`);
      break;
    }

    case "SUCCESS": {
      console.log(`성공 : ${task.response?.data}`);
      break;
    }
  }
}

const loading: AsyncTask = {
  state: "LOADING",
};

const faild: AsyncTask = {
  state: "FAILED",
  error: {
    message: "오류 발생 원인은~~",
  },
};

const success: AsyncTask = {
  state: "SUCCESS",
  respones: {
    data: "데이터 ~~",
  },
};
```
