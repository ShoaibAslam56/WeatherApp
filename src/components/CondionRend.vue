<template>
    <div>
        <h1 v-if="islogin">True Condition</h1>
        <h1 v-else>False Condition</h1>
    </div>
</template>
<script>
export default {
    data(){
        return{
            islogin:false
        }
    }
}
</script>