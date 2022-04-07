<template>
  <div>
    <button @click="increment()">+</button>
    <p>{{value}}</p>
    <button @click="decrement()">-</button>
  </div>
</template>

<script>
export default {
    data(){
        return {value :0}
    },
    methods:{
        increment(){
            this.value++
        },
        decrement(){
            this.value--
        }
    }
};
</script>