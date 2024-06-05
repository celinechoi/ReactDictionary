# html-tag

## react-helmet

head태그로 가는 다이렉트 역할을 하는 라이브러리문서의 html "<head></head>"에 추가된다. 타이틀, favicon, css 원하는건 다 넣을 수 있다.

```bash
npm i react-helmet
```

```Javascript
<Helmet>
	<meta charSet="utf-8" />
	<title>App Title</title>
</Helmet>
```

## react-helmet-async

react-helmet의 단점을 커버하는 유사한 라이브러리. react-helmet은 여러 스레드(프로세스 내에서 작업 수행하는 주체)의 동시 접근이 생겨도 프로그램 실행에 문제가 없는 스레드세이프가 없다. 하지만 react-helmet-async은 스레드세이프가 있다.

- 상위 컴포넌트 (예: index.tsx)

```Javascript
<HelmetProvider>
	<App />
</HelmetProvider>
```

- 사용할 해당 컴포넌트 (예: App.tsx)

```Javascript
<Helmet>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" />
	<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;500;700;900&family=Source+Sans+Pro:wght@300;400&display=swap" rel="stylesheet" />
	<title>Page Name</title>
</Helmet>
```
