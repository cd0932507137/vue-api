<template>
  <div id="app">
    <router-view/>
    <table>
      <tr>
        <th>sno(站點代號)</th>
        <th>sna(場站名稱)</th>
        <th>sarea(場站區域)</th>
        <th>snaen(場站名稱)</th>
        <th>act(全站禁用狀態)</th>
      </tr>
      <tbody>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{ item.sno }}</td>
          <td>{{ item.sna }}</td>
          <td>{{ item.sarea }}</td>
          <td>{{ item.snaen }}</td>
          <td>{{ item.act }}</td>
        </tr>
    </tbody>
    </table>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

export default {
  name: 'App',
  data: function () {
    return {
      items: []
    }
  },
  created () {
    Vue.axios.get('/data/youbike').then(response => {
      console.log(response.data)
      this.items = response.data.retVal
    })
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
