# ReactDictionary

React.js 상황에 따른 사용법을 적은 개인 기록장
+ notion 추가 내용 기재

## 로컬에서 시작

```bash
npm start
```

## 빌드

```bash
npm run build
```

## 백앤드 키 숨기기

.env 파일에 작성 및 커밋하기전, .gitignore 파일에 추가. 이 파일 없다면 생성 후 아래 내용을 입력 후 반영

```text
# See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# production
/build

# misc
.DS_Store
.env.local
.env.development.local
.env.test.local
.env.production.local
.env
package-lock.json

npm-debug.log*
yarn-debug.log*
yarn-error.log*

```
