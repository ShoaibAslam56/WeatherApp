<template>
    <div>
        <h2 >{{ msg }}</h2>
    </div>
</template>
<script>
export default {
    name : 'HomePage',
    props:{
        msg: String
    }
}
</script>