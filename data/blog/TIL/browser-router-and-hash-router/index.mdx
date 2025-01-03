---
title: '브라우저 라우팅와 해시 라우팅'
date: '2025-01-02T13:33:27.982Z'
summary: '항해 2주차에서 배운 것'
tags: ['JavaScript']
---

이번 항해플러스를 수강하면서 브라우저 라우팅과 해시 라우팅 개념에 대해 접할 수 있었습니다.
둘의 차이에 대해 학습하며, 이를 정리한 글을 작성하게 되었습니다.

## 라우팅의 진화

웹의 초기에는 모든 페이지 전환이 전체 페이지를 새로 로드하는 방식이었습니다.
사용자가 링크(우리가 알고 있는 a 태그)를 클릭하면 서버에서 새로운 HTML을 받아와 전체 페이지를 다시 그리는 방식으로 이를 Multiple Page Application, 줄여서 `MPA`라고 합니다.
이는 매번 새로운 페이지를 요청할 때마다 서버에서 완전한 HTML을 다운로드하고 브라우저가 처음부터 다시 페이지를 렌더링해야 했기 때문에, 불필요한 서버 요청과 화면 깜빡임을 발생시켰고 결과적으로 사용자 경험을 저해했습니다.

2005년 Ajax 기술이 등장하면서 웹의 새로운 가능성이 열렸습니다. Gmail과 같은 서비스들은 Ajax를 활용해 페이지 전체를 새로고침하지 않고도 콘텐츠를 동적으로 업데이트할 수 있게 되었고, 이는 후에 Single Page Application, 줄여서 `SPA`이라는 개념으로 발전하게 됩니다.

<figure>
  <img src="https://github.com/user-attachments/assets/629ec145-718e-4695-a031-6067d8c7dd1f" />
  <figcaption>
    출처: [Single Page Apps vs. Multi-Page
    Apps](https://www.naukri.com/code360/library/single-page-apps-vs-multi-page-apps)
  </figcaption>
</figure>

`SPA`가 발전하면서 클라이언트 측 라우팅의 필요성이 대두되었습니다. 이에 URL의 `해시(#)` 부분을 활용한 `해시 라우팅` 방식이 도입되었습니다.

## 해시 라우팅

`해시(#)` 부분이 변경되어도 페이지가 새로고침되지 않는다는 특성을 활용한 것이었습니다.
이는 모든 브라우저에서 동작했고, 서버 설정도 필요 없었습니다. 서버 요청 없이 클라이언트에서 라우팅 처리가 가능했습니다.

```
// 해시 라우팅 URL 예시
https://example.com/#/
https://example.com/#/about
https://example.com/#/products/1
```

`해시 라우터`는 다음과 같이 구현할 수 있습니다.

```ts
export const createHashRouter = (routes) => {
  // 현재 해시 경로를 가져오는 함수
  const getPath = () => {
    // 해시가 없으면 '/'를, 있으면 '#' 이후의 경로를 반환
    return window.location.hash ? window.location.hash.slice(1) : '/';
  };

  // 현재 경로에 해당하는 라우트 핸들러를 가져오는 함수
  const getTarget = () => {
    const currentPath = getPath();
    return routes[currentPath] || routes['404'];
  };

  // 새로운 경로로 이동하는 함수
  const push = (path) => {
    window.location.hash = path;
  };

  // 해시 변경 이벤트 처리
  window.addEventListener('hashchange', () => {
    const handler = getTarget();
    if (handler) {
      handler();
    }
  });

  // 초기 로드 시 해시가 없는 경우를 처리
  window.addEventListener('load', () => {
    if (!window.location.hash) {
      push('/');
    } else {
      const handler = getTarget();
      if (handler) {
        handler();
      }
    }
  });

  return {
    get path() {
      return getPath();
    },
    push,
    getTarget,
  };
};
```

`해시 라우터`는 `window.location.hash`를 갈아 끼우는 형태로 URL을 변경합니다. 또한 `hashchange` 이벤트를 통해 해시 값이 변경될 때마다 해당하는 컴포넌트를 렌더링합니다.

## 브라우저 라우팅

그러다 HTML5가 등장하면서 [`History API`](https://developer.mozilla.org/ko/docs/Web/API/History_API)가 소개되었고, 이를 기반으로 한 `브라우저 라우팅` 방식이 새로운 표준으로 자리잡게 됩니다.
이제 개발자들은 실제 URL을 조작하면서도 페이지 새로고침 없이 상태를 관리할 수 있게 되었습니다.

`브라우저 라우터`는 다음과 같이 구현할 수 있습니다.

```ts
export const createBrowserRouter = (routes) => {
  // 현재 경로 가져오기
  const getPath = () => window.location.pathname;

  // 현재 경로에 해당하는 라우트 핸들러를 가져오는 함수
  const getTarget = () => {
    const currentPath = getPath();
    return routes[currentPath] || routes['404'];
  };

  // 새로운 경로로 이동하는 함수
  const push = (path) => {
    // History API를 사용하여 URL 변경
    window.history.pushState({}, '', path);
    // 라우트 핸들러 실행
    const handler = getTarget();
    if (handler) handler();
  };

  // 브라우저 뒤로가기/앞으로가기 처리
  window.addEventListener('popstate', () => {
    const handler = getTarget();
    if (handler) handler();
  });

  // 초기 로드 처리
  window.addEventListener('load', () => {
    const handler = getTarget();
    if (handler) handler();
  });

  return {
    get path() {
      return getPath();
    },
    push,
    getTarget,
  };
};
```

`브라우저 라우터`는 `pushState()`로 URL을 변경합니다. 또한 `popstate` 이벤트를 통해 뒤로가기/앞으로가기를 처리할 수 있습니다.

`브라우저 라우터`를 사용할 때는 서버 설정이 중요합니다. 일반적으로 서버에는 다음과 같은 파일들만 존재합니다.

```
app/
├── index.html
├── static/
    ├── js/
    │   └── bundle.js
    └── css/
        └── styles.css
```

즉, 실제 서버에는 /about이나 /products 같은 경로에 해당하는 물리적인 파일이 없습니다. 이런 경로들은 클라이언트 사이드에서 자바스크립트에 의해 처리되는 가상의 경로입니다.

예를 들어

1. / 경로 접속: 서버의 index.html 제공
2. /about 경로 접속: 서버에는 해당 파일이 없음 → 404 에러

이 문제를 해결하기 위해 모든 요청을 index.html로 보내는 서버 설정이 필요한 것입니다.

## SEO적인 측면

`해시 라우터`는 SEO에 불리한 특성을 가지고 있습니다. 검색 엔진의 크롤러는 URL의 `해시(#)` 이후 부분을 무시하기 때문입니다.

```
https://example.com/#/products
https://example.com/#/about
https://example.com/#/contact

// 실제로 검색 엔진이 인식하는 URL
https://example.com/
```

이로 인하여

1. 개별 페이지의 컨텐츠가 검색 결과에 독립적으로 나타나지 않음
2. 페이지별 메타 데이터 설정이 어려움
3. 검색 엔진의 페이지 랭킹에 불리
4. 소셜 미디어 공유 시 모든 페이지가 동일한 미리보기를 보여줌

의 문제가 있어 SEO에 불리한 특성을 가지고 있습니다.

반면에 `브라우저 라우터`는 실제 URL 경로를 사용하기 때문에 SEO에 유리합니다. 각 URL이 고유한 경로를 가지므로

1. 검색 엔진이 각 페이지를 개별적으로 인덱싱
2. 페이지별 메타 데이터 설정 가능
3. 페이지별 SEO 최적화 가능성
4. 소셜 미디어 공유 시 페이지별 적절한 미리보기 제공

이 가능합니다.

## 해시 라우터의 존재 이유

실제로 우리가 사용하는 React Router도 `브라우저 라우터`와 `해시 라우터`를 선택할 수 있습니다.

```tsx
// BrowserRouter 사용
import { BrowserRouter } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

// HashRouter 사용
import { HashRouter } from 'react-router-dom';

function App() {
  return (
    <HashRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </HashRouter>
  );
}
```

그런데 앞서 언급한 내용들로만 보면 해시 라우터보다는 History를 지원하는 `브라우저 라우터`가 좀 더 모던한 라우터처럼 느껴집니다.
그렇다면 React Router에는 왜 `해시 라우터`가 존재하는 것일까요?

이유는 `정적 호스팅`에 있습니다.

`정적 호스팅`은 서버에서 동적으로 페이지를 렌더링하지 않고, 미리 만들어진 정적 파일을 제공하는 방식입니다.

예를 들어 GitHub Pages나 S3와 같은 정적 호스팅 환경에서는 서버 설정을 변경할 수 없습니다. 이런 환경에서 `브라우저 라우터`를 사용하면 문제가 발생합니다.

1. example.github.io/about로 접근
2. 서버는 /about 경로의 파일을 찾으려고 시도
3. 실제로는 그런 파일이 없어서 404 에러가 발생

만약 `해시 라우터`를 사용하면

1. example.github.io/#/about으로 접근
2. 서버는 # 이후를 무시하고 항상 index.html만 제공
3. 클라이언트에서 #/about 부분을 해석해서 라우팅 처리

따라서 정적 호스팅 환경에서는 `해시 라우터`를 사용하는 것이 적합합니다.

### ✏️ 출처

https://www.naukri.com/code360/library/single-page-apps-vs-multi-page-apps <br/>
https://developer.mozilla.org/ko/docs/Web/API/History <br/>
https://developer.mozilla.org/ko/docs/Web/API/History_API <br/>
https://fe-developers.kakaoent.com/2022/221124-router-without-library/
