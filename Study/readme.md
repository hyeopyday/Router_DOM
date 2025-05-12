# 리액트 라우터 돔 정리

* 1. React Router DOM이란?
  - React에서 페이지 이동(라우팅)을 가능하게 해주는 라이브러리

* 2. 쓰는 이유
  - React는 기본적으로 싱글 페이지 앱(SPA)이기 때문에 URL이 바뀌어도 실제로는 한 페이지임 -> React Router DOM은 이 URL 변화에 따라 다른 컴포넌트를 보여주게 해줌
 
* 3. 설치방법
  ```jsx
   npm install react-router-dom
  ```

* 4. 기본 사용법 예시
```jsx
  // App.jsx (혹은 App.js)
import {
  BrowserRouter as Router, // 라우팅을 설정하고 URL을 관리하는 최상위 컴포넌트
  Routes, //  여러 Route를 포함하여 경로에 따라 렌더링할 컴포넌트를 결정
  Route, // 특정 경로에 대한 컴포넌트를 정의하는 컴포넌트
  Link
} from "react-router-dom";

import Home from "./pages/Home";
import About from "./pages/About";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">홈</Link>
        <Link to="/about">소개</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

* 5. 
