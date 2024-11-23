<template>
  <div>
    <h1>{{ name }}</h1>
    <h1>{{ age }}</h1>
  </div>
</template>

<script>
export default {
      name:'PropsLift',
      props:{
        name: String,
        age: Number,
      },
}
</script>