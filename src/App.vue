<template>
  <div id="app">
    <h3>Increment:</h3>
    <increment></increment>
    <h3>Reset:</h3>
    <reset></reset>
    <h3>Counter:</h3>
    <counter></counter>
  </div>
</template>

<script>
import Counter from './components/CounterDisplay.vue'
import Increment from './components/IncrementButton.vue'
import Reset from './components/ResetButton.vue'
export default {
  components: {
    Counter,
    Increment,
    Reset
  }
}
</script>

<style>
</style>
