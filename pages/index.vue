<template>
  <div>
    <div class="container">
      <h1>BRM / TDD</h1>
      <h2>A simple BMR and TDEE calculator</h2>
      <a href="#calc" target="_blank" class="btn bg red">What is my BMR?</a>
    </div>
    <calculator />
    <end />
  </div>
</template>

<script>
import calculator from '~/components/calculator.vue'
import end from '~/components/end.vue'

export default {
  components: {
    calculator,
    end
  }
}
</script>

<style lang="scss" scoped>
@import 'assets/css/setup/variables';
</style>
