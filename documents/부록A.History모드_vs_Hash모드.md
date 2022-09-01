# [Vue router] Hash 모드 vs History 모드
```js
const router = new VueRouter({
  mode: 'history', // or mode: 'hash' (default 가 hash 임)
  routes: [...]
})
```
## 시각적 차이
두 모드의 두드러지는 차이점은 url 상의 '#' 존재 유무.

- Hash 모드 : `http://baseUrl/#/componentUrl`
- History 모드 : `http://baseUrl/componentUrl`\
  위의 두 url 모두 같은페이지를 가리킨다.

## 기능적 차이

예를 들어 `http://localhost:8080/#/page` 에 접속한다 가정하자 (History 모드에선 '...8080/page')\
=> 위 url은 'localhost:8080/ 페이지에서 page 컴포넌트로 가주세요~' 이다.

hash 모드에선 브라우저에 위 url을 그대로 입력해도 똑같은 페이지가 뜬다.
그러나 history 모드에선 `http://localhost:8080/page` 를 입력하면 404가 뜬다.
- vue 는 SPA 이므로 root 컴포넌트를 찾아놓고, 라우터를 이용해서 내부 컴포넌트들을 찾아다닌다.
    - hash 모드에선 '#'라는 기준이 있어서 어디부터 컴포넌트 url인지 명확하다.
    - history모드는 브라우저에게 'root 컴포넌트 url + /page' 라는 등록되지 않은 root 컴포넌트를 찾아달라고 부탁하는 꼴.

## '#'이 보기 싫지만, 새로고침해도 페이지가 제대로 뜨면 좋겠어요
#을 보지 않으려면 history모드를 사용해야한다.\
history 모드를 사용하면서 url 입력이 정상 작동되길 원한다면, `history.pushState` API 를 활용하도록 하자


---
자세한 내용은 [vue-js-히스토리-관리](https://www.bottlehs.com/vue/vue-js-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EA%B4%80%EB%A6%AC/)라는 블로그 글을 보자.