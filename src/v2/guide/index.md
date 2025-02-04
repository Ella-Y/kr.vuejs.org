---
title: 시작하기
type: guide
order: 2
---

## Vue.js가 무엇인가요?

Vue(/vjuː/ 로 발음, **view** 와 발음이 같습니다.)는 사용자 인터페이스를 만들기 위한 **프로그레시브 프레임워크** 입니다. 다른 단일형 프레임워크와 달리 Vue는 점진적으로 채택할 수 있도록 설계하였습니다. 핵심 라이브러리는 뷰 레이어만 초점을 맞추어 다른 라이브러리나 기존 프로젝트와의 통합이 매우 쉽습니다. 그리고 Vue는 [현대적 도구](single-file-components.html) 및 [지원하는 라이브러리](https://github.com/vuejs/awesome-vue#components--libraries)와 함께 사용한다면 정교한 단일 페이지 응용프로그램을 완벽하게 지원할 수 있습니다.

Vue를 알아보기 전에 Vue에 대해 자세히 알고 싶다면 핵심 원칙과 샘플 프로젝트를 바탕으로 설명하는 <a id="modal-player"  href="#">비디오</a>를 만들었으니, 참고하시면 좋을 것 입니다.


이미 숙련된 프론트엔드 개발자이고 Vue를 다른 라이브러리/프레임워크와 비교하고 싶다면 [다른 프레임워크와의 비교](comparison.html)를 확인하십시오.

<div class="vue-mastery"><a href="https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/" target="_blank" rel="sponsored noopener" title="Free Vue.js Course">Vue Mastery의 무료 강의 보기</a></div>

## 시작하기

<a class="button" href="installation.html">설치</a>

<p class="tip">공식 가이드는 HTML, CSS 및 JavaScript에 대한 중간 수준의 지식을 전제로 하고 있습니다. 이제 막 프론트 엔드 개발에 대해 배우기 시작했다면 첫 번째 단계로 프레임워크를 시작하는 것은 좋은 생각이 아닙니다. 기본을 파악한 다음 다시 해보세요! 다른 프레임워크에 대한 사전 경험이 도움될 수 있지만 반드시 필요한것은 아닙니다.</p>

Vue.js를 시험해 볼 수 있는 가장 쉬운 방법은 [JSFiddle Hello World 예제](https://jsfiddle.net/chrisvfritz/50wL7mdz/)를 사용하는 것입니다. 브라우저의 새 탭에서 열어 본 후 몇 가지 기본 예제를 따라가십시오. 또는 단순히 <a href="https://gist.githubusercontent.com/chrisvfritz/7f8d7d63000b48493c336e48b3db3e52/raw/ed60c4e5d5c6fec48b0921edaed0cb60be30e87c/index.html" target="_blank" download="index.html"><code>index.html</code> 파일</a>을 만들고 Vue를 다음과 같이 포함할 수 있습니다.

``` html
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

또는:

```html
<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```


[설치](installation.html) 페이지에는 Vue를 설치하기 위한 옵션이 추가로 제공됩니다. 특히 Node.js 기반 빌드 도구에 아직 익숙하지 않으면 `vue-cli`로 시작하는 것을 권장하지 **않습니다.**

보다 인터랙티브한 학습을 원한다면, 언제든지 중지/재생 할 수 있는 스크린캐스트와 코드를 테스트 할 수 있는 환경를 제공해주는 [Scrimba의 튜토리얼 시리즈](https://scrimba.com/playlist/pXKqta)를 확인해보세요.

## 선언적 렌더링

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cQ3QVcr" target="_blank" rel="noopener noreferrer">Scrimba에서 레슨 받기</a></div>

Vue.js의 핵심에는 간단한 템플릿 구문을 사용하여 DOM에서 데이터를 선언적으로 렌더링 할 수있는 시스템이 있습니다.

``` html
<div id="app">
  {{ message }}
</div>
```
``` js
var app = new Vue({
  el: '#app',
  data: {
    message: '안녕하세요 Vue!'
  }
})
```
{% raw %}
<div id="app" class="demo">
  {{ message }}
</div>
<script>
var app = new Vue({
  el: '#app',
  data: {
    message: '안녕하세요 Vue!'
  }
})
</script>
{% endraw %}

첫 Vue 앱을 성공적으로 만들었습니다! 이것은 문자열 템플릿을 렌더링하는 것과 매우 유사하지만, Vue.JS 내부에서는 더 많은 작업을 하고 있습니다. 이제 데이터와 DOM이 연결되었으며 모든 것이 **반응형**이 되었습니다. 우리는 그것을 어떻게 확인할 수 있을까요? 브라우저의 JavaScript 콘솔을 열고 `app.message`를 다른 값으로 설정해 보십시오. 위 예제가 업데이트 변경된 값에 따라 업데이트되는 것을 볼 수 있습니다.

텍스트 보간 이외에도 다음과 같은 엘리먼트 속성을 바인딩할 수 있습니다.

``` html
<div id="app-2">
  <span v-bind:title="message">
    내 위에 잠시 마우스를 올리면 동적으로 바인딩 된 title을 볼 수 있습니다!
  </span>
</div>
```
``` js
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '이 페이지는 ' + new Date() + ' 에 로드 되었습니다'
  }
})
```
{% raw %}
<div id="app-2" class="demo">
  <span v-bind:title="message">
    내 위에 잠시 마우스를 올리면 동적으로 바인딩 된 title을 볼 수 있습니다!
  </span>
</div>
<script>
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '이 페이지는 ' + new Date() + '에 로드 되었습니다'
  }
})
</script>
{% endraw %}

여기서 우리는 새로운 것을 만났습니다. `v-bind` 속성은 **디렉티브** 이라고 합니다. 디렉티브는 Vue에서 제공하는 특수 속성임을 나타내는 `v-` 접두어가 붙어있으며 사용자가 짐작할 수 있듯 렌더링 된 DOM에 특수한 반응형 동작을 합니다. 기본적으로 "이 요소의 `title` 속성을 Vue 인스턴스의 `message` 속성으로 최신 상태를 유지 합니다."

다시 JavaScript 콘솔을 열고 `app2.message = '새로운 메시지'`라고 입력하면 HTML(이 경우에 `title` 속성)이 업데이트되었음을 다시 한번 확인할 수 있습니다.

## 조건문과 반복문

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQe4SJ" target="_blank" rel="noopener noreferrer">Scrimba에서 레슨 받기</a></div>

엘리먼트가 표시되는지에 대한 여부를 제어하는 것은 아주 간단합니다.

``` html
<div id="app-3">
  <p v-if="seen">이제 나를 볼 수 있어요</p>
</div>
```

``` js
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

{% raw %}
<div id="app-3" class="demo">
  <span v-if="seen">이제 나를 볼 수 있어요</span>
</div>
<script>
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
</script>
{% endraw %}

계속해서, Javascript 콘솔에 `app3.seen = false`를 입력하면, 메시지가 사라지는 것을 볼 수 있습니다.

이 예제는 텍스트와 속성뿐 아니라 DOM의 **구조**에도 데이터를 바인딩 할 수 있음을 보여줍니다. 또한 Vue 엘리먼트가 Vue에 삽입/업데이트/제거될 때 자동으로 [트랜지션 효과](transitions.html)를 적용할 수 있는 강력한 전환 효과 시스템을 제공합니다.

몇가지 디렉티브가 있습니다. 각 디렉티브마다 고유한 기능이 있습니다. 예를 들어 `v-for` 디렉티브는 배열의 데이터를 바인딩하여 Todo 목록을 표시하는데 사용할 수 있습니다.

``` html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```
``` js
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'JavaScript 배우기' },
      { text: 'Vue 배우기' },
      { text: '무언가 멋진 것을 만들기' }
    ]
  }
})
```
{% raw %}
<div id="app-4" class="demo">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
<script>
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'JavaScript 배우기' },
      { text: 'Vue 배우기' },
      { text: '무언가 멋진 것을 만들기' }
    ]
  }
})
</script>
{% endraw %}

콘솔에서, `app4.todos.push({ text: 'New item' })`을 입력하십시오. Todo 목록에 새 항목이 동적으로 추가 된것을 볼 수 있습니다.

## 사용자 입력 핸들링

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/czPNaUr" target="_blank" rel="noopener noreferrer">Scrimba에서 레슨 받기</a></div>

사용자가 앱과 상호 작용할 수 있게 하기 위해 우리는 `v-on` 디렉티브를 사용하여 Vue 인스턴스에서 메소드를 호출하는 이벤트 리스너를 추가 할 수 있습니다 :

``` html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">메시지 뒤집기</button>
</div>
```
``` js
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: '안녕하세요! Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
{% raw %}
<div id="app-5" class="demo">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">메시지 뒤집기</button>
</div>
<script>
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: '안녕하세요! Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
</script>
{% endraw %}

이 방법은 직접적으로 DOM을 건드리지 않고 앱의 상태만을 업데이트합니다. 모든 DOM 조작은 Vue에 의해 처리되며 작성한 코드는 기본 로직에만 초점을 맞춥니다.

Vue는 또한 양식에 대한 입력과 앱 상태를 양방향으로 바인딩하는 `v-model` 디렉티브를 제공합니다.

``` html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
``` js
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: '안녕하세요 Vue!'
  }
})
```
{% raw %}
<div id="app-6" class="demo">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
<script>
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: '안녕하세요 Vue!'
  }
})
</script>
{% endraw %}

## 컴포넌트를 사용한 작성방법

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQVkA3" target="_blank" rel="noopener noreferrer">Scrimba에서 레슨 받기</a></div>

컴포넌트 시스템은 Vue의 또 다른 중요한 개념입니다. 이는 작고 독립적이며 재사용할 수 있는 컴포넌트로 구성된 대규모 애플리케이션을 구축할 수 있게 해주는 추상적 개념입니다. 생각해보면 거의 모든 유형의 애플리케이션 인터페이스를 컴포넌트 트리로 추상화할 수 있습니다.

![컴포넌트 트리](/images/components.png)

Vue에서 컴포넌트는 미리 정의된 옵션을 가진 Vue 인스턴스 입니다. Vue에서 컴포넌트를 등록하는 방법은 간단합니다.

``` js
// todo-item 이름을 가진 컴포넌트를 정의합니다
Vue.component('todo-item', {
  template: '<li>할일 항목 하나입니다.</li>'
})

var app = new Vue(...)
```

이제 다른 컴포넌트의 템플릿에서 이 컴포넌트를 추가할 수 있습니다.

``` html
<ol>
  <!-- todo-item 컴포넌트의 인스턴스 만들기 -->
  <todo-item></todo-item>
</ol>
```

그러나 이것은 `todo-item` 컴포넌트를 사용할 때마다 똑같은 텍스트를 렌더링할뿐 무언가가 부족합니다. 부모 영역의 데이터를 자식 컴포넌트에 전달할 수 있어야 합니다. [prop](components.html#Props)을 전달받을 수 있도록 `todo-item` 컴포넌트의 정의를 수정해봅시다.

``` js
Vue.component('todo-item', {
  // 이제 todo-item 컴포넌트는 "prop" 이라고 하는
  // 사용자 정의 속성 같은 것을 입력받을 수 있습니다.
  // 이 prop은 todo라는 이름으로 정의했습니다.
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
```

이제 `v-bind`를 사용하여 각각의 반복되는 `todo-item` 컴포넌트에 전달할 수 있습니다.

``` html
<div id="app-7">
  <ol>
    <!--
      이제 각 todo-item 에 todo 객체를 제공합니다.
      화면에 나오므로, 각 항목의 컨텐츠는 동적으로 바뀔 수 있습니다.
      또한 각 구성 요소에 "키"를 제공해야합니다 (나중에 설명 됨).
     -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
```
``` js
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
})
```
{% raw %}
<div id="app-7" class="demo">
  <ol>
    <todo-item v-for="item in groceryList" v-bind:todo="item" :key="item.id"></todo-item>
  </ol>
</div>
<script>
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
})
</script>
{% endraw %}

이것은 인위적으로 만든 예시이지만, 우리는 앱을 두 개의 더 작은 단위로 나눌 수 있었고, 자식을 props 인터페이스를 통하여 부모로부터 합리적인 수준으로 분리할 수 있었습니다. 이제 앞으로는 부모 앱에 영향을 주지 않으면서 `<todo-item>` 컴포넌트를 더 복잡한 템플릿과 로직으로 더욱 향상시킬 수 있을 것입니다.

대규모 애플리케이션에서는 개발을 보다 쉽게 관리 할 수 있도록 전체 앱을 컴포넌트로 나누는 것이 필수적입니다. [가이드의 뒷부분](components.html)에서 컴포넌트에 대해 자세히 설명하겠지만 여기서는 컴포넌트를 사용한 앱의 모습이 어떻게 구성될지에 대한 (가상의) 예를 작성하겠습니다.

``` html
<div id="app">
  <app-nav></app-nav>
  <app-view>
    <app-sidebar></app-sidebar>
    <app-content></app-content>
  </app-view>
</div>
```

### 사용자 정의 엘리먼트와의 관계

Vue 컴포넌트는 [Web Components Spec](http://www.w3.org/wiki/WebComponents/)의 일부인 **사용자 지정 엘리먼트** 와 매우 유사하다는 것을 눈치 챘을 수 있습니다. Vue의 컴포넌트 구문은 스펙 이후 느슨하게 모델링 되었기 때문입니다. 예를 들어 Vue 컴포넌트는 [Slot API](https://github.com/w3c/webcomponents/blob/gh-pages/proposals/Slots-Proposal.md)와 `is` 특수 속성을 구현합니다. 그러나 몇가지 중요한 차이가 있습니다.

1. Web Components Spec은 최종안이 정해졌지만 모든 브라우저들이 기본적으로 구현되는 것은 아닙니다. 현재 사파리 10.1+, 크롬 54+ 그리고 파이어폭스 63+ 기본적으로 Web Components를 지원합니다. 이에 비해 Vue 컴포넌트는 지원되는 모든 브라우저 (IE 9 이상)에서 폴리필을 필요로 하지 않으며 일관된 방식으로 작동합니다. 필요한 경우 Vue 컴포넌트는 기본 사용자 정의 엘리먼트 내에 래핑할 수 있습니다.

2. Vue 컴포넌트는 컴포넌트간 데이터의 흐름을 비롯해, 사용자 정의 이벤트와 통신, 빌드 도구와의 통합 등 기본 사용자 지정 엘리먼트에서 사용할 수 없엇던 중요한 기능을 제공합니다.

Vue는 내부적으로 사용자 정의 엘리먼트를 사용하지 않지만, 사용자 정의 엘리먼트로 사용 또는 배포하는 경우에는 [뛰어난 상호운용성](https://custom-elements-everywhere.com/#vue)을 가집니다. Vue CLI는 자기자신을 네이티브 커스텀 엘리먼트로서 등록하는 Vue 컴포넌트의 빌드도 지원하고 있습니다.

## 더 해야할 것은 무엇인가요?

우리는 Vue.js 코어의 가장 기본적인 기능을 간략하게 소개했습니다. 이 가이드의 나머지 부분에서 더 자세한 세부 내용이 포함된 다른 고급 기능에 대해 다룰 예정이므로 꼭 읽어보시기 바랍니다.

<div id="video-modal" class="modal"><div class="video-space" style="padding: 56.25% 0 0 0; position: relative;"><iframe src="https://player.vimeo.com/video/247494684?dnt=1" style="height: 100%; left: 0; position: absolute; top: 0; width: 100%; margin: 0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script><p class="modal-text">Video by <a href="https://www.vuemastery.com" target="_blank" rel="sponsored noopener" title="Vue.js Courses on Vue Mastery">Vue Mastery</a>. Watch Vue Mastery’s free <a href="https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/" target="_blank" rel="sponsored noopener" title="Vue.js Courses on Vue Mastery">Intro to Vue course</a>.</div>
