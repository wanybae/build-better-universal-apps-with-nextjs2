# Next.js 2.0을 이용하여 보다 낳은 Universal JavaScript 앱을 만들기
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

 `next build`로 앱을 빌드하고 앱을 시작하면, **Next.js 2.0**은 JavaScript 화일과 기타 리소스들(assets)을 이뮤터블 리소스로서 서빙하게 됩니다. This simply means that once the browser has downloaded any immutable asset, if you reload the browser page, your browser won't try to load these assets from the server again.

Another gain for performance and speed. Whoop! Whoop!

### 7. Custom Babel and Webpack Configurations

Next.js 2 is fully extensible. You have complete control over Babel's and Webpack's configuration. For example, if you want to extend Babel, you can simply define a .babelrc file at your app's root and apply next/babel preset. With that, you include whatever babel plugins you need like so:

```
{
  "presets": ["next/babel"],
  "plugins": ["transform-flow-strip-types"]
}
```
Check out this working example.

sample .babelrc file

To extend the usage of Webpack in Next.js, you can create a next.config.js file in the root of your project's directory. Once you have that, you can define a function in the Node.js module like so:

```
module.exports = {
  webpack: (config, { dev }) => {
    // Perform customizations to config

    // Important: return the modified config
    return config
  }
}
```
Note: The next.config.js file is a regular Node.js module.

8. Composed CSS support

Before now, next/css was the default CSS-in-JS solution for Next.js. In Next.js 2, it has been deprecated in favor of styled-jsx, a Babel transformation that provides full, scoped and component-friendly CSS support for JSX (rendered on the server or the client).

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

In the code example above, you can see how it provides scoped support for this JSX-written component.

9. Isolating React From Next

Before now, Next.js shipped with React. All you needed to do was:


`npm install next --save`
In Next.js 2.0, you now need to bring in next with react and react-dom like so:


`npm install --save next react react-dom`
This creates opportunity for you to use other React API implementations such as Preact. It also allows you to update React independently of Next.js.

9. Practical Examples of Backend Integrations

Many developers have been helping out in providing examples on how to integrate Next.js with several backend technologies.

Hapi Integration
Express Integration
Koa integration
10. Availability of Learning Platforms

It's amazing to see that in a short time that Next.js has been in existence, lots of examples have been amassed and there is a learning platform that the Next.js team approves of. With the release of Next.js 2, we have:

About 48 examples of integrating Next.js with Apollo, Inferno, Preact and ways of achieving different common functionalities with Next.js
learnnextjs.com, built by Arunoda Susiripala
Learn Next.js learnnextjs.com Landing page

Logged In view learnnextjs.com Logged in view

Oh, the UI and Backend for learnnextjs.com is open-source. This presents another opportunity to learn Next.js 2.0 by going through its source code.

## Enter Next.js 2.2.0

**Next.js 2.2.0** was tagged yesterday. It comes bundled with some nice changes:

* CDN support: You might want to upload all your static files to a CDN, including build files. Now, you can serve Next.js static assets via a CDN. All you need is to expose the following option in next.config.js like so:
```
const isProd = process.NODE_ENV === 'production'
module.exports = {
  // You may only need to add assetPrefix in the production.
  assetPrefix: isProd? 'https://cdn.mydomain.com' : ''
}
```

More information can be found here.

* ETag support for server rendered pages : The ETag HTTP response header is an identifier for a specific version of a resource found at a URL. It allows caches to be more efficient, and saves bandwidth, as a web server does not need to send a full response if the content has not changed. However, if the content has changed, etags are useful to help prevent simultaneous updates of a resource from overwriting each other. Etags are otherwise known as fingerprints used for tracking resource changes on the server.

In Next.js, all server-rendered pages now support Etags.

* New official examples on how to use Next.js with other technologies:
  * Material UI
  * Socket.io
  * Semantic UI
  * Firebase

More information can be found in the [release notes](https://github.com/zeit/next.js/releases/tag/2.2.0).

## Aside: Authenticating a Next.js 2.0 App with Auth0

Auth0 issues JSON Web Tokens on every login for your users. This means that you can have a solid identity infrastructure, including single sign-on, user management, support for social identity providers (Facebook, Github, Twitter, etc.), enterprise identity providers (Active Directory, LDAP, SAML, etc.) and your own database of users with just a few lines of code.

We can easily set up authentication in a Next.js 2.0 apps by using the Lock Widget. If you don't already have an Auth0 account, sign up for one now. Navigate to the Auth0 management dashboard, click on `New client` by the right hand side, select Regular Web App from the dialog box and then go ahead to the `Settings` tab where the client ID, client Secret and Domain can be retreived.

Note: Make sure you set the `Allowed Callback URLs` to `http://localhost:3000/` or whatever url/port you are running on. Also set the `Allowed Origins (CORS)` to `http://localhost:3000/` or whatever domain url you are using, especially if it is hosted.

Authentication in a Next.js app could be a little complicated because you have to ensure that the server-rendered pages are authenticated, meaning they need to have access to the token.

In the example below, the token returned from Auth0 is stored in LocalStorage and also as a cookie.

Check out [the completed app on Github](https://github.com/auth0-blog/next2-auth0).

utils/auth.js

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
utils/lock.js

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
Grab the token and secret from Auth0 as it returns to the callback which is the signed-in page, save it and redirect to the index page.

![Signed in](https://cdn.auth0.com/blog/signedin/authenticated.png) Secret page shows that the user is signed in and can access it

pages/index.js

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
The index page is server-rendered. It checks if the user is authenticated or not and renders content based on the status.

The secret page too checks if the user is logged in and determines content based on the user's status.

![Secret page unauthorized](https://cdn.auth0.com/blog/secret/notloggedin.png) Not displaying valid content because the user cant access the secret page without signing in

Note: Nextjs exposes virtually everything to the client. Secrets and environment variables are leaked to the frontend. So if you want to perform an API call and you need to validate a token based on a secret, then you will have to run a custom express server so that your secret can be available only on the server. This also applies to other forms of operations that require loading some secret environment variables that the user of your app shouldn't have access to.

## Conclusion

With Next.js 2, the Github repo now has over 11,000 stars and we have seen lots of significant improvements & major upgrades from the initial version that was released last year. Kudos to the team behind this lovely tool and the JavaScript community for their continuous support. In fact, they already have plans for Next.js 3.

Try out Next.js 2 and let me know what you think in the comments section!