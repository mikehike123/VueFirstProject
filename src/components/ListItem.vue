<template>
    <div>
        
        <input type="checkbox" name="completed" id="completed">
        {{listItem.description}}
        <input type="button" value="delete" name="delete" id="delete">
        
    </div>
</template>
<script>
export default {
    name:"ListItem",
    props:['listItem']
}
</script>
<style scoped>

</style>
