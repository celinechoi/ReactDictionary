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
## useLocation
현재 사용자가 머물고 있는 페이지에 대한 정보를 알려주는 훅.
객체형식을 띈다.
```Javascript
const useArea = useLocation();
const {result} = useArea.state;
const packageItem = useArea.state.result.package;
```