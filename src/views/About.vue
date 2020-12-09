<template>
  <div>
    <Counter
      :year="2021"
      :month="0"
      :date="0"
      :hour="0"
      :minute="0"
      :second="0"
      :millisecond="0"
    />
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
