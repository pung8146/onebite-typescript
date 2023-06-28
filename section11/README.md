# React - TS적용

> 1. npx create-react-app . // . 을 붙이는 이유는 새로운 폴더를 생성하지 않고 현재 폴더내에서 파일들이 생성됩니다.
> 2. 안쓰는 파일과 코드들을 제거해줍니다.
> 3. npm i @types/node @types/react @types/react-dom @types/jest
> 4. tsconfig.json 최상단 디렉토리에 파일생성해줍니다
> 5. tsconfig.json 기초적인 코드를 작성합니다

```json
{
  "comilerOptions": {
    "target": "ES5",
    "module": "CommonJS",
    "strict": true,
    "allowJs": true,
    "esModuleInterop": true
  },
  "include": ["src"]
}
```

> 6. js파일든 이제 jsx문법을 사용해야 되므로 확장자를 변경합니다.
> 7. js,jsx 파일들 한번에 변경하는것보다 하나씩 tsx로 변경하는게 좋습니다.

## 상태관리

> 8.  useState(①) ①: 특정값을 넣으면 그값을 기준으로 타입을 추론하며 공백일경우 undefined로 추론합니다.

> 9.  TS에서 useState(①) : 공백으로 두면 undefined만 사용해야되는점이있어 공백을 사용하는걸 지양합니다.

> 10 공란으로 두어야 될경우 useState<string>() 등 타입을 지정해줘야합니다. => <string|undefined> 유니온이 됩니다.
