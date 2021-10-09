<template>
  <Heading></Heading>
  <LineCopier></LineCopier>
  <APITest></APITest>
</template>

<script>
import LineCopier from './components/LineCopier/LineCopier.vue'
import Heading from './components/Heading/Heading.vue'
import APITest from './components/APITest/APITest.vue'

export default {
  name: 'App',
  components: {
    LineCopier,
    Heading, 
    APITest
  },
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Quicksand:300,500");

#app {
  font-family:  'Quicksand', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
  padding: 0px;
}
</style>
