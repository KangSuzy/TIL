# Vue_Instance

Vue 로 화면을 개발하기 위해 필수적으로 생성해야하는 **기본 단위**

## 인스턴스 생성

```html
...
  <body>
    <!-- CDN 추가 -->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>

    <div id="app">{{ message }}</div>

    <script>
      new Vue({
        el: '#app',
        data: {
          message: 'Hello Vue',
        },
      })
    </script>
  </body>
</html>
```

**인스턴스를 생성**하기 위해서는 **new Vue** 라는 생성자를 호출해야한다

생성자란 객체를 새로 생성할 때 자주 사용하는 옵션과 기능들을 미리 특정 객체에 저장해놓고

새로운 객체를 생성할 때 기존에 포함된 기능과 더불어 기존 기능을 쉽게 확장하여 사용하는 방법 !

el, data 외에도 template, methods, created 등 여러 생성자의 속성이 존재한다

---

## 인스턴스의 유효범위

Vue 인스턴스는 생성 후 HTML 의 범위내에서만 옵션 속성이 적용되는데 이를 유효범위라 한다

**인스턴스의 유효범위** 는 **el속성** 에 의해 정해진다

인스턴스가 생성된 후 화면에 적용되는 순서는 아래랑 같다 !

1. Vue 라이브러리 로딩
2. 인스턴스 객체 생성
3. 특정화면에 element 인스턴스를 연결
4. 인스턴스의 내용이 element 에 적용
5. 적용된 화면이 사용자에게 노출

```html
<!-- 아래 코드는 인스턴스 범위를 벗어났기 때문에 message 가 출력되지 않는다 -->

<div id="#app"></div>
{{ message }}
```

## 인스턴스의 라이프 사이클

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcBRP50%2FbtqEANhTvvV%2FAPUj8IaEefht8d4YEcpxo0%2Fimg.png">

Vue 인스턴스는 인스턴스 생성 중에 인스턴스의 생성에 따라 호출할 수 있는 속성들인 라이프 사이클 속성들이 있다

```html
<html>
  <head>
    <title>Vue Instance Lifecycle</title>
  </head>
  <body>
    <div id="app">
      {{ message }}
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>
    <script>
      new Vue({
        el: '#app',
        data: {
          message: 'Hello Vue.js!',
        },
        beforeCreate: function () {
          console.log('beforeCreate')
        },
        created: function () {
          console.log('created')
        },
        mounted: function () {
          console.log('mounted')
        },
        updated: function () {
          console.log('updated')
        },
      })
    </script>
  </body>
</html>
```

결과가 아래와 같이 출력되는데 인스턴스의 data 값이 변경된 적이 없기 때문에 실행되지않는다

update 가 출력되기 위해선 mounted 단계의 data 를 수정하면 된다

```
beforecreate
create
mounted
```
