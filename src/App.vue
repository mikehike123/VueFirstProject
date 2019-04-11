<template>
  <div id="app">
    <MyHeader />
    <NewItemForm  v-on:addListItem= "insertListItem"/>
    <h1>My Items</h1>
    <ListItems v-bind:listItems="listArray" v-on:deleteItem="deleteListItem" v-on:markItemComplete="setComplete"/>
   
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import ListItems from './components/ListItems.vue'
import NewItemForm from './components/NewItemForm.vue'
//import { METHODS } from 'http';

export default {
  name: 'app',
  data: function()  {
     return {
       listArray : []
     }},
  components: {

    MyHeader,
    ListItems,
    NewItemForm
  },
  mounted () {
    this.readItems();
  },
  methods:{
    deleteListItem(myId)
    {
      alert(myId);
      const url = "http://localhost:8080/api/shoppingList/list/delete.php";
      axios.post(url, {
        "id": myId
      })
      .then(response=> {
        console.log(response);
        //get data again
        this.readItems();
      })
      .catch(function (error) {
        console.log(error);
      });
    },
    insertListItem(newListItem)
    {
      const url = "http://localhost:8080/api/shoppingList/list/add.php"; // site that doesn’t send Access-Control-*
      
      axios.post(url, newListItem)
      .then(response => {
        console.log(response);
        //get data again
        this.readItems();
      })
      .catch(function (error) {
        console.log(error);
      });
      //console.log('listItem added');
      
      
    },

    readItems()
    {
      axios
      .get('http://localhost/shoppingList/list/read.php')
      .then(response => {
          this.listArray = response.data['records'];
          //this.listArray[0].completed = parseInt(this.listArray[0].completed, 10);
          //this.listArray[0].completed=false;
          //alert(JSON.stringify(this.listArray))
       })
    },
    setComplete(listItem)
    {
      //const proxyurl = "https://cors-anywhere.herokuapp.com/";
      const url = "http://localhost:8080/api/shoppingList/list/completed.php"; // site that doesn’t send Access-Control-*
      
      var isCompleted = listItem.completed?1:0;
      
      axios.post(url, {
        "id": listItem.id,
        "completed": isCompleted
      })
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });
      console.log('markComplete Called');
    }

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
