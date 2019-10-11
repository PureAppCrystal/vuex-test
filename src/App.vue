<template>
  <div id="app">
    Partner counter: {{ parentCounter }}<br>

    <button @click="addCounter">+</button>
    <button @click="subCounter">-</button>

    <!-- Child 등록후 counter 데이터 속성을 props로 전달한다. -->
    <Child/>
  </div>
</template>

<script>
import Child from './components/Child.vue'
// map* 들을 import 하여 method에 정의하면, store 의 구현체를 사용 할 수있다.
// 사용할이름 : '등록된 method 네임'
import {  mapGetters, mapMutations, mapActions} from 'vuex'

export default {
  methods: {
    ...mapMutations({
      //addCounter: 'addCounter' ,
      subCounter: 'subCounter'

    }),
    /*
      Action 은 Mutations 와 비슷하지만  차이점이 존재한다.
      - state를 변경하지 않고, mutations의 핸들러 함수를 호출할 수 있다.
      - 비동기 작업을 수행할 수 있다. (Dispatch)
      실용적인 사용방법 : Back-End API 호출
      -> 응답받은 후 mutations의 핸들러 함수 호출
      dispatch 는 promise 를 사용한다. async/await 사용가능 
    */
    ...mapActions({
      addCounter: 'addCounter'
    })
  },
  computed: {
    ...mapGetters({
      parentCounter: 'getCounter'
    })
  },
  components: {
    Child,
  }
}


</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
