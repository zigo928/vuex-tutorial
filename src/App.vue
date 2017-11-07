<template>
  <div id="app">
    <h3>Increment:</h3>
    <increment></increment>
    <h3>Counter:</h3>
    <counter></counter>
    <TableList></TableList>
  </div>
</template>

<script>
import Counter from './components/CounterDisplay.vue'
import Increment from './components/IncrementButton.vue'
import TableList from './components/TableList.vue'
export default {
  components: {
    Counter,
    Increment,
    TableList
  }
}
</script>

<style>
</style>
