<img src="./lit_logo.png">

# lit 2.0 getting started

### 소개
이 프로젝트는 vite의 보일러플레이트에 기반한 lit 2.0 getting started를 수행하였음\
\
공홈의 Getting Started 링크는 [여기](https://lit.dev/docs/getting-started/)이며 한글 번역본은 없다\
\
lit 2.0는 구글 프로젝트 답게 하위버전과 호환되지 않는 것으로 보인다. lit 1.0과는 임포트 구문부터 다르다\
\
참고로 lit 2.0의 임포트문은

```javascript
import {LitElement, html} from 'lit';
```

이지만 lit 구버전의 임포트문은

```javascript
import { LitElement, html } from "lit-element";
```
으로 시작한다


---

### lit 2.0 소개

lit는 웹 컴포넌트에 기반한 UI 프레임워크이다\
\
웹 컴포넌트라는 용어가 생소하면 [네이버 d2의 기사](https://d2.naver.com/helloworld/188655)나 [MDN 문서](https://developer.mozilla.org/ko/docs/Web/Web_Components)를 참조할것
\
간단하게 설명하면 웹 컴포넌트는 웹브라우저 수준에서 네이티브 수준으로 지원하는 리액트 컴포넌트다. 비록 이 정의가 부정확 하더라도 어떤 개념인지 감을 잡는데는 도움이 된다\
\
따라서 lit는 UI컴포넌트를 만드는 도구인데 이는 `리액트의 클래스 컴포넌트와 개념적으로나 구조적으로 비슷하다`\
\
차이점은 리액트 컴포넌트기 최종적으로 html엘리먼트로 렌더링되는데 반하여 lit컴포넌트는 웹컴포넌트로 렌더링된다\
\
lit를 `클라이언트 사이드 렌더링 방식`으로 쓰려면 lit 컴포넌트가 정의된 js파일을 `<script type="module" />` 구문으로 임포트하라. 만일 모듈로 임포트하지 않으면 정상적으로 작동하지 않을 것이다\
\
모듈로 lit 컴포넌트를 임포트하면 js파일 내부에서 호출된 `window.customElements.define()` 메소드에 의해 html 커스텀 엘리먼트로 등록된다\
\
html 커스텀 엘리먼트는 다른말로 웹 컴포넌트이고 define메소드의 처리가 완료되면 네이티브 html 엘리먼트와 거의 유사한 구문으로 사용할수있다.\
\
가상돔이 필요없고 실제 html파일에 직접 엘리먼트를 삽입하여 사용하므로 ReactDOM.render()같은 js기반 렌더링 과정이 필요없다\
\
lit는 기본적으로 `클라이언트-사이드-렌더링`이지만 `서버사이드 렌더링(SSR)` 기능도 가능하다. SSR을 원한다면 선언적 쉐도우돔을 이용하라. 이 기능은 [아스트로](https://astro.build/) 프레임워크에서 지원한다\
\
웹컴포넌트는 쉐도우돔 기반이므로 css-in-js는 기본이다

---

### Q & A

Q. onclick을 어떻게 표현하는가?\
A. @click이다. 이 방법은 vue의 방법과 똑같다.\
\
Q. onclick에 이벤트 핸들러 함수는 어떻게 등록하는가?\
A. @click에 인자로 메소드를 넣는다. 리액트의 방법과 완전히 똑같다.\
\
Q. lit는 클래스 컴포넌트 기반인데 컴포넌트 내에서 변수는 어떻게 생성하는가?\
A. static properties라는 메소드 내부에서 생성한다\
\
Q. 초기화는 어디서 하는가?\
A. 컴포넌트의 constructor() 메소드에서 초기화한다\
\
Q. 변수를 초기화하지 않고 쓸 수 있는가?\
A. 변수를 props로 넘겨서 사용하면 굳이 초기화할 필요가 없다\
\
Q. css는 어떻게 적용하는가?\
A. static style이라는 변수를 생성해서 css스타일을 정의한다
