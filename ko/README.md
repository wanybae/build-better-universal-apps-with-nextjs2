# Next.js 2.0을 이용하여 보다 나은 Universal JavaScript 앱을 만들기
## TL;DR: 
<!-- On Tuesday, October 25 2016, a small JavaScript framework, Next.js was released to the public. It's a minimal framework for building server-rendered universal JavaScript web apps. Within a few months of its existence, it gathered a lot of attention from the JavaScript community. The React community was set ablaze with joy for finally having a tool that can help build server-side rendering apps without hassle and in-depth technical know-how. In fact, we covered how to build a universal JavaScript web app with it. The team behind Next.js did not take a break, they continued working tirelessly for months to fix several bugs, improve performance and still make the framework as simple as possible. Their efforts have yielded a Next.js 2.0 release. -->

 2016년 10월 25일 화요일, 작은 JavaScript 프레임워크인 **Next.js**가 릴리스 되었습니다. 이는 서버 랜더링을 포함한 Universal JavaScript 웹 앱을 위한 최소한의 프레임워크입니다. 몇달 안에 **Next.js**는 JavaScript 커뮤니티로부터 많은 주목을 받게 되었습니다. React 커뮤니티에서는 드디어 깊은 기술지식과 엄청난 노력없이 서버사이드 랜더링 앱을 만드는 데에 도움이 되는 툴이 나왔다면서 즐거움에 흥분했습니다. 다음 포스트에서 [How to build a universal JavaScript web app](https://auth0.com/blog/building-universal-apps-with-nextjs) 위 내용을 다루었습니다. **Next.js** 팀은 쉴 틈이 없었고, 계속해서 몇몇 버그들을 수정하기위해서 끊임없이 일하여, 향상된 성능과 가능한한 간단한 프래임워크를 만들었습니다. 그 결과 **Next.js 2.0**을 릴리스하게 되었습니다.

## Universal JavaScript 어플리케이션이란 무엇인가?

 *Universal JavaScript*를 새로운 용어로 사용하는 사람들을 위해서 약간의 컨택스트를 제공하는 것

<!-- Universal simply means the ability to run the same code on the server, browsers, mobile devices and any other platform. Universal Javascript is a term people are leaning towards these days. A lot of developers also call it Isomorphic JavaScript. In short, there is a debate on the React repo about this term. Michael Jackson, a popular ReactJS developer wrote a blog post on Universal JavaScript. It's indeed true that naming things is one of the most difficult aspects of Computer Science. -->

  *Universal* 이라는 용어는 단순히 서버, 브라우저, 모바일 장치 및 기타 플랫폼에서 동일한 코드를 실행할 수 있는 기능을 의미합니다. *Universal Javascript*는 요즘 사람들이 꽤 애착을 두고 있는 용어입니다. 많은 개발자들은 이를 **Isomorphic JavaScript**라고도 합니다. 요컨데 이 용어에 대한 토론이 벌어지고 있는 곳([React repo](https://github.com/facebook/react/pull/4041))이 있습니다. 인기있는 ReactJS 개발자인 Michael Jackson씨는 [Universal JavaScript](https://medium.com/@mjackson/universal-javascript-4761051b7ae9#.ij2c0zh8j)에 대한 블로그 포스트를 작성했는데요. 여기서 그는 컴퓨터공학에서 가장 어려운 것중 하나가 명명하는 것이라고 했습니다. 

## Next.js 2.0에서 무엇이 새롭게 등장했나?

<!-- Next.js 2.0 was released on On March 27, 2017. It comes bundled with a set of new features and improvements of existing features. Next.js 1.0 already included the following features: -->

 Next.js 2.0은 2017년 3월 27일에 릴리스 되었습니다. 새로운 기능 셋과 개선된 기존 기능이 같이 번들로 제공됩니다. *Next.js 1.0*에는 다음 기능들이 이미 포함되어 있습니다:

- Hot code reloading
- 자동 transpilation과 bundling(babel과 webpack을 사용)
- 서버 랜더링과 /pages 디렉토리 내에서의 JavaScript 화일 인덱싱
- 정적화일 서빙
- CSS의 격리와 모듈화


 그래서, 뭐가 바뀌었나? 어떤 개선이 이루어졌나? 새로운 기능은 있는건가? 새 버전으로 제작 된 Next.js 앱을 실제로 제작할 준비가 되었는지? 자, **Next.js 2.0**에서 제공하는 모든 것을 살펴봅시다!

### 1. 컴파일 시간의 단축

<!-- Every developer and their dog need their apps to be highly performant from development stage up until production. A lot of work has been done to improve the dev build time that Next.js 1.0 brought to the scene. With great joy, I hereby announce to you that Next.js 2.0 comes bundled with shorter build/rebuild times. This was made possible by offering Lazy compilation during development. This simply means that before now, when you run next, it compiles all the pages. But now, lazy compilation ensures that it is only when a user hits a page, that compilation happens. So each page that is called by the user is an on-demand entry. -->

 모든 개발자와 그들의 반려견은 개발 단계부터 프로덕션 단계까지 앱 성능이 뛰어나야합니다. **Next.js 1.0**에서는 dev 빌드 시간을 개선하기 위해 많은 작업이 수행되었습니다. 아주 기분 좋은 소식은, **Next.js 2.0**에서는 빌드 / 리빌드 시간이 더 짧아졌다는 겁니다. 이는 [개발 중에 Lazy 컴파일](https://github.com/zeit/next.js/pull/1111)을 걸어둘 수 있게 되었다는 겁니다. 이건 이전까지는, `next`를 실행할 때 모든 페이지를 컴파일했다는 의미입니다. 하지만 이제부터는 Lazy 컴파일은 사용자(역주:Next.js를 이용하는 개발자)가 페이지에 접근 할 때에만 해당 컴파일을 하도록 합니다. 따라서 사용자가 호출하는 각 페이지는 주문형 항목이 됩니다.

<!-- Lazy Compilation during development Lazy Compilation during development-->

![Lazy Compilation during development](https://cdn.auth0.com/blog/next20/lazycompilationdev.png) *Lazy Compilation during development*

![Implement on-demand entries](https://cdn.auth0.com/blog/next20/lazycompilation.png) *Implement on-demand entries*

### 2. 사전 Gzip 압축

<!-- Next.js 2.0 automatically gzips all your static JavaScript files and serves them when you build your app by running next build . This saves a lot of CPU power especially for apps deployed in cloud function-like environments.-->

**Next.js 2.0**에서는 *next build*를 실행할때 모든 정적 JavaScript화일을 자동으로 gzip압축을 하고 앱을 빌드할때 압축된 파일들을 서브합니다. 이렇게하면 특히 클라우드 환경에 배포된 앱의 경우에 많은 CPU성능을 절약할 수 있습니다.

### 3. 작고 효율적인 빌드

<!-- Apart from reducing the dev build times, Next.js 2.0 offers much smaller and more-efficient builds than its' previous version. So by default, your app size is now smaller. -->

 개발 시간을 줄이는 것과는 별개로 **Next.js 2.0**은 이전 버전보다 훨씬 작고 효율적인 빌드를 제공합니다. 따라서 기본 앱 사이즈가 작아졌습니다. 

<!-- Bundle sizes for 1.0 and 2 Basic site with Next.js and React bundled -->

![1.0과 2.0의 번들 사이즈](https://cdn.auth0.com/blog/next20/newbundlesize.png)
Next.js와 React로 번들 된 기본 사이트

자료제공: [zeit.co](https://zeit.co/blog/next2)

<!-- Page loads have also been made faster by making initial bundle files to be cached permanently on clients. -->

초기 번들 파일을 클라이언트에 영구적으로 캐시함으로써 페이지로드가 빨라졌습니다.

<!-- An issue was raised in Next.js 1.0 about shared dependencies between pages that caused latency when browsing through different server-rendered pages, and the ever-ready team found a way to solve it by setting up Webpack common chunks to avoid shipping repeated code across components. -->

**Next.js 1.0**에서는 서로 다른 서버사이드 랜더링이 된 페이지를 브라우징할 때 대기시간을 야기시킨 페이지 간에 공유된 디펜던시에 대한 이슈가 있었는데, 준비된 팀에서 webpack common chunk설정을 통해서 반복적인 코드나 컴포넌트를 무시하고 건너 뛸 수 있는 방법을 찾아냈습니다.

![Shared dependency issues](https://cdn.auth0.com/blog/next20/sharedependenciesissue.png) *공유 디펜던시 이슈*

![Shared dependency issues solved](https://cdn.auth0.com/blog/next20/shareloadsolved.png) *CommonChunkPlugin으로 해결된 디펜던시 이슈*

### 4. 라우팅을 위한 프로그래밍 API

<!-- In the first major version of Next.js, dynamic routing was only possible with query strings. There was no way to acheive clean and fancy URLs and loading your own custom server code was a big challenge. With Next.js 2, those challenges are a thing of the past. -->

 **Next.js**의 첫번째 메이저 버전에서 동적 라우팅은 쿼리 문자열만 사용 가능했습니다. 깔끔하고 멋진 URL을 아카이브할 방법이 없었고, 커스텀 서버코드를 로딩하는 것은 꽤 어려운 일이였습니다. **Next.js 2.0**에서는 이제 위와 같은 일들은 과거의 일이 되었습니다.

![Custom routing](https://cdn.auth0.com/blog/next/customrouting.png) *2016년의 이슈*

<!-- You can now write your own custom server programmatically, customize routes and use different route patterns like so: -->

 이제 프로그래밍 방식으로 커스텀 서버에 작성할 수 있고, 라우트를 커스터마이징할 수 있고, 다음과 같이 다른 경로 페턴을 사용할 수 있습니다:

```
const express = require('express')
const next = require('next')

const dev = process.env.NODE_ENV !== 'production'
const app = next({ dev })
const handle = app.getRequestHandler()

app.prepare().then(() => {

const server = express()

  server.get('/p/:username', (req, res) => {
    return app.render(req, res, '/z', {
      ...req.query,
      username: req.params.username
    })
  })

  server.get('*', handle)
  server.listen(3333)
})
```

<!-- In the code sample above, you have set up a custom server. The path /p/prosper where prosper is the :username is resolved to ./pages/z . The page gets access to the username parameter and can do whatever has been programmed in it. Check out this example. -->

 위와같은 예제코드에서는 커스텀 서버를 설정했습니다. `prosper`가 `/p/prosper`인 경로는 `:username`은 `./pages/z`로 해석됩니다. 이 페이지는 username 매개변수에 액세스 할 수 있으면 이 매개변수에 프로그래밍 된 내용을 다 수행할 수 있습니다. 다음 [예제](https://github.com/zeit/next.js/blob/master/examples/custom-server)를 확인해 보세요.

### 5. 페이지 프리 페치

<!-- Next.js 2 comes bundled with an API that allows you prefetch pages. Any <Link> tag can accept a prefetch prop and prefetch the pages it links to in the background like so: -->

 **Next.js 2.0**에서는 페이지를 프리 페치하는 API가 번들로 제공됩니다. 모든 `<Link>` 테그는 `prefetch` 프로퍼티를 받아들일 수 있으며 다음과 같이 링크된 페이지를 프리 페치 할 수 있습니다:

```
import Link from 'next/link'

export default () => (
  <nav>
    <ul>
      <li><Link prefetch href='/pricing'><a>About</a></Link></li>
      <li><Link prefetch href='/auth0'><a>Contact</a></Link></li>
    </ul>
  </nav>
)
```

<!-- This gives you the performance of an SPA coupled with server rendering. Wow, that's better performance with little efforts. Whoop! Whoop! -->

 이렇게 하면 서버 렌더링이 포함된 SPA의 성능을 얻을 수 있죠. 오호!! 적은 노력으로 괜찮은 성능을 얻어낼 수 있다니. 오예~~ 

### 6. 이뮤터블 캐싱

<!-- When you build your app with next build and start your app, Next.js 2 will serve your JavaScript files and other assets as immutable assets. This simply means that once the browser has downloaded any immutable asset, if you reload the browser page, your browser won't try to load these assets from the server again. -->

 `next build`로 앱을 빌드하고 앱을 시작하면, **Next.js 2.0**은 JavaScript 화일과 기타 리소스들(assets)을 이뮤터블 리소스로서 서빙하게 됩니다. 이는 단순히 브라우저가 이뮤터블 리소스를 다운로드한 후에 브라우저 페이지를 리로드하면 브라우저가 서버에서 이 리소스를 리로드 하려고 시도하지 않는다는 것을 의미합니다.

<!-- Another gain for performance and speed. Whoop! Whoop! -->

 성능과 속도를 위한 또다른 이득! 오예~~

### 7. Babel과 Webpack 커스텀 설정

<!-- Next.js 2 is fully extensible. You have complete control over Babel's and Webpack's configuration. For example, if you want to extend Babel, you can simply define a .babelrc file at your app's root and apply next/babel preset. With that, you include whatever babel plugins you need like so: -->

 **Next.js 2.0** 완벽하게 확장이 가능합니다. Babel과 Webpack의 설정을 완벽하게 할 수 있습니다. 예를들어서, 만약 Babel을 확장하기 위해서 간단하게 `.babelrc`화일을 앱루트에 정의하고 `next/babel`의 프리셋을 적용하면 됩니다. 이를 통해서 다음과 같이 원하는 어떤 Babel 플러그인이든 포함시킬 수 있습니다:

```
{
  "presets": ["next/babel"],
  "plugins": ["transform-flow-strip-types"]
}
```

<!-- Check out this working example. -->

다음 [셈플 예제](https://github.com/zeit/next.js/tree/master/examples/with-custom-babel-config)를 확인해보세요.

<!-- To extend the usage of Webpack in Next.js, you can create a next.config.js file in the root of your project's directory. Once you have that, you can define a function in the Node.js module like so: -->

 **Next.js**에서 `Webpack`을 확장해서 사용하려면, `next.config.js`화일을 프로젝트 루트 디렉토리에 생성하세요. 일단 그렇게 하면 다음과 같이 Node.js에서 함수를 정의할 수 있습니다:

```
module.exports = {
  webpack: (config, { dev }) => {
    // Perform customizations to config

    // Important: return the modified config
    return config
  }
}
```
<!-- Note: The next.config.js file is a regular Node.js module.-->

**참고**: `next.config.js` 화일은 일반 Node.js 모듈입니다.

### 8. 정리된 CSS의 지원

<!-- Before now, next/css was the default CSS-in-JS solution for Next.js. In Next.js 2, it has been deprecated in favor of styled-jsx, a Babel transformation that provides full, scoped and component-friendly CSS support for JSX (rendered on the server or the client). -->

이전까지는, `next/css`는 Next.js의 기본 `CSS-in-JS` 솔루션이었습니다. **Next.js 2.0**에서는 이게 더이상 사용되지 않고 스타일드 컴포넌트(역주:밑에 예제와 같이 CSS를 컴포넌트화 한 방식)로 사용하게 됩니다.

```
export default () => (
  <div>
    <textarea />
    <button>add comment</button>
    <style jsx>{`
      textarea {
        width: 400px;
        height: 100px;
        display: block;
        margin-bottom: 10px;
      }

      button {
        padding: 3px 4px;
      }
      @media (max-width: 750px) {
        textarea {
          width: 100%;
        }
      }
    `}</style>
  </div>
)
```

<!-- In the code example above, you can see how it provides scoped support for this JSX-written component. -->

 위의 코드를 보면, JSX로 씌여진 컴포넌트에 명확히 스타일의 범위가 정리되어 제공되고 있는걸 볼 수 있습니다.

### 9. Next에서 React 격리시키기

<!-- Before now, Next.js shipped with React. All you needed to do was:-->

이전에는, **Next.js**는 **React**와 같이 제공되었었죠. 그래서 다음과 같이 `next`만 설치하면 되었습니다:
`npm install next --save`

<!--In Next.js 2.0, you now need to bring in next with react and react-dom like so:-->

**Next.js 2.0**에서는 앞으로 `next`와 같이 `react`와 `react-dom`도 같이 설치해야 합니다:
`npm install --save next react react-dom`

 이를 통해 [Preact](https://github.com/zeit/next.js/tree/master/examples/using-preact)와 같은 다른 React API를 사용할 수 있습니다. 또한 Next.js와 독립적으로 React를 업데이트 할 수 있습니다.

<!-- This creates opportunity for you to use other React API implementations such as Preact. It also allows you to update React independently of Next.js. -->

### 10. 백엔드 통합의 실제 사례

<!-- Many developers have been helping out in providing examples on how to integrate Next.js with several backend technologies.-->

많은 개발자들이 Next.js를 여러 백엔드 기술과 통합하는 방법에 대한 예제를 제공하는 데에 도움을 주었습니다.

* [Hapi 통합](https://github.com/zeit/next.js/blob/master/examples/custom-server-hapi)
* [Express 통합](https://github.com/zeit/next.js/blob/master/examples/custom-server-express)
* [Koa 통합](https://github.com/zeit/next.js/blob/master/examples/custom-server-koa)

### 11. 학습 플랫폼의 가용성

<!-- It's amazing to see that in a short time that Next.js has been in existence, lots of examples have been amassed and there is a learning platform that the Next.js team approves of. With the release of Next.js 2, we have: -->

 Next.js의 많은 예제가 축적되어 Next.js 팀이 승인 한 학습 플랫폼이 존재한다는 사실에 놀라게 될껍니다. **Next.js 2.0** 릴리스로 우리는 다음과 같은 결과를 얻었습니다:

<!-- * About 48 examples of integrating Next.js with Apollo, Inferno, Preact and ways of achieving different common functionalities with Next.js
* learnnextjs.com, built by Arunoda Susiripala -->

* [Next.js와 Apollo, Inferno, Preact를 통합](https://github.com/zeit/next.js/tree/master/examples)하고 Next.js와 다른 공통 기능을 구현하는 방법에 대한 48 가지 예
* [Arunoda Susiripala](https://twitter.com/arunoda)씨가 만든 [learnnextjs.com](https://learnnextjs.com/)

![Learn Next.js](https://cdn.auth0.com/blog/next20/learnnextjs.png) *learnnextjs.com 랜딩 페이지*

![Logged In view](https://cdn.auth0.com/blog/next20/loggedinview.png) *learnnextjs.com에 로그인 하고 나서의 화면*

<!-- Oh, the UI and Backend for learnnextjs.com is open-source. This presents another opportunity to learn Next.js 2.0 by going through its source code. -->

 아, [learnnextjs.com](https://learnnextjs.com/)의 [UI](https://github.com/arunoda/coursebook-ui)와 [백엔드](https://github.com/arunoda/coursebook-server)는 오픈 소스입니다. 이것은 소스 코드를 통해 **Next.js 2.0**을 배울 수 있는 또 다른 기회를 제공합니다.

## Next.js 2.2.0으로 들어가기

<!-- **Next.js 2.2.0** was tagged yesterday. It comes bundled with some nice changes: -->

**Next.js 2.2.0**에서 몇가지 꽤 괜찮은 변경점들이 번들로 제공됩니다.:

<!-- * CDN support: You might want to upload all your static files to a CDN, including build files. Now, you can serve Next.js static assets via a CDN. All you need is to expose the following option in next.config.js like so: -->

* **CDN 제공**: 빌드 파일을 포함해서 모든 정적 화일을 CDN에 업로드 하기를 원했었죠. 이제 CDN을 통해 Next.js 정적 리소스들을 제공 할 수 있습니다. 다음과 같이 `next.config.js`에 다음 옵션을 추가하면됩니다.
```
const isProd = process.NODE_ENV === 'production'
module.exports = {
  // Production에서 assetPrefix만 추가하면 됩니다.
  assetPrefix: isProd? 'https://cdn.mydomain.com' : ''
}
```
자세한 정보는 [다음 PR](https://github.com/zeit/next.js/pull/1700)에서 확인을 할 수 있습니다.

<!-- More information can be found here.-->

<!-- * ETag support for server rendered pages : The ETag HTTP response header is an identifier for a specific version of a resource found at a URL. It allows caches to be more efficient, and saves bandwidth, as a web server does not need to send a full response if the content has not changed. However, if the content has changed, etags are useful to help prevent simultaneous updates of a resource from overwriting each other. Etags are otherwise known as fingerprints used for tracking resource changes on the server. -->

* **서버 렌더링 페이지에 대한 ETag 지원**: ETag HTTP 응답 헤더는 URL에서 발견되는 특정 버전의 리소스에 대한 식별자입니다. 웹 서버는 내용이 변경되지 않은 경우 전체 응답을 전송할 필요가 없기 때문에 캐시의 효율성을 높이고 대역폭을 절약 할 수 있습니다. 그러나 내용이 변경된 경우 Etag는 자원의 동시 업데이트가 서로 겹쳐 쓰는 것을 방지하는 데 유용합니다. 반면에 Etag는 서버의 변경자원들을 추적하는 데에 사용되는 지문으로 알려져 있습니다.

Next.js에서 서버에서 랜더링 된 모든 페이지들은 Etag를 지원합니다.
<!--In Next.js, all server-rendered pages now support Etags.-->

<!-- * New official examples on how to use Next.js with other technologies:
  * Material UI
  * Socket.io
  * Semantic UI
  * Firebase -->

* 어떻게 Next.js를 다른 기술들과 같이 사용하는지에 대한 새로운 공식 예제들:
  * [Material UI](https://github.com/zeit/next.js/tree/master/examples/with-material-ui)
  * [Socket.io](https://github.com/zeit/next.js/tree/master/examples/with-socket.io)
  * [Semantic UI](https://github.com/zeit/next.js/tree/master/examples/with-semantic-ui)
  * [Firebase](https://github.com/zeit/next.js/tree/master/examples/with-firebase)

<!-- More information can be found in the [release notes](https://github.com/zeit/next.js/releases/tag/2.2.0). -->

자세한 정보는 [릴리스 노트](https://github.com/zeit/next.js/releases/tag/2.2.0)를 참고해 주세요.

## Aside: Auth0을 사용한 Next.js 2.0 앱의 인증

<!-- Auth0 issues JSON Web Tokens on every login for your users. This means that you can have a solid identity infrastructure, including single sign-on, user management, support for social identity providers (Facebook, Github, Twitter, etc.), enterprise identity providers (Active Directory, LDAP, SAML, etc.) and your own database of users with just a few lines of code. -->

**Auth0**은 사용자 로그인 할 때마다 [JSON 형태의 웹 토큰](https://jwt.io/)을 발행합니다. 즉, [싱글 사인온(SSO)](https://auth0.com/docs/sso/single-sign-on), 사용자 관리, 소셜 ID 제공 업체(Facebook, Github, Twitter 등), 엔터프라이즈 ID 제공자(Active Directory, LDAP, SAML 등)에 대한 지원을 비롯하여 견고한 [ID 인프라](https://auth0.com/docs/identityproviders)를 보유 할 수 있습니다. 몇 줄의 코드만으로 사용자 데이터베이스를 구축 할 수 있습니다.

<!-- We can easily set up authentication in a Next.js 2.0 apps by using the Lock Widget. If you don't already have an Auth0 account, sign up for one now. Navigate to the Auth0 management dashboard, click on `New client` by the right hand side, select Regular Web App from the dialog box and then go ahead to the `Settings` tab where the client ID, client Secret and Domain can be retreived.-->

 [잠금 위젯](https://auth0.com/lock)을 사용하여 **Next.js 2.0** 앱에서 인증을 쉽게 설정할 수 있습니다. 여기서 Auth0 계정이 필요한데 없다면 가입하세요. Auth0 관리 대시 보드로 이동하여 오른쪽에있는 '새 클라이언트'를 클릭하고 대화 상자에서 일반 웹 응용 프로그램을 선택한 다음 클라이언트 ID, 클라이언트 비밀 번호 및 도메인을 검색 할 수있는 '설정'탭으로 이동하십시오.

<!-- Note: Make sure you set the `Allowed Callback URLs` to `http://localhost:3000/` or whatever url/port you are running on. Also set the `Allowed Origins (CORS)` to `http://localhost:3000/` or whatever domain url you are using, especially if it is hosted. -->

참고: `Allowed Callback URL`을 `http://localhost:3000/` 또는 사용중인 url/port로 설정하세요. `Allowed Origins (CORS)`를 `http://localhost:3000/` 또는 여러분이 사용하고있는 도메인 URL로 설정하세요.

<!-- Authentication in a Next.js app could be a little complicated because you have to ensure that the server-rendered pages are authenticated, meaning they need to have access to the token.-->

 Next.js 앱의 인증은 서버 렌더링 페이지가 인증되었는지, 즉 토큰에 액세스해야 하는지를 확인해야하기 때문에 조금 복잡 할 수 있습니다.

<!-- In the example below, the token returned from Auth0 is stored in LocalStorage and also as a cookie. -->

아래 예제에서 Auth0에서 반환 된 토큰은 LocalStorage에 저장되며 쿠키로도 저장됩니다.

<!-- Check out [the completed app on Github](https://github.com/auth0-blog/next2-auth0).-->

 [Github에 완성된 앱](https://github.com/auth0-blog/next2-auth0)을 확인하세요.

*utils/auth.js*
```
import jwtDecode from 'jwt-decode'
import Cookie from 'js-cookie'

const getQueryParams = () => {
  const params = {}
  window.location.href.replace(/([^(?|#)=&]+)(=([^&]*))?/g, ($0, $1, $2, $3) => {
    params[$1] = $3
  })
  return params
}

export const extractInfoFromHash = () => {
  if (!process.browser) {
    return undefined
  }
  const {id_token, state} = getQueryParams()
  return {token: id_token, secret: state}
}

export const setToken = (token) => {
  if (!process.browser) {
    return
  }
  window.localStorage.setItem('token', token)
  window.localStorage.setItem('user', JSON.stringify(jwtDecode(token)))
  Cookie.set('jwt', token)
}

export const unsetToken = () => {
  if (!process.browser) {
    return
  }
  window.localStorage.removeItem('token')
  window.localStorage.removeItem('user')
  window.localStorage.removeItem('secret')
  Cookie.remove('jwt')

  window.localStorage.setItem('logout', Date.now())
}

export const getUserFromCookie = (req) => {
  if (!req.headers.cookie) {
    return undefined
  }
  const jwtCookie = req.headers.cookie.split(';').find(c => c.trim().startsWith('jwt='))
  if (!jwtCookie) {
    return undefined
  }
  const jwt = jwtCookie.split('=')[1]
  return jwtDecode(jwt)
}

export const getUserFromLocalStorage = () => {
  const json = window.localStorage.user
  return json ? JSON.parse(json) : undefined
}

export const setSecret = (secret) => window.localStorage.setItem('secret', secret)

export const checkSecret = (secret) => window.localStorage.secret === secret
```

*utils/lock.js*
```
import { setSecret } from './auth'

import uuid from 'uuid'

const getLock = (options) => {
  const config = require('../config.json')
  const Auth0Lock = require('auth0-lock').default
  return new Auth0Lock(config.AUTH0_CLIENT_ID, config.AUTH0_CLIENT_DOMAIN, options)
}

const getBaseUrl = () => `${window.location.protocol}//${window.location.host}`

const getOptions = (container) => {
  const secret = uuid.v4()
  setSecret(secret)
  return {
    container,
    closable: false,
    auth: {
      responseType: 'token',
      redirectUrl: `${getBaseUrl()}/auth/signed-in`,
      params: {
        scope: 'openid profile email',
        state: secret
      }
    }
  }
}

export const show = (container) => getLock(getOptions(container)).show()
export const logout = () => getLock().logout({ returnTo: getBaseUrl() })
```

pages/auth/sign-in.js
```
import React from 'react'

import defaultPage from '../../hocs/defaultPage'
import { show } from '../../utils/lock'

const CONTAINER_ID = 'put-lock-here'

class SignIn extends React.Component {
  componentDidMount () {
    show(CONTAINER_ID)
  }
  render () {
    return <div id={CONTAINER_ID} />
  }
}
```

export default defaultPage(SignIn)
Display the login page once the sign-in component gets mounted.

![Sign in](https://cdn.auth0.com/blog/secret/sign-in.png) Sign-in page

pages/auth/signed-in.js

```
import React, { PropTypes } from 'react'

import { setToken, checkSecret, extractInfoFromHash } from '../../utils/auth'

export default class SignedIn extends React.Component {
  static propTypes = {
    url: PropTypes.object.isRequired
  }

  componentDidMount () {
    const {token, secret} = extractInfoFromHash()
    if (!checkSecret(secret) || !token) {
      console.error('Something happened with the Sign In request')
    }
    setToken(token)
    this.props.url.pushTo('/')
  }

  render () {
    return null
  }
}
```

<!--Grab the token and secret from Auth0 as it returns to the callback which is the signed-in page, save it and redirect to the index page. -->

로그인 페이지인 콜백으로 돌아가서 Auth0에서 토큰과 시크릿을 가져 와서 저장하고 인덱스 페이지로 리디렉션하세요.

![Signed in](https://cdn.auth0.com/blog/signedin/authenticated.png) *시크릿 페이지는 사용자가 로그인하여 액세스 할 수 있음을 보여줍니다.*

*pages/index.js*

```
import React, { PropTypes } from 'react'
import Link from 'next/link'

import defaultPage from '../hocs/defaultPage'

const SuperSecretDiv = () => (
  <div>
    This is a super secret div.
    <style jsx>{`
      div {
        background-color: #ecf0f1;
        box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
        border-radius: 2px;
        padding: 10px;
        min-height: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #333;
        text-align: center;
        font-size: 40px;
        font-weight: 100;
        margin-bottom: 30px;
      }
    `}</style>
  </div>
)

const createLink = (href, text) => (
  <a href={href}>
    {text}
    <style jsx>{`
      a {
        color: #333;
        padding-bottom: 2px;
        border-bottom: 1px solid #ccc;
        text-decoration: none;
        font-weight: 400;
        line-height: 30px;
        transition: border-bottom .2s;
      }

      a:hover {
        border-bottom-color: #333;
      }
    `}</style>
  </a>
)

const Index = ({ isAuthenticated }) => (
  <div>
    {isAuthenticated && <SuperSecretDiv />}
    <div className='main'>
      <h1>Hello, friend!</h1>
      <p>
        This is a super simple example of how to use {createLink('https://github.com/zeit/next.js', 'next.js')} and {createLink('https://auth0.com/', 'Auth0')} together.
      </p>
      {!isAuthenticated && (
        <p>
          You're not authenticated yet. Maybe you want to <Link href='/auth/sign-in'>{createLink('/auth/sign-in', 'sign in')}</Link> and see what happens?
        </p>
      )}
      {isAuthenticated && (
        <p>
          Now that you're authenticated, maybe you should try going to our <Link href='/secret'>{createLink('/secret', 'super secret page')}</Link>!
        </p>
      )}
    </div>
    <style jsx>{`
      .main {
        max-width: 750px;
        margin: 0 auto;
        text-align: center;
      }

      h1 {
        font-size: 40;
        font-weight: 200;
        line-height: 40px;
      }

      p {
        font-size: 20px;
        font-weight: 200;
        line-height: 30px;
      }
    `}</style>
  </div>
)

Index.propTypes = {
  isAuthenticated: PropTypes.bool.isRequired
}

export default defaultPage(Index)
```
<!-- The index page is server-rendered. It checks if the user is authenticated or not and renders content based on the status. -->

인덱스 페이지는 서버에서 렌더링됩니다. 사용자가 인증되었는지 여부를 확인하고 상태를 기반으로 콘텐츠를 렌더링합니다.

<!-- The secret page too checks if the user is logged in and determines content based on the user's status.-->

[시크릿 페이지](https://github.com/auth0-blog/next2-auth0/blob/master/pages/secret.js)도 사용자가 로그인했는지 여부를 확인하고 사용자의 상태에 따라 콘텐츠를 결정합니다.

![Secret page unauthorized](https://cdn.auth0.com/blog/secret/notloggedin.png) *사용자가 로그인하지 않고도 시크릿 페이지에 액세스 할 수 없기 때문에 유효한 내용을 표시하지 않습니다.*

<!--Note: Nextjs exposes virtually everything to the client. Secrets and environment variables are leaked to the frontend. So if you want to perform an API call and you need to validate a token based on a secret, then you will have to run a custom express server so that your secret can be available only on the server. This also applies to other forms of operations that require loading some secret environment variables that the user of your app shouldn't have access to.-->

**참고**: Next.js는 사실상 모든 것을 클라이언트에 공개합니다. *시크릿*과 환경 변수가 프론트 엔드로 유출됩니다. 따라서 API 호출을 수행하고 시크릿을 기반으로 토큰의 유효성을 검사해야하는 경우 서버에서 *시크릿*만 사용할 수 있도록 [커스텀 고속 서버](https://github.com/zeit/next.js/tree/master/examples/custom-server-express)를 실행해야합니다. 이는 앱의 사용자가 액세스해서는 안되는 일부 시크릿 환경 변수를 로드해야하는 다른 작업 양식에도 적용됩니다.

## 끝맺음

<!-- With Next.js 2, the Github repo now has over 11,000 stars and we have seen lots of significant improvements & major upgrades from the initial version that was released last year. Kudos to the team behind this lovely tool and the JavaScript community for their continuous support. In fact, they already have plans for Next.js 3.-->

 **Next.js 2**를 통해 [Github 레포](https://github.com/zeit/next.js/)에는 현재 11,000개 이상의 별이 붙었으며 작년에 출시 된 초기 버전에서 많은 중요한 개선 및 주요 업그레이드를 하였습니다. 이 멋진 도구와 JavaScript 커뮤니티의 지속적인 지원에 대한 팀의 공로를 인정합니다. 사실 그들은 **Next.js 3**에 대한 계획을 가지고 있다고 합니다.

<!--Try out Next.js 2 and let me know what you think in the comments section!-->

Next.js 2를 써보시고 댓글란에 여러분의 의견을 공유해주세요.