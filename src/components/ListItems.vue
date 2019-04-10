<template>
    <div>
        <div v-bind:key="listItem.id" v-for="listItem in listItems">
            <ListItem  v-bind:listItem="listItem" v-on:markComplete="$emit('markComplete',listItem)"/>
        </div>
    </div>
</template>
<script>
import ListItem from './ListItem.vue'
export default {
    name:"ListItems",
    props:['listItems', 'listItem'],
    components:
    {
        ListItem
    }
}
</script>
<style scoped>

</style>


