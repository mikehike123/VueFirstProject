<template>
    <div>
        <input type="checkbox" v-bind:checked="this.listItem.completed"  name="chk-completed" id="chk-completed" v-on:change="markComplete">
        <span v-bind:class="{'is-completed':this.listItem.completed}">{{this.listItem.description}}</span>
        <input type="button" value="X" class="round-button" name="delete" id="delete">
        
    </div>
</template>
<script>
export default {
    name:"ListItem",
    props:['listItem'],
    methods:
    {
        markComplete(event)
        {
           
            this.listItem.completed = !this.listItem.completed;
            //this.$forceUpdate();
            this.$emit("markComplete",this.listItem);

            
        }
    }
}
</script>
<style scoped>
    .is-completed
    {
        color:green;
        text-decoration: line-through;
    }
    div, input
    {
        font-size:30px;
    }
    #delete
    {
        margin:0 0px 0 40px;
    }
    
    #chk-completed
    {
        
        margin:0 40px 0 0;
    }

    .round-button {
        display:inline-block;
        width:30px;
        height:30px;
        line-height:25px;
        border: 2px solid #f5f5f5;
        border-radius: 50%;
        color:#f5f5f5;
        text-align:center;
        text-decoration:none;
        background:red;
        box-shadow: 0 0 3px gray;
        font-size:20px;
        font-weight:bold;
    }
    .round-button:hover
    {
        color:black;
        background-color: white;
        border: 2px solid black;
    }
    input[type=checkbox] {
        transform: scale(2);
    }
</style>
