<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Counter
      :year="2021"
      :month="0"
      :date="0"
      :hour="0"
      :minute="0"
      :second="0"
      :millisecond="0" />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Counter from '@/components/Counter.vue'

export default {
  name: 'Home',
  components: {
    // HelloWorld,
    Counter
  }
}
</script>
