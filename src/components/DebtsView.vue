<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <ul v-for="debt in debts" :key="debt.id">
      <li>
        {{debt.title}}
      </li>
      <li>
        To: {{debt.who}}
      </li>
      <li>
        ${{debt.amount}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Collector PWA',
  data () {
    return {
      baseURL: 'http://localhost:3000',
      msg: 'My debts:',
      debts: null
    }
  },
  mounted () {
    this.$http.get(this.baseURL + '/debts').then(response => (this.debts = response.data))
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
