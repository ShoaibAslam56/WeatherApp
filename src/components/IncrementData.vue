<template>
    <div>
        <p># {{ count }}</p>
        <button v-on:click="increment">increment</button>
        <button v-on:click="decrement">decrement</button>
    </div>
</template>

<script>
export default {
    name:'IncrementData' ,
    data(){
        return{
            count:0
        }
    },
    methods:{
        increment(){
            this.count++;
        },
        decrement(){
            if (this.count > 0) {
                this.count--;
            }
        }
    }
}
</script>