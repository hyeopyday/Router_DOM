# 리액트 라우터 돔 정리

* 1. React Router DOM이란?
  - React에서 페이지 이동(라우팅)을 가능하게 해주는 라이브러리

* 2. 쓰는 이유
  - React는 기본적으로 싱글 페이지 앱(SPA)이기 때문에 URL이 바뀌어도 실제로는 한 페이지임 -> React Router DOM은 이 URL 변화에 따라 다른 컴포넌트를 보여주게 해줌
 
* 3. 설치방법
  ```jsx
   npm install react-router-dom
  ```

* 4. 기본 사용법
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
1. path : 경로 설정 속성
  - 기본 방식 : /index (명시적 경로)
  - 와일드카드 방식 : * (모든 경로 포함) /index/* (특정 경로 아래의 모든 경로 포함)
  - 옵셔널 방식 : /index/test? (경로의 일부가 있을 수도, 없을 수도 있음)
  - 파라미터 방식 : /index/:id (경로의 일부를 변수처럼 사용)
 
2. element  : 해당 경로로 이동했을 때 렌더링할 컴포넌트를 설정

3. index  : 기본 경로(/)일 때 렌더링할 컴포넌트를 설정

4. caseSensitive  : 경로의 대소문자를 구분할지 설정

5. errorElement  : 경로로 이동할 때 에러가 발생하면 보여줄 컴포넌트를 설정

* 5. 실사용 예 : (블로그 사이트)
  - / → 메인 페이지
  - /posts → 글 목록
  - /posts/:id → 특정 글 상세보기
 
```jsx
<Route path="/posts" element={<PostList />} />
<Route path="/posts/:id" element={<PostDetail />} />
```

* 6. Apache + Laravel에서 적용하는 법 ( 학교 서버 구축 프로젝트 사용 )
  1. 설정 방법
  - Laravel 라우터 설정 (routes/web.php)

```php
Route::get('/{any}', function () {
    return view('app'); // React 앱을 렌더링
})->where('any', '.*');
```
  2. Apache .htaccess 설정 (public/.htaccess)
  - React 라우터는 새로고침하면 서버에 직접 URL을 요청합니다. 이를 막기 위해 .htaccess 설정 필요:
```php
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    RewriteRule ^index\.html$ - [L]
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /index.html [L]
</IfModule>
```
  3. React 앱 빌드 후 Laravel에 넣기
```bash
npm run build
```
