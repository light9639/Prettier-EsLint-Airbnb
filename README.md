# :zap: Vite 설치방법
## :zap: Vite 프로젝트 만들기
- npm
```
$ npm create vite@latest
```
- yarn
```
$ yarn create vite
```
- pnpm
```
$ pnpm create vite
```
## :zap: Vite를 이용해 React 프로젝트를 만들려고 한다면
- npm 6.x
```
npm create vite@latest my-react-app --template react
```
- npm 7+, '--'를 반드시 붙여주세요
```
npm create vite@latest my-react-app -- --template react
```
- yarn
```
yarn create vite my-react-app --template react
```
- pnpm
```
pnpm create vite my-react-app --template react
```
## :zap: Vite package.json Script 부분 작성
```
{
  "scripts": {
    "dev": "vite", // 개발 서버를 실행합니다. (`vite dev` 또는 `vite serve`로도 시작이 가능합니다.)
    "build": "vite build", // 배포용 빌드 작업을 수행합니다.
    "preview": "vite preview" // 로컬에서 배포용 빌드에 대한 프리뷰 서버를 실행합니다.
  }
}
```
## :zap: 확장 프로그램 설치
- Prettier - Code formatter를 VsCode 확장프로그램에서 설치하기

<img src="https://raw.githubusercontent.com/light9639/Prettier-EsLint-Airbnb/main/public/prettier.png" alt="prettier">

- EsLint를 VsCode 확장프로그램에서 설치하기

<img src="https://raw.githubusercontent.com/light9639/Prettier-EsLint-Airbnb/main/public/esLint.png" alt="EsLint">

## :zap: Eslint Prettier 설치 / 연동
- airbnb 스타일 가이드의 코드 규칙을 적용하기 위한 종속성 설치
```
yarn add --dev eslint prettier
yarn add --dev eslint-config-airbnb
```
- eslint-config-prettier: eslint와 prettier간 충돌나는 규칙을 비활성화해주는 eslint 설정
- eslint-plugin-prettier: prettier 규칙을 생성하는 eslint 플러그인
```
yarn add --dev eslint-config-prettier
yarn add --dev eslint-plugin-prettier
```
## :zap: .prettier.js 작성법
- .prettier.js 파일 생성 후 작성(json 파일로 생성해도 되지만, 주석의 용이성을 위해서)
```
module.exports = {
    singleQuote: true,
    // 문자열은 작은 따옴표로 통일
    semi: true,
    //코드 마지막에 세미콜른이 자동 생성
    useTabs: false,
    //탭의 사용을 금하고 스페이스바 사용으로 대체
    tabWidth: 4,
    // 들여쓰기 너비는 4칸
    trailingComma: 'all',
    // 객체나 배열 키:값 뒤에 콤마 생성
    printWidth: 80,
    // 코드 한줄이 maximum 80칸
    arrowParens: 'avoid',
    // 화살표 함수가 하나의 매개변수를 받을 때 괄호 생략
};
```
- 해당 세팅은 자신이 원하는대로 설정하면 됩니다
  - 참고: https://prettier.io/docs/en/configuration.html
## :zap: .eslintrc.js 작성법
- .eslintrc.js 파일 생성 후 작성(json 파일로 생성해도 되지만, 주석의 용이성을 위해서)
```
module.exports = {
    env: {
        browser: true,
        es6: true,
        node: true,
    },
    extends: [
        'eslint:recommended',
        'airbnb',
        'prettier',
        'plugin:prettier/recommended',
    ],
    rules: {
        'react/jsx-filename-extension': [
            'error',
            { extensions: ['.js', '.jsx'] },
        ],
    },
};
```