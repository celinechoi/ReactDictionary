# react-router-dom의 Hook

```bash
npm i --save react-router-dom@5.2.0
```

## useHistory (v.5까지)
**버전 6부터는 "useNavigate"로 변경**
페이지 기록을 알수 있는 훅.
컴포넌트 내에 구현하는 메소드에서 라우터에 직접 접근 가능.
```Javascript
const history = useHistory();
history.push(`이동하고자하는 path`);
```
### 자주 사용하는 Method
* go
```Javascript
function handleHistory(){
	history.go(1) // 앞으로 가기
	history.go(-1) // 뒤로가기
	history.go(-2) // 뒤로 두번가기
}
```
* back
```Javascript
function handleHistory(){
	history.back(1) // 이전 url로 
}
```
* replace
```Javascript
function handleHistory(){
	history.replace('/someurl') // 현재 url를 someurl으로 변경
}
```

## useParams
url안의 파라미터 부분을 알고싶을 때 사용하는 훅.
* typescript 사용하는 프로젝트에서 사용 예시: 타입스크립트는 url내에 파라미터가 없다고 기본으로 여기기에, 있다고 설명해야함
* useParams()와 ```Javascript <Route path="/:coinId"><CoinItem/></Route> ``` 관계 있음.

```Javascript
import { useParams } from "react-router-dom";

interface RouteParams {
	coinId: string,
}

function CoinItem(){
	const {coinId} = useParams<RouteParams>();
	return (
		<>
			<h1>{coinId}</h1>
		</>
	)
}

export default CoinItem;
```
또는
```Javascript
import { useParams } from "react-router-dom";

function CoinItem(){
	const {coinId} = useParams<{coinId: string}>();
	return (
		<>
			<h1>{coinId}</h1>
		</>
	)
}

export default CoinItem;
```

## useLocation
```Javascript <Link to={{ pathname:`/${coin.id}`, state: {name: coin.name} }}></Link> ```에서 보내주는 데이터를 받는 훅.
react-router-dom이 보내주는 location Object에 접근할 수 있다.
객체형식을 띈다.
* useLocation()과 ```Javascript <Link to={{ pathname:`/${coin.id}`, state: { name: coin.name } }} ``` 관계 있음.
```Javascript
const useArea = useLocation();
const {result} = useArea.state;
const packageItem = useArea.state.result.package;
```

## Link
파라미터 통해 url에게 정보를 넘길때 사용.
Link를 사용하면 a태그를 직접사용하게 될경우 페이지 이동이 생기지만 Link 훅을 사용하여 페이지 이동을 구현하면 결과적으로 a태그로 보여지지만 페이지 새로고침은 일어나지 않는다.
Link는 굳이 페이지별로 같은 데이터를 반복적으로 불러오지 않는다.
* 비하인드 씬 커뮤니케이션 : 이미 받은 데이터를 재활용 할 수 있는 방법. 
```Javascript
<Link to={{
	pathname: `${coin.id}`,
	state: {
		name: coin.name
	}
}}>
```