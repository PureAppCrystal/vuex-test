<template>
    <div>  
        <hr>
        Child counter: {{ childCounter }} <br>
        <button @click="addCounter">+</button>
        <button @click="subCounter">-</button>
    </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from 'vuex'

export default {
    // Parenter 에서 넘겨준 counter 속성을 passedCounter 로 받음
    // props : ['passedCounter']
    name: 'child',
    computed: {
        ...mapGetters({
            childCounter: 'getCounter'
        })
    },
    methods: {
    ...mapMutations({
      //addCounter: 'addCounter' ,
      subCounter: 'subCounter'

    }),

    ...mapActions({
      addCounter: 'addCounter'
    })
  },    
}
</script>
