---
layout: default
title: Vue.js
parent: Web Tech
nav_order: 9
---

#  Vue.js
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

### Vue-CLI
{:.bigger}

애플리케이션에 필요한 요소들을 대화형 커맨드로 쉽게 설치하도록 도와준다.

##### 설치
{:.bigger}

```js
$ npm i -g @vue/cli
$ vue --version

$ npm i -g @vue/cli-init
//@vue/cli-init은 2.x Template을 가져오기 위한 vue init기능을 제공.

$ vue init webpack my-project
```

##### 생성
{:.bigger}

```js
$ vue create <project-name>
```
<div  class="code-example narrow bg" markdown="1">
 Please pick a preset : Manually select features<br>
 check the features needed for your project:<br>
 <input type="radio" id="babel" checked><label for="babel"> Babel</label><br>
 <input type="radio" id="typescript"><label for="typescript"> TypeScript</label><br>
 <input type="radio" id="pwa"><label for="pwa"> Progressive web App (PWA) Support</label><br>
 <input type="radio" id="router" checked><label for="router"> Router</label><br>
 <input type="radio" id="vuex" checked><label for="vuex"> Vuex</label><br>
 <input type="radio" id="css" checked><label for="css"> CSS Pre-processors</label><br>
 <input type="radio" id="linter" checked><label for="linter"> Linter / Formatter</label><br>
 <input type="radio" id="unit"><label for="unit"> Unit Testing</label><br>
 <input type="radio" id="e2e"><label for="e2e"> E2E Testing</label><br>
</div>

--- 

### Vue
{:.bigger}

- 오픈소스 자바스크립트 프레임웍
- 반응형 애플리케이션 쉽게 만들수 있는 기능 제공
- 쉽고 유연한 데이터 바인딩
- 재사용할 수 있는 컴포넌트 제공

> vue create `f` irstapp `--default` <br>
`f` 소문자(대문자 안됨)<br>
`--default` babel, eslint적용해 생성한다는 것<br>
{:.list}

- babel : 구형 브라우저가 지원하지 않는 자바스크립트를 최신버전을 적용할 수 있도록 해줌
- eslint : 구문에러, 코드 품질


##### 기본코드
{:.bigger}

```html
<!DOCTYPE html>
<html>
<body>
<div id="app">
  <h1>{{ message }}</h1>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.11/dist/vue.min.js"></script>
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
<script src="https://unpkg.com/vuex@3.5.1/dist/vuex.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lodash@4.17.5/lodash.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/axios@0.17.1/dist/axios.min.js"></script>
<script>
  var app = new Vue({
    el: '#app',
    data: {
      message: 'Hello Vue.js!'
    }
  })
</script>
</body>
</html>
```

```html
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

##### 라이프 사이클
{:.bigger}

- `beforeCreate`{:.property} 가장 먼저 실행
- `created`{:.property}  
  > 아직까지 DOM에는 추가되지 않은 상태<br>
  data에 직접 접근이 가능하기 때문에, 컴포넌트 초기에 외부에서 받아온 값들로 data를 세팅해야 하거나 이벤트 리스너를 선언해야 한다면 이 단계에서 하는 것이 가장 적절<br>
  {:.list}
- `beforeMount`{:.property} 첫 렌더링이 일어나기 직전에 실행
- `mounted`{:.property} 
  > 컴포넌트, 템플릿, 렌더링된 돔에 접근할 수 있다<br>
  모든 하위 컴포넌트가 마운트된 상태를 보장하지는 않는다<br>
  서버렌더링에서는 호출되지 않는다<br>
  부모와 자식 관계의 컴포넌트에서 우리가 생각한 순서로 mounted가 발생하지 않는다는 점<br>
  Created훅은 부모→자식의 순서로 실행되지만 mounted는 그렇지 않는다<br>
  {:.list}
- `beforeUpdate`{:.property} 
  > 컴포넌트의 데이터가 변하여 업데이트 사이클이 시작될때 실행 <br>
  정확히는 돔이 재 렌더링되고 패치되기 직전에 실행<br>
  {:.list}
- `updated`{:.property} 
  >  컴포넌트의 데이터가 변하여 재 렌더링이 일어나 후에 실행<br>
  돔이 업데이트 완료된 상태이므로 돔 종속적인 연산을 할 수 있다. 그러나 여기서 상태를 변경하면 무한루프에 빠질 수 있다. <br>
  모든 자식 컴포넌트의 재 렌더링 상태를 보장하지는 않는다.<br>
  {:.list}
- `beforeDestroy`{:.property} 
  > 해체(뷰 인스턴스 제거)되기 직전에 호출<br>
  서버 렌더링시 호출되지 않는다.<br>
  {:.list}
- `destroyed`{:.property} 
  > 해체(뷰 인스턴스 제거)된 후에 호출<br>
  Vue 인스턴스의 모든 디렉티브가 바인딩 해제 되고 모든 이벤트 리스너가 제거되며 모든 하위 Vue 인스턴스도 삭제된다. <br>
  서버 렌더링시 호출되지 않는다.<br>
  {:.list}

##### 문자열
{:.bigger}

보간법 : **{** **{** message **}** **}**


##### 속성
{:.bigger}

###### v-bind 디렉티브
{:.bigger}

  ```html
  <div v-bind:id="dynamicId"></div> 

  <!--JavaScript 표현식 사용-->
  <div v-bind:id="'list-' + id"></div>
  ```
  
  ```html
  <a :[attributeName]="url"> ... </a> 
    <a :href="url"> ... </a>
  <a @[eventName]="doSomething"> ... </a>
    <a @click="doSomething"> ... </a>

  <!-- shorthand with dynamic argument (2.6.0+) -->
  <a :[key]="url"> ... </a>
    <a @[event]="doSomething"> ... </a>
  ```

  - :src
  - :href
  - :class
  - :style
  - :key

###### v-model
{:.bigger}

- 양방향 데이터 바인딩 
- Form 태그 : input / checkbox / textarea / select 엘레먼트의 속성형태로 사용
> `v-model.trim` : 좌우 공백 제거 <br>
`v-model.number` : 데이타타입 Number <br>
`v-model.lazy` <br>
`v-model.trim.lazy` <br>
{: .list}



##### 조건문
{:.bigger}

- `v-if`{:.property} 
- `v-else`{:.property} 
- `v-else-if`{:.property} 
- `v-show`{:.property} 특정 조건에서 보여지지 않게 하려면 (`display: none`{:.special} 속성으로 표시)

```js
<p v-if="seen">이제 나를 볼 수 있어요</p>
```


##### 반복문
{:.bigger}

**v-for**

```js
<div v-for="(item, index) in array" :key="index">{{ item }}</div>
```

> `item` 하나의 데이터<br>
`array` 데이터 집합 <br>
`:key` item의 한속성 <br>
{: .list}

##### computed
{:.bigger}

- 데이터 조작하는 데 유용함
- data객체 내 프로퍼티가 변화가 발생할 때마다 반응하도록 설정
- <i class="material-icons text-purple-100">code</i> [테스트 코드](https://github.com/hyojinni/blog/blob/master/code/vueComputed.html)

##### 이벤트 수식어
{:.bigger}

- `event.stopPropagation()` 이벤트 버블링 중지
- `event.preventDefault()` submit버튼 클릭하면 서버로 form데이터가 바로 전송되지 않게 한다.
- `@click.stop`
- `@click.once` 한번만 이벤트 발생
- `@click.self` 자신만 이벤트 발생
- `@click.self.capture`


##### component
{:.bigger}

```js
Vue.component( '컴포넌트이름', {
  template: 'html코드들'
})
```

```js
import `OurHeader` form './components/header.vue'
import `OurBody` form './components/body.vue'

export default {
  name: 'app',
  components: {OurHeader, OurBody}
}
```

**전역 컴포넌트**

> `main.js`에 등록
{: .list}

```js
import ChildComponent from './components/ChildComponent'
Vue.component('child-component', ChildComponent)
```
'child-component' Vue 인스턴스

**지역 컴포넌트**

> `app.vue`에 등록
{: .list}

```js
import ChildComponent from './components/ChildComponent'

export default {
  components : {
    'child-component': ChildComponent
  }
}
```

##### props
{:.bigger .mt-6}

> 하나의 컴포넌트에서 다른 컴포넌트로 데이터를 전달할 경우
{: .list}

- `props` : 부모 → 자식
- `$emit`, `on` : 자식 → 부모
- `eventBus`를 이용해 데이터 전달 : 부모 ≠ 자식, 발행자와 구독자 패턴으로 컴포넌트간의 전달
  - 발행부분 : emit() 메서드를 이용
  - 발행된 이벤트 구독하는 부분은  on()메서드 
  - cdn
  ```js
    const EventBus = new Vue()
  ```
  - Vue/Cli 이용
  ```js
    import Vue from 'Vue'
    const EventBus = new Vue()
    export default EventBus
  ```
  - 발행된 이벤트를 삭제 or 한번만 구독하고 싶을 경우
    ```js
    EventBus.$off('event-name') //삭제
    EventBus.$once('event-name', payload => {});
  ```


부모컴포넌트
```js
<child :props-name="부모가 전달할 데이터"></child>

//
<child v-on:sendmessage="receivemessage"></child>
```


자식컴포넌트
```js
props: [props-name]

//
methods: {
  sendmessage() {
    this.$emit('sendmessage', this.message);
  }
}
```


##### slot
{:.bigger .mt-6}
부모가 자녀에게 콘텐츠를 제공
- unnamed slot
- named slot
- scoped slot : 템플릿을 이용하는 재사용이 가능한 특별한 슬롯(자녀 → 부모 데이터 전달)
  ```js
  //부모
  <child>
    <template slot-scope="childData">
    ...
    </template>
  </child>

  //자녀
  <slot :childData="sendData">
  </slot>
  ```


---

### Vue Router
{:.bigger}

##### install(npm)
{:.bigger}

```js
npm install vue-router
```

##### 사용법
{:.bigger}

**router연결** `root/routes/index.js`

```js
import Vue from 'vue'
import VueRouter from 'vue-router'
import Main from '../views/Main.vue'
import NewsView from '../views/NewsView.vue'

Vue.use(VueRouter)

export const router = new VueRouter({
  routes: [
    {
      path: '/',
      component: Main
    },
    {
      path: '/notice',
      component: Notice
    }
  ]
})
```

**router등록** `root/src/main.js`

```js
import Vue from 'vue'
import App from './App.vue'
import { router } from '../routes/index.js'

Vue.config.productionTip = false

new Vue({
  render: h => h(App),
  router, // router: router 와 같다
}).$mount('#app')
```

**이동** `root/src/App.vue`

선언적 방식

```html
<template>
  <div>
    
    <router-view></router-view>

  </div>
</template>

<template>
  <div id="app">
    <router-link to="/">main</router-link> |
    <router-link to="/notice">notice</router-link>

    <!-- 여기에 라우터가 컴포넌트를 그린다 -->
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
}
</script>
```

프로그래밍적 방식

```html
<template>
  <div>
    
    <router-view></router-view>

  </div>
</template>

<template>
  <div id="app">
    <span @click="go('/')">main</span>
    <span @click="go('/notice')">news</span>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    go (url) { 
      this.$router.push(url)
    }
  }
}
</script>
```

---

### vuex
{:.bigger}

- 애플리케이션의 모든 컴포넌트에 대한 중앙 집중식 저장소 역활 및 관리
- 부모는 자식에서 props의 방법
- 자식은 부모에게 Emit event의 방법
- 형제 컴포넌트간 데이터를 주고 받으려면 EventBus를 활용


##### install(npm)
{:.bigger}

```js
npm install vuex --save
```

##### 핵심 개념
{:.bigger}

-  `State`{:.property} 컴포넌트 간에 공유할 데이터
    > 프로젝트에서 공통으로 사용할 변수를 정의한다.<br>
    프로젝트 내의 모든 곳에서 참조 및 사용이 가능<br>
    state를 통해 각 컴포넌트에서 동일한 값을 사용할 수 있다.
    {:.list}

    ```js
      this.$store.state.items

     computed: { ...mapState({ items: state => state.items, }),}
    ```

- `Getters`{:.property} 연산된 state 값을 접근하는 속성<br>
    > `computed()`처럼 미리 연산된 값을 접근하는 속성<br>
    각 Components의 계산된 속성(computed)의 공통 사용 정의<br>
    하위 모듈의 getters를 불러오기 위해서는 this.$store.getters["경로명/함수명"];
    {:.list}

    ```js
    this.$store.getters["경로명/함수명"];

    computed: { ...mapGetters({ doneCount: 'item/doneTodosCount' }) }
    ```
    
- `Mutations`{:.property} 변수를 조작하는 함수를 의미<br> 
    > state를 변경시키는 역활<br>
    동기처리를 한다.<br>
    `commit('함수명', '전달인자')`으로 동작, 항상 첫번째 인자로 state를 가져온다.
    {:.list}

    ```js
    this.$store.commit('경로명/함수명')

    computed: { ...mapMutations({ add: 'item/increment' })}
    //this.add()를 this.$store.commit('item/increment')에 매핑
    ```

- `Actions`{:.property} 화면에서 발생하는 이벤트 또는 사용자의 입력<br>
  > Mutations를 실행시키는 역활<br>
    actions 내에 함수 형태로 작성<br>
    비동기 처리이기 때문에 콜백함수로 주로 작성<br>
    함수 형태로 작성<br>
    `.dispatch('함수명', '전달인자')`로 actions 호출, 비동기 로직 수행 후<br>
    `.commit()`으로 vuex store의 mutations 호출.<br>
    {:.list}

    ```js
    this.$store.commit('경로명/함수명')

    methods: { ...mapActions({ add: 'item/increment' })}
    // this.add()를 this.$store.dispatch('item/increment')에 매핑
    ```

### 용어정리
{:bigger}

- Event Bus : 상위 - 하위 관계가 아닌 컴포넌트 간의 통신을 위해 Event Bus를 활용할 수 있다.

---
## 참고링크
- [[PowerShell] 이 시스템에서 스크립트를 실행할 수 없으므로 파일을 로드할 수 없습니다.](https://dog-developers.tistory.com/183){:target="_blank"}
- [Vuex 주요 기술 요소](https://ict-nroo.tistory.com/107){:target="_blank"}
- [Vuex에서 Store활용 방법](https://ux.stories.pe.kr/149){:target="_blank"}
- [Vue.js 최근소식들5 — Vue 3 Alpha 버전 시작 등](https://medium.com/@jeongwooahn/Vue.js 최근소식들5 — Vue 3 Alpha 버전 시작 등/){:target="_blank"}
- [고양이도 할 수 있는 Vue.js](https://rintiantta.github.io/jpub-vue/){:target="_blank"}
- [Vue 라이프사이클 이해하기](https://wormwlrm.github.io/2018/12/29/Understanding-Vue-Lifecycle-hooks.html){:target="_blank"}
- [Vue CLI3 tutorial](https://kdydesign.github.io/2019/04/22/vue-cli3-tutorial/){:target="_blank"}
- [Vue Router](https://router.vuejs.org/kr/){:target="_blank"}
- [Vue Router](https://velog.io/@skyepodium/Vue-Router-fijr95dn4j){:target="_blank"}
- [예제로 배우는 Vue.js]