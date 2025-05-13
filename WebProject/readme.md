
# 웹프로그래밍 프로젝트 라우터 돔을 이용한 프론트 작업 구상


---

## 1. 라우팅 설정
```jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import TopRightInfoMenu from './components/TopRightInfoMenu';

import PostListPage from './pages/PostListPage';
import PostCreatePage from './pages/PostCreatePage';
import PostDetailPage from './pages/PostDetailPage';
import PostEditPage from './pages/PostEditPage';

import LoginPage from './pages/LoginPage';
import SignupPage from './pages/SignupPage';
import FindIdPage from './pages/FindIdPage';
import ResetPasswordPage from './pages/ResetPasswordPage';

function App() {
  return (
    <Router>
      <div>
        <TopRightInfoMenu />

        <Routes>
          <Route path="/" element={<PostListPage />} />
          <Route path="/post/new" element={<PostCreatePage />} />
          <Route path="/post/:id" element={<PostDetailPage />} />
          <Route path="/post/:id/edit" element={<PostEditPage />} />
          
          <Route path="/login" element={<LoginPage />} />
          <Route path="/signup" element={<SignupPage />} />
          <Route path="/find-id" element={<FindIdPage />} />
          <Route path="/reset-password" element={<ResetPasswordPage />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```
---

## 2. 게시글 목록 (PostListPage.jsx)

```jsx
function PostListPage() {
  return (
    <div>
      <h2>게시글 목록</h2>
      {/* 게시글 리스트 나열 */}
    </div>
  );
}
export default PostListPage;

```
---
## 3. 게시글 작성 (PostCreatePage.jsx)
```jsx
function PostCreatePage() {
  return (
    <div>
      <h2>게시글 작성</h2>
      {/* 제목, 내용 입력 필드 + 작성 버튼 */}
    </div>
  );
}
export default PostCreatePage;
```
---

## 4. 게시글 상세 (PostDetailPage.jsx)
```jsx
import { useParams } from 'react-router-dom';

function PostDetailPage() {
  const { id } = useParams();

  return (
    <div>
      <h2>게시글 상세</h2>
      <p>글 ID: {id}</p>
      {/* 게시글 내용 불러오기 */}
    </div>
  );
}
export default PostDetailPage;
```
---

## 5. 게시글 수정 (PostEditPage.jsx)
```jsx
import { useParams } from 'react-router-dom';

function PostEditPage() {
  const { id } = useParams();

  return (
    <div>
      <h2>게시글 수정</h2>
      <p>수정할 글 ID: {id}</p>
      {/* 기존 게시글 데이터 불러와서 편집 */}
    </div>
  );
}
export default PostEditPage;
```
---

## 6. 로그인 (LoginPage.jsx)
```jsx
function LoginPage() {
  return (
    <div>
      <h2>로그인</h2>
      {/* 이메일, 비밀번호 입력 폼 */}
    </div>
  );
}
export default LoginPage;
```
---
## 7. 회원가입 (SignupPage.jsx)
```jsx
function SignupPage() {
  return (
    <div>
      <h2>회원가입</h2>
      {/* 이름, 이메일, 비번 등 입력 필드 */}
    </div>
  );
}
export default SignupPage;
```
---
## 8. 아이디 찾기 (FindIdPage.jsx)
```jsx
function FindIdPage() {
  return (
    <div>
      <h2>아이디 찾기</h2>
      {/* 이메일 입력 → 아이디 반환 */}
    </div>
  );
}
export default FindIdPage;
```

## 8. 비밀번호 재설정 (ResetPasswordPage.jsx)
```jsx
function ResetPasswordPage() {
  return (
    <div>
      <h2>비밀번호 재설정</h2>
      {/* 이메일 또는 인증 후 새 비밀번호 입력 */}
    </div>
  );
}
export default ResetPasswordPage;
```
