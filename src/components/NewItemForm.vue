 <template>
    <div>
        <form v-on:submit="addMyListItem">
            <input type="text" v-model="description" name="description"  placeholder="New Item">
            <input type="submit" value="Add" name="add-shoppingItem" >  
        </form>
    </div>
</template>
<script>

export default {
    name:"NewItemForm",
    data: function()
    {
        return {
            description:''
        }
    },
    
    methods:
    {
        addMyListItem(event)
        {
            event.preventDefault();
            
            const newListItem =
            {
                userID: 1,
                listID: 1,
                description: this.description,

            }
            this.$emit("addListItem",newListItem);
        }
        
    }
    
}
</script>
<style scoped>
div
{
    margin-top:50px;
}
div, input
{
    font-size:30px;
}
</style>


