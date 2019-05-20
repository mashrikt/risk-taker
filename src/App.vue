<template>
  <div id="app">

  <Header />
  <Form
  :name="name"
  :text="text"
  :number="number"
  :date="date"
  :choice="choice"
  />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'

export default {
  name: 'app',
  components: {
    Header,
    Form
  },

  data() {
  return {
    resource_id: 1,
    name: "",
    text: {},
    number: {},
    date: {},
    choice: {}
    }
  },
  mounted: function() {
    fetch('http://157.230.35.253:3333/api/v1/risk-types/1/', {
      method: 'get'
    })
    .then((response) => {
        return response.json()
      })
      .then((jsonData) => {

        this.name = jsonData.name
        this.text = jsonData.risk_fields[0]
        this.number = jsonData.risk_fields[1]
        this.date = jsonData.risk_fields[2]
        this.choice = jsonData.risk_fields[3]
      })
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
