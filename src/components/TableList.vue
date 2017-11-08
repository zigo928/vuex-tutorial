<template>
  <div class="">
    <table>
      <thead>
        <tr>
          <th @click="sortBy('name')">Name</th>
          <th @click="sortBy('age')">Age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="row in finalData">
          <td>{{ row.name }}</td>
          <td>{{ row.age }}</td>
        </tr>
      </tbody>
    </table>
    <input v-model="searchText" placeholder="Search">
    <a href="#" @click="prevPage">Prev</a>
    <a href="#" @click="nextPage">Next</a>
  </div>
</template>

<script>
import _ from 'lodash'
export default {
  data () {
    return {
      tableData: [
        {name: 'john', age: 44},
        {name: 'junZhang', age: 28},
        {name: 'apple', age: 30},
        {name: 'beer', age: 20},
        {name: 'origen', age: 50},
        {name: 'bnana', age: 10},
        {name: 'xiaoxu', age: 30}
      ],
      searchText: '',
      sortColumn: 'name',
      pageNum: 0
    }
  },
  computed: {
    finalData () {
      return this.paginateRows(this.sortedData, this.pageNum)
    },
    sortedData () {
      return this.sortedRows(this.filteredData, this.sortColumn)
    },
    filteredData () {
      return this.filteredRows(this.tableData, this.searchText)
    }
  },
  methods: {
    paginateRows (data, pageNum) {
      console.log('page num is ' + pageNum)
      let start = 5 * pageNum
      let end = 5 * (pageNum + 1)
      return _.slice(data, start, end)
    },
    sortedRows (data, sortColumn) {
      console.log('sort column is ' + sortColumn)
      return _.sortBy(data, sortColumn)
    },
    filteredRows (data, searchText) {
      console.log('search text is ' + searchText)
      if (searchText !== '') {
        return _.filter(data, {'name': searchText})
      }

      return data
    },
    sortBy (sortColumn) {
      console.log('sort name is ' + sortColumn)
      this.sortColumn = sortColumn
    },
    prevPage () {
      if (this.pageNum > 0) {
        this.pageNum -= 1
      }
    },
    nextPage () {
      if ((this.pageNum + 1) * 5 < this.filteredData.length) {
        this.pageNum += 1
      }
    }
  }
}
</script>

<style scoped>

</style>
