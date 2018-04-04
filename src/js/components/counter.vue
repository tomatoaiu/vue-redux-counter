<template>
<div>
    value : {{value}}
    <button @click="increment()">+</button>
    <button @click="decrement()">-</button>
</div>
</template>

<script>
import store from '../store/index'

export default {
    data(){
        return {
            value: store.getState(),
        }
    },
    mounted(){
        store.subscribe(() => {
            this.value = store.getState();
        });
    },
    methods: {
        increment(){
            store.dispatch({type: "INCREMENT"});
        },
        decrement(){
            store.dispatch({type: "DECREMENT"});
        }
    }
}
</script>

<style scoped>

</style>
