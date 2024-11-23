<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <Home msg="This is prop that we pass from the Parent Component"/> -->
    <!-- <CondionRend/> -->
    <!-- <LoopData/> -->
    <!-- <IncrementData/> -->
     <!-- <TerneryOprt/> -->
     <!-- <PropsLift name="Shoaib Aslam" :age="17"/> -->
      <Parent/>
  </div>
</template>

<script>
// import Home from './components/Home.vue';
// import CondionRend from './components/CondionRend.vue';
// import LoopData from './components/LoopData.vue';
// import IncrementData from './components/IncrementData.vue';
// import TerneryOprt from './components/TerneryOprt.vue';
// import PropsLift from './components/PropsLift.vue';
import Parent from './Parent.vue';
export default {
  name: 'App',
  components: {
    // Home,
    // CondionRend,
    // LoopData,
    // IncrementData,
    // TerneryOprt ,
    // PropsLift ,
    Parent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
