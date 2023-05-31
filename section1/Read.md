# TS초기 설정

npm init 초기화후
npm i @types/node
npm install typescript -g // 전역설치 (설치가 안될경우 mac은 sudu / window는 관리자권한으로 실행 해야 설치가 됨 )
tsc src/index.ts 터미널에서 입력시 컴파일 실행이되고 index.js파일이 생성됩니다  
npm install ts-node -g //ts와 노드를 한번에 까는법

tsc --init

## TS 파일을 컴파일 하는법

- ts-node 폴더위치/파일.ts 입력
- tsc 입력시 폴더내 TS 파일들이 JS파일들로 생성됩니다.

# tsconfig

## CompilerOptions

### CompilerOptions - target

-
- es5 구버전 /ESNext 자바스크립트 치신버전

### CompilerOptions - module

### CompilerOptions - strict

- true일땐 엄격히 검사
- false 일땐 유연히 검사

- JS=> TS로 전환하는 작업시 strict를 true로 되있는 경우 에레가 많이 나와 꺼두기도 합니다.

## include

# 타입스크립트는 모든 모듈을 ** 전역 모듈 ** 로 취급합니다.

#### 그렇기에 모든 변수가 같은 곳에 있는 것으로 취급됩니다.

## 두가지 해결방법

### 첫번째

- export import 같은 모듈 시스템 활용하는방법
- 이럴경우 독립된 모듈로 판단합니다.

### 두번째

- tsconfig 옵션 조절
- 각각의 파일을 어떤 모듈로 감지할지 정하는옵션
- "moduleDetection" : "force"
- 각각의 파일들을 개별 모듈로 자동으로 만들어 줍니다.
- export/import 가 자동으로 추가 됩니다.

# tsconfig 수정 후 작동이 안될때

- 컨트롤 + P
- > restart 검색 후 실행
- ts가 다시 실행 다시 검사합니다.

## ts-node

### ts-node esm

- true esm 모듈로 실행됩니다.
