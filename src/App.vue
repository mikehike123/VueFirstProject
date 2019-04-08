<template>
  <div id="app">
    <MyHeader />
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App Lets change this!!!"/>
    <h1>My Items</h1>
    <div v-bind:key="listItem.id" v-for="listItem in listArray">
        <div>Description={{listItem.description}}</div>
    </div>
    <MyForm />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import MyForm from './components/MyForm.vue'
import MyHeader from './components/MyHeader.vue'

export default {
  name: 'app',
  data: function()  {
     return {
       listArray : []
     }},
  components: {
    HelloWorld,
    MyForm,
    MyHeader,
  },
  mounted () {
    axios
      .get('http://localhost/shoppingList/list/read.php')
      .then(response => {
          this.listArray = response.data['records'];
          alert(JSON.stringify(this.listArray))
       })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
body
{
  margin:0px;
}
</style>
