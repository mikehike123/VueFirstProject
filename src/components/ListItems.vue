<template>
    <div>
        <div v-bind:key="listItem.id" v-for="listItem in listItems">
            <ListItem  v-bind:listItem="listItem"   v-on:deleteItem="$emit('deleteItem',$event)" v-on:markDone="$emit('markItemComplete',listItem)"/>
        </div>
    </div>
</template>
<script>
import ListItem from './ListItem.vue'
export default {
    name:"ListItems",
    props:['listItems'],
    components:
    {
        ListItem
    },
    data:function()
    {
        return{
            id:0
        }
    }
}
</script>
<style scoped>

</style>


