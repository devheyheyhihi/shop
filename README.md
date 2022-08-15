# shop

css 파일에서 src 폴더안에 있는 사진을 사용하고 싶으면 

./이미지경로

html 안에서 이미지를 집어넣고 싶으면 
이미지를 import 해오고 사용해야합니다.

어디 호스팅되어있는 외부 이미지는 절대경로 그대로 작성하면 잘보입니다. 


public 폴더의 용도  

여러가지 소스코드는 src 폴더에 보관하면 되는데 
이미지같은 static 파일의 경우 public 폴더에 보관해도 됩니다.

리액트로 개발을 끝내면 build 작업이라는걸 하는데 
지금까지 짰던 코드를 한 파일로 압축해주는 작업입니다. 
src 폴더에 있던 코드와 파일은 다 압축이 되는데 public 폴더에 있는 것들은 그대로 보존해줍니다.
이미지, txt, json 등 수정이 필요없는 static 파일들의 경우엔 public 폴더에 보관해도 상관없습니다. 

권장되는 방식 <img src={process.env.PUBLIC_URL + '/logo192.png'} />

서브경로 만들 수 있는 nested routes
<Route path="/about" element={ <About/> } >  
  <Route path="member" element={ <div>멤버들</div> } />
  <Route path="location" element={ <div>회사위치</div> } />
</Route>

<Outlet></Outlet>

페이지를 여러개 만들고 싶으면 URL 파라미터라는 문법을 사용가능합니다. 

path 작명할 때 /:어쩌구 이렇게 사용하면 "아무 문자"를 뜻

useParams() 라는 함수를 상단에서 import 해오면 쓸 수 있는데

이거 쓰면 현재 /:url파라미터 자리에 유저가 입력한 값을 가져올 수 있습니다.

styled-components
1. class 만들어놓은걸 까먹고 중복해서 또 만들거나

2. 갑자기 다른 이상한 컴포넌트에 원하지않는 스타일이 적용되거나

3. CSS 파일이 너무 길어져서 수정이 어렵거나
그래서 스타일을 바로 입혀서 컴포넌트를 만들어버릴 수있다

styled-components 기본적인 사용법 
1. <div>를 하나 만들고 싶으면 저렇게 styled.div 라는걸 사용하면 됩니다.

<p> 만들려면 styled.p 이런 식임 

2. 오른쪽에 `` backtick 기호를 이용해서 CSS 스타일을 넣을 수 있습니다. 

3. 그럼 그 자리에 컴포넌트를 남겨주는데 변수에 저장해서 쓰면 됩니다. 

장점1. CSS 파일 오픈할 필요없이 JS 파일에서 바로 스타일넣을 수 있습니다.

장점2. 여기 적은 스타일이 다른 JS 파일로 오염되지 않습니다. 원래 그냥 CSS파일은 오염됩니다.
css 도 컴포넌트명.module.css하면 오염 방지 가능
장점3. 페이지 로딩시간 단축됩니다.

 props 문법 지원

컴포넌트는

1. 생성이 될 수도 있고 (전문용어로 mount)

2. 재렌더링이 될 수도 있고 (전문용어로 update)

3. 삭제가 될 수도 있습니다. (전문용어로 unmount)
컴포넌트 인생 중간중간에 간섭할 수 있기 때문
간섭이 뭐냐면 그냥 코드실행인데 
컴포넌트가 장착이 될 때 특정 코드를 실행할 수도 있고 
컴포넌트가 업데이트될 때 특정 코드를 실행할 수도 있다는 겁니다.

갈고리를 달아서 코드를 넣어주면 됩니다.갈고리는 영어로 hook이라고 합니다. 

 useEffect()
콜백함수 추가해서 안에 코드 적으면 이제 그 코드는 컴포넌트가 mount & update시 실행
useEffect 안에 적은 코드는 html 렌더링 이후에 동작합니다.예를 들어서 굉장히 시간이 오래걸리는 쓸데없는 코드가 필요
조금이라도 html 렌더링이 빠른 사이트를 원하면
함수의 핵심기능 외에 쓸데없는 기능들을 프로그래밍 용어로 side effect라고 부릅니다.
쓸데없는 것들은 useEffect 안에 넣어보길 바랍니다. 
컴포넌트의 핵심 기능은 html 렌더링이라 
그거 외의 쓸데없는 기능들은 useEffect 안에 적으라는 소리입니다. 
오래걸리는 반복연산, 서버에서 데이터가져오는 작업, 타이머다는거 

useEffect()의 둘째 파라미터로 [ ] 를 넣을 수 있는데
 [ ]에 있는 변수나 state 가 변할 때만 useEffect 안의 코드를 실행
아무것도 안넣으면 컴포넌트 mount시 (로드시) 1회 실행하고 영영 실행해주지 않습니다.

clean up function
useEffect 동작하기 전에 특정코드를 실행하고 싶으면
return ()=>{} 안에 넣을 수 있습니다. 

서버란?
유저가 데이터달라고 요청을 하면 데이터를 보내주는 간단한 프로그램

서버에 데이터를 요청할 때는 정확한 규격에 맞춰서 요청해야하는데 

1. 어떤 데이터인지 (URL 형식으로)

2. 어떤 방법으로 요청할지 (GET or POST)

데이터를 가져올 때는 보통 GET 고르면 되고 

데이터를 서버로 보낼 때는 POST 고르면 됩니다. 

그리고 어떤 데이터를 보고싶은지 URL만 잘 기재

POST요청을 날리고 싶으면

<form action="요청할url" method="post"> 태그 이용

AJAX란? 
서버에 GET, POST 요청을 할 때 새로고침 없이 데이터를 주고받을 수 있게 도와주는
간단한 브라우저 기능

POST요청 하는 법 

axios.post('URL', {name : 'kim'})
이거 실행하면 서버로 { name : 'kim' } 자료가 전송됩니다. 

JSON은 문자 취급을 받기 때문에 서버와 자유롭게 주고받을 수 있습니다.

axios 라이브러리는 JSON -> object/array 변환작업을 자동으로 해줘서 

출력해보면 object/array가 나옵니다. 
완료시 특정 코드를 실행하고 싶으면 이것도 역시 .then() 뒤에 붙이면 됩니다.

props 쉽게 쓰고 싶으면
function TabContent({탭})

애니메이션 만들고 싶으면 

1. 애니메이션 동작 전 스타일을 담을 className 만들기 

2. 애니메이션 동작 후 스타일을 담을 className 만들기 

3. transition 속성도 추가

4. 원할 때 2번 탈부착

setTimeout 왜 씁니까
리액트 18버전 이상부터는 automatic batch 라는 기능이 생겼습니다.

Context API 문법으로 props 없이 state 공유하기
createContext() 함수를 가져와서 context를 하나 만들어줍니다.
context를 쉽게 비유해서 설명하자면 state 보관함입니다. 
    <Context1.Provider value={{}}>
    </Context1.Provider>
1. 만들어둔 Context를 import 해옵니다.
2. useContext() 안에 넣습니다. 

실은 잘 안쓰는 이유는 

1. state 변경시 쓸데없는 컴포넌트까지 전부 재렌더링이 되고 
2. useContext() 를 쓰고 있는 컴포넌트는 나중에 다른 파일에서 재사용할 때 Context를 import 하는게 귀찮아질 수 있습니다.

그래서 이것 보다는 redux 같은 외부라이브러리를 많이들 사용합니다.

Redux는 props 없이 state를 공유할 수 있게 도와주는 라이브러리

Redux 셋팅

1. 아무데나 store.js 파일을 만들어
2. index.js 파일가서 Provider 라는 컴포넌트와 아까 작성한 파일을 import 
<Provider store={import해온거}> 이걸로 <App/> 을 감싸면 됩니다. 

Redux store에 state 보관하는 법 
step 1. createSlice( ) 로 state 만들고
step 2. configureStore( ) 안에 등록하면 됩니다.

store의 state 변경하는 법 
1. store.js 안에 state 수정해주는 함수부터 만듭니다. 
slice 안에 reducers : { } 열고 거기 안에 함수
2. 다른 곳에서 쓰기좋게 export 해둡니다.
3. 원할 때 import 해서 사용합니다. 근데 dispatch() 로 감싸서 써야함 
dispatch( state변경함수() )

Q. 컴포넌트에서 state 직접 수정하면 편하지 않나요?

그럼 당장은 편한데 나중에 프로젝트가 커지면 심각한 단점이 있을 수 있습니다. 

 
