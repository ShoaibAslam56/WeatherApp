<template>
    <div>
      <h2>Child Component</h2>
      <p>Message: {{ message }}</p>
      <p>Count: {{ count }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name:'ChildProp' ,
    props: {
      message: {
        type: String,
        required: true,
      },
      count: {
        type: Number,
        required: true,
      },
    },
  };
  </script>
  