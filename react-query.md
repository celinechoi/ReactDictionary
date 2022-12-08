# react-query
API로 부터 response를 받고 있어서 우리가 화면을 바꿨다가 돌아오더라도 data가 이미 캐시(cache)에 저장되어 있다.
그래서 다시 API에 접근하지 않고 캐시(cache)에 저장된 데이터를 불러온다.

React version 18이상이면 @tanstack/react-query 설치해서 사용
```bash
npm i --save @tanstack/react-query
```
dev는
```bash
npm i -D @tanstack/react-query-devtools
```


* api.ts
```Javascript
const BASE_PATH = "example";

export interface IgetCoins {
	id: string;
	name: string;
	symbol: string;
	rank: string;
}

export function getCoins(){
	return fetch(`${BASE_PATH}`).then(response => response.json());
}
```
* CoinsList.tsx
```Javascript
import { useQuery } from "@tanstack/react-query";
function CoinsList(){
	const {data, isLoading} = useQuery<IgetCoins[]>(["coins"], getCoins);
}
export default CoinsList;
```

## react-query/devtools
데이터를 주고 받는걸 시각화한 개발자도구(Developer tools)
* react-query에 있는 devtools를 import하면 캐시에 있는 query를 볼 수 있다.
* App.tsx
```Javascript
import {ReactQueryDevtools} from "react-query/devtools";
function App() {
  return (
    <>
      <GlobalStyle />
      <Router />
      <ReactQueryDevtools initialIsOpen={true} />
    </>
  );
}
export default App;
```