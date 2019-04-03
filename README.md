# frontend

- webpack
- gulp
- babel
- es6
- ajax
- jquery
- axios
- vuejs
- vue-router

## webpack

JavaScript 모듈화 도구.

### 모듈 정의와 모듈 사용

모듈을 작성하고 다음과 같이 module.exports 속성에 외부에 배포할 모듈을 전달해 모듈을 정의한다.

```javascript
module.exports = {message: 'webpack'};
```

모듈을 사용할 때는 모듈을 로딩하는 파일의 require() 함수에 로딩할 모듈의 경로를 전달한다. 
다음 코드는 모듈을 정의하는 examplemodule.js 파일을 사용하는 예이다.

```javascript
alert(require('./examplemodule').message);
```

두 개의 모듈을 합쳐서 사용하는 예이다.

hello.js
```javascript
module.exports = 'Hello';
```

world.js
```javascript
module.exports = 'World';
```

greeting.js
```javascript
var greeting = require('./hello') + require('./world');
module.exports = greeting;
```

두 모듈을 합친 greeting 모듈을 로딩해 브라우저에서 경고 메시지를 나타내는 app.js
```javascript
alert(require('./greeting'));
```

모듈을 정의하고 사용하도록 로딩하는 방법은 어렵지 않다.
다만 모듈로 만든 파일은 바로 웹 페이지에 넣어 브라우저에서 실행할 수 없다.
webpack을 통해 컴파일해 브라우저에서 실행할 수 있는 형태로 바꿔야한다.

### webpack 사용 방법

webpack은 Node.js가 설치된 환경에서 실행된다.
Node.js를 사용하는 환경에서 webpack을 설치하고 모듈을 컴파일하는 방법은 다음과 같다.

#### 설치와 컴파일

webpack은 다음과 같은 명령어로 설치할 수 있다.

```
npm install webpack -g
```

webpack이 설치되면 다음과 같이 webpack [엔트리 파일 경로] [번들 파일 경로] 형식으로 명령어를 실행해 모듈을 컴파일한다.

```
webpack ./entry.js bundle.js
```
