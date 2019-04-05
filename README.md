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
브라우저에서 파일 단위 모듈 시스템을 사용하기 쉽지않아, 모듈을 IIFE 스타일로 변경해주는 과정 뿐만 아니라 하나의 파일로 묶어 네트워크 비용을 최소화할 수 있는 방법이 웹 프론트엔드 개발 과정에 필요하다.

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

### entry

webpack 의존성의 시작점.

webpack은 entry를 통해서 필요한 모듈을 로딩하고 하나의 파일로 묶는다.

```javascript
module.exports = {
  entry: {
    main: './src/app.js'
  }
}
```

### output

entry에 설정한 자바스크립트 파일을 시작으로 의존되어 있는 모든 모듈을 하나로 묶는다.
번들된 결과물의 위치는 output에 기록한다.

```javascript
module.export = {
  entry: {
    main: './src/app.js'
  },
  output: {
    filename: 'bundle.js',
    path: './dist'
  }
}
```

html파일에서 번들된 파일을 로딩하게 작성해준다.

```html
<body>
  <script src="./dist/bundle.js"></script>
</body>
```

### loader

webpack은 모든 파일을 모듈로 관리한다. 자바스크립트 뿐만아니라 이미지, 폰트, 스타일시트도 모두 모듈로 관리한다. 그러나 webpack은 자바스크립트 밖에 모른다. 자바스크립트가 아닌 파일을 webpack이 이해할 수 있게 변환을 해줘야하는데 로더가 이러한 역할을 한다.

## 참고자료
1. https://d2.naver.com/helloworld/0239818
2. http://blog.jeonghwan.net/js/2017/05/15/webpack.html
