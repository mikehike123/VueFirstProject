<template>
  <div id="app">
    <MyHeader />
    
    <h1>My Items</h1>
    <ListItems v-bind:listItems="listArray"/>
   
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import ListItems from './components/ListItems.vue'

export default {
  name: 'app',
  data: function()  {
     return {
       listArray : []
     }},
  components: {

    MyHeader,
    ListItems
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
