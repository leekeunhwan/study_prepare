# 2018-10-16 Study Prepare

## CRA 2.0 Review

---

## create-react-app 2.0 Feature

1. <b>No more Webpack, Easy to use sass</b> - 더 이상 Webpack loader 없이 sass 를 사용할 수 있게 되었습니다.

```
$ yarn add node-sass
```

<br>

node-sass 를 설치하면 sass 를 간편하게 사용할 수 있습니다.<br>
기존까지 sass 를 이용하려면 webpack loader 를 설정하는 등<br>
복잡한 과정이 있었습니다. (eject 잘못해서 파일 다시 만드는 경우도 있더랬죠..)<br>

<br>

```js
// FcStudy.js

import React from "react";
import "./FcStudyStyle.scss";

const FcStudy = () => {
  return (
    <div className="FcStudy">
      In order to become a legend,
      <div className="FcStudyExample">Do Our Best</div>
    </div>
  );
};

export default FcStudy;
```

```js
// App.js
import React, { Component } from "react";
import FcStudy from "./FcStudy";

class App extends Component {
  render() {
    return (
      <div className="App">
        <FcStudy />
      </div>
    );
  }
}

export default App;
```

```scss
// FcStudyStyle.scss

.FcStudy {
  display: inline-block;
  background: rgba(166, 55, 33, 0.5);
  color: #fff;
  padding: 1rem;
  text-align: center;

  &Example {
    font-size: 2rem;
    font-weight: 500;
    color: yellow;
    text-align: center;
  }
}
```

<br>

이렇게 잘 sass 가 적용되는 것을 보실 수 있습니다.<br>

<br>

<img src="./asset/image/cra-scss.png">

<br>
<br>

기존에 웹백 loader 를 설정하는등.. sass 를 쓰기위해<br>
귀찮은 작업을 하곤 했었는데 CRA 2.0 이 릴리즈 되면서<br>
편하게 사용할 수 있습니다.<br>

<br>
<br>

2. <b>CSS Module Support</b>

이 기능에 대해서는 스터디에 참여하신 분들중<br>
잘 모르셨던 분들도 있으실 수 있을 것 같다고 생각합니다.<br>
바로 아래 코드와 같은 것들인데요!<br>

```css
/* ExampleCssModule.module */

.exampleBox {
  background: salmon;
  color: white;
  padding: 1rem;
  font-size: 1.3rem;
}

.exampleText {
  color: powderblue;
  font-weight: bold;
}
```

```js
// ModuleCSS.js

import React from "react";
import styles from "./ExampleCssModule.module.css";

const ModuleCSS = () => {
  return (
    <div className={styles.exampleBox}>
      <div className={styles.exampleText}>Hello CSS Module</div>
    </div>
  );
};

export default ModuleCSS;
```

쉽게 말해서 CSS 의 재사용을 위해 모듈화 시킨 것입니다.<br>
CSS Module 을 이용하기 위해서는 .module.css 라는 이름으로<br>
CSS 파일을 작성한 뒤, 기존 css 를 불러오듯 import 를 하되<br>
alias(별칭)을 설정하여 불러오고, 위의 js 코드처럼 사용하면 됩니다.<br>
어때요? 참쉽죠?<br>

<img src="./asset/image/cra-modulecss.png">

<br>
<br>
<br>

3. <b>Upgrade To Babel 7</b>

Babel 7 으로 업그레이드가 되면서 빌드속도가 개선되었습니다.<br>
추가적으로는 preset-typescript 를 통한 타입스크립트 지원 및<br>
자동적인 Polyfill 등의 기능이 도입되었습니다.<br>

특히 리액트를 사용해서 개발을 하는 분들의 경우에는 다음과 같은 점이 흥미로운데요!<br>
기존에 React16 에서 알려진 `<></>` (= <React.Fragment>와 같은 의미)를<br>
사용하기 위해서 별도의 커스터마이징이 필요했는데 Babel 7 으로 오면서<br>
별도의 설정 없이도 사용가능합니다.<br>

```js
// 기존에 코드에 div를 추가했습니다.
// 두개의 태그가 return 태그안에 있어서 에러가 나는데
// 여기에 div, span, React.Fragment가 아닌 <></> 넣어보았습니다.
// 결과는 어떨까요?

import React from "react";
import "./FcStudyStyle.scss";

const FcStudy = () => {
  return (
    <>
      <div className="FcStudy">
        In order to become a legend,
        <div className="FcStudyExample">Do Our Best</div>
      </div>
      <div className="FcStudy">We will do anything!</div>
    </>
  );
};

export default FcStudy;
```

<br>

<img src="./asset/image/cra-babel7.png">

<br>
<br>

에러없이 정상적으로 화면이 출력되는 것을 보실 수 있습니다.<br>
앞써 말씀드린 <a href="https://babeljs.io/blog/2018/08/27/7.0.0#typescript-support-babel-preset-typescript" target="_blank">preset-typescript</a> 와 <a href="https://babeljs.io/blog/2018/08/27/7.0 0#automatic-polyfilling-experimental" target="_blank">자동 폴리필</a>이 궁금하신 분들은 링크를 참조해주세요!!:)<br>

<br>

preset-typescript 을 궁금해하실 분이 있으실 것 같아서 설명드리자면<br>
아래와 같습니다.<br>
<br>

```
1. 다음과 같이 설치를 해준다음 (리액트에는 자동으로 babel이 설치되니 설치할 필요가 없습니다.)
npm 대신 yarn을 사용하시는 경우 npm install 대신 yarn add로 입력해주세요!

npm install --save-dev @babel/preset-typescript @babel/preset-env @babel/plugin-proposal-class-properties @babel/plugin-proposal-object-rest-spread
```

```json
2. 다음과 같이 .babelrc를 설정해줍니다.

{
    "presets": [
        "@babel/env",
        "@babel/preset-typescript"
    ],
    "plugins": [
        "@babel/proposal-class-properties",
        "@babel/proposal-object-rest-spread"
    ]
}
```

```
3. babel / cli로 간단한 빌드를 실행합니다.

babel ./src --out-dir lib --extensions ".ts,.tsx"
```

```json
4. 이제 lib 디렉토리에서 파일을 빌드하고 생성합니다.
TypeScript로 유형 검사를 추가하려면 tsconfig.json 파일을 작성하시면 됩니다.

{
  "compilerOptions": {
    /* Target latest version of ECMAScript. */
    "target": "esnext",
    /* Search under node_modules for non-relative imports. */
    "moduleResolution": "node",
    /* Process & infer types from .js files. */
    "allowJs": true,
    /* Don't emit; allow Babel to transform files. */
    "noEmit": true,
    /* Enable strictest settings like strictNullChecks & noImplicitAny. */
    "strict": true,
    /* Disallow features that require cross-file information for emit. */
    "isolatedModules": true,
    /* Import non-ES modules as default imports. */
    "esModuleInterop": true
  },
  "include": [
    "src"
  ]
}
```

```
5. 작동시킵니다

tsc
```

```js
// 기존에는 타입스크립트를 사용할 경우 parameter에도 타입을 명시했었는데

interface Person {
  firstName: string;
  lastName: string;
}

function greeter(person: Person) {
  return "Hello, " + person.firstName + " " + person.lastName;
}
```

```js
// 이제는 명시하지 않아도 됩니다.

function greeter(person) {
  return "Hello, " + person.firstName + " " + person.lastName;
}
```

자세한 내용은 아래 링크를 참조해주세요!<br>
https://blogs.msdn.microsoft.com/typescript/2018/08/27/typescript-and-babel-7/<br>

<br>
<br>

4. Upgrade To Webpack v4

웹팩이 v4 로 업그레이드되면서 번들링 속도가 개선되었고,<br>
JS 번들을 분리할 때 좀 더 스마트하게 분리한다고 합니다.<br>
`yarn build` 를 입력해보면 아래처럼 나타납니다.<br>

<img src="./asset/image/cra-webpack.png">

1.000.chunk.js 에는 react, react-dom 이<br>
main.000.chunk.js 에는 우리가 작성한 component 들의 코드가 있습니다.<br>

create-react-app v2.0 이전에는 `CommonsChunkPlugin`를 사용해서<br>
했던 작업이 `optimization.splitchunk`라는 API 를 통해 자동으로 이뤄진다고 합니다.<br>
chunk 를 나누고 최적화한다는 내용의 이름의 뜻처럼 닉값(?)하네요!<br>

<br>
<br>

5. Import SVG as React Component

SVG 를 불러올 때 이전처럼 그냥 불러올 수도 있지만

```js
// 기존

import picture from "./picture.svg";
```

이제 컴포넌트화하여 불러올 수 있습니다.

```js
// CRA 2.0

import { ReactComponent as Picture } from "./picture.svg";
```

이렇게 컴포넌트화하여 불러온 svg 를 다음처럼 사용할 수 있습니다.

```js
import React from "react";
import "./FcStudyStyle.scss";
import { ReactComponent as Picture } from "./picture.svg";

const FcStudy = () => {
  return (
    <>
      <div className="FcStudy">
        In order to become a legend,
        <div className="FcStudyExample">Do Our Best</div>
      </div>
      <div className="FcStudy">We will do anything!</div>
      <Picture />
    </>
  );
};

export default FcStudy;
```

Picture.svg 는 가상의 파일이여서 출력 결과를 보여드리지 못하지만<br>
충분히 정상적으로 svg 가 화면에 출력되는 코드이니 svg 파일을 가지고<br>
따라해보시길 권장드립니다!<br>
img 혹은 object 로 불러오거나 별도의 컴포넌트를 만들어서 가져올 필요 없이<br>
사용할 수 있으니 어때요? 참 편하죠?<br>

<br>
<br>

6. Customize proxy settings

종종 웹팩 개발 서버에서 백엔드 API 를 호출시 발생하는 CORS 에러를 방지하기 위해<br>
웹팩 개발 서버에서 proxy 를 설정 할 수 있습니다.<br>
기존에도 package.json 에서 proxy 빌드를 설정할 수 있었습니다.<br>

```json
{
  "name": "what-is-new",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "node-sass": "^4.9.3",
    "react": "^16.5.2",
    "react-dom": "^16.5.2",
    "react-scripts": "2.0.3"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": [">0.2%", "not dead", "not ie <= 11", "not op_mini all"],
  "proxy": "https://jsonplaceholder.typicode.com"
}
```

이렇게 지금도 똑같이 하시면 됩니다.<br>
그럼 뭐가 달라졌냐고 생각하실텐데<br>
바로 커스터마이징이 가능해진 것 입니다.<br>

여기서 직접 커스터 마이징도 가능합니다만<br>
중간 단계에서부터 작업을 해야할 경우는 이 proxy 는 삭제하고,<br>
http-proxy-middleware 라는 모듈을 설치하고,<br>
src 에서 setupProxy.js 라는 파일을 설치합니다. (파일명은 컨벤션입니다.)<br>

```
위에서처럼 yarn 사용자는 npm install 대신 yarn add를 입력해주세요!

npm install http-proxy-middleware axios
```

```js
// src/setupProxy.js

const proxy = require("http-proxy-middleware");

module.exports = function(app) {
  app.use(
    proxy("/posts", {
      target: "http://jsonplaceholder.typicode.com/",
      changeOrigin: true

      // virtual host의 경우 아래처럼 해줍니다.
        target: {
            host: 'hwan.branchYamme.com',
            protocol: 'http:',
            path: '/myBranch/mylunch/js-eat.js',
        },
        // 기타 설정들 (다음은 예시입니다.)
        secure: false,
        ignorePath: true,
        changeOrigin: true,
    })
  );
};
```

여기서 사용하는 app 은 Express 서버 인스턴스입니다.<br>
proxy 쪽에 changeOrigin 의 경우엔 jsonplaceholder 에서<br>
Origin 을 전달하지 않으면 제대로 처리가 안되기에 넣어준 것입니다.<br>

만약 우리가 쓰는 API 서버에서 Virtual Host<br>
(요청 받는 Domain 의 이름에 따라 다른 요청 처리하기)를 사용하고 있다면,<br>
이 설정을 해줘야 합니다.<br>

지금까지 잘 따라오셨다면 이제 axios 를 통해서 요청을 합니다.<br>

```js
import React, { Component } from "react";
import axios from "axios";

class App extends Component {
  state = {
    data: null
  };
  getPost = async () => {
    try {
      const response = await axios.get("/posts/1");
      this.setState({
        data: response.data
      });
    } catch (e) {
      console.log(e);
    }
  };
  componentDidMount() {
    this.getPost();
  }
  render() {
    if (!this.state.data) {
      return <div>로딩중...</div>;
    }
    const { title, body } = this.state.data;

    return (
      <div>
        <h1>{title}</h1>
        <p>{body}</p>
      </div>
    );
  }
}

export default App;
```

<img src="./asset/image/cra-velopert.png">

<br>
<br>
<br>

7. Don"t Support IE

CRA 2.0 부터 Internet Explorer (A.K.A.. 야근유발자)를<br>
기본적으로 아예 지원하지 않는다고 합니다.<br>
지원이 필요하다면 react-app-polyfill 을 사용해야 합니다.<br>

```
이제는 yarn add 말 안해도 아시죠??:)

npm install react-app-polyfill
```

설치가 완료되었으면 src/index.js 에 아래의 코드를 추가해줍니다.

```js
import "react-app-polyfill/ie9"; // For IE9
import "react-app-polyfill/ie11"; // For IE11
```

자세한 내용은 <a href="https://github.com/facebook/create-react-app/tree/master/packages/react-app-polyfill" target="_blank">여기</a>를 참조해주세요!<br>

<br>
<br>

8. ETC..

`serviceWorker.unregister();`의 등장 - 이제는 서비스워커를 사용하려면 이 함수를<br>
`serviceWorker.registser();`로 바꿔야 합니다.<br>
안쓴다고 지우던 게 엇그제 같았는데 이제는 굳이 지우는 번거로운 일을 안해도 되네요!<br>

<br>

<b style="font-size:1.2rem;">여기서 잠깐 서비스워커를 모르시는 분들을 위해 간략한 설명!</b><br>

서비스 워커는 브라우젛가 백그라운드에서 실행하는 스크립트로 웹 페이지와는 <b style="color:salmon;">별개로</b> 작동하며,<br>
웹페이지 또는 사용자 상호 작용이 필요하지 않은 기능에 대해 문호를 개방합니다.<br>
현재 푸시 알림 및 백그라운드 동기화와 같은 기능은 이미 제공되고 있습니다.<br>
향후 서비스 워커는 주기적 동기화 또는 지오펜싱과 같은 다른 기능을 지원할 예정이라고 합니다.<br>

이것이 이처럼 흥미로운 API 인 이유는<br>
<b style="color:salmon;">오프라인 환경을 완벽히 통제할 수 있는 권한을 개발자에게 부여하여 오프라인 환경을 지원할 수 있도록 해주기 때문</b>입니다.<br>

이상으로 create-react-app v 2.0 의 리뷰를 마치겠습니다.!

<br>
<br>
<br>

# 참고자료

> https://babeljs.io/blog/2018/08/27/7.0.0#typescript-support-babel-preset-typescript<br>
>
> https://babeljs.io/blog/2018/08/27/7.0.0#automatic-polyfilling-experimental<br>
>
> https://babeljs.io/blog/2018/08/27/7.0.0#jsx-fragment-support<br>
>
> https://velog.io/@velopert/create-react-app-v2<br>
