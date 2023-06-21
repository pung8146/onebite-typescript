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
