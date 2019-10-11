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
import {  mapGetters, mapMutations, mapActions} from 'vuex'

export default {
  methods: {
    ...mapMutations({
      //addCounter: 'addCounter' ,
      subCounter: 'subCounter'

    }),

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
