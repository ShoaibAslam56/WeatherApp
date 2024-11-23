<template>
    <div>
      <h1>Parent Component</h1>
      <!-- Pass props to the child component -->
      <ChildProp :message="parentMessage" :count="parentCount" />
    </div>
  </template>
  
  <script>
  import ChildProp from './components/PropsLifting/ChildProp.vue';
  
  export default {
    components: {
      ChildProp
    },
    data() {
      return {
        parentMessage: 'Hello from the Parent!',
        parentCount: 42,
      };
    },
  };
  </script>
  