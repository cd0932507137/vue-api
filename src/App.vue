<template>
  <div id="app">
    <router-view/>
    <div class="container">
      <div class="row">
        <table class="table table-striped">
          <thead>
            <tr>
              <th scope="col">sno(站點代號)</th>
              <th scope="col">sna(場站名稱)</th>
              <th scope="col">sarea(場站區域)</th>
              <th scope="col">snaen(場站名稱)</th>
              <th scope="col">act(全站禁用狀態)</th>
            </tr>
          </thead>
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
    </div>
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
</style>
