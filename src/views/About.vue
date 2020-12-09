<template>
  <div>
        <h1>This is the About page</h1>

    <Counter
      :year="2021"
      :month="0"
      :date="0"
      :hour="0"
      :minute="0"
      :second="0"
      :millisecond="0"
    />
    <p>By Kingsconsult</p>
  </div>
</template>

<script>
import Counter from "@/components/Counter.vue";
export default {
  components: { Counter },
};
</script>

<style  scoped>
</style>
