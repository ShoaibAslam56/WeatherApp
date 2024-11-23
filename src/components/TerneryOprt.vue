<template>
    <div>
        <!-- for styling through the style attribute -->
        <h1 v-bind:style="{color : value ? 'red' : 'pink'}">Ternory opreator</h1>
        <!-- for styling through the class -->
         <h1 v-bind:class="value ? 'active' : 'inactive'">Styling through the Class </h1>
    </div>
</template>
<script>
export default {
    data(){
        return{
            value:false
        }
    }
}
</script>

<style  scoped>
.active{
    color:blue;
}
.inactive{
    color:green
}
</style>