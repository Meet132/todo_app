<template>
  <div class="todo-footer">
    <b-button 
        variant="outline-success" 
        @click="filterTodo('all')"
        >
            All
    </b-button>
    <b-button 
        variant="outline-success" 
        @click="filterTodo('active')"
        >
            Active
    </b-button>
    <b-button 
        variant="outline-success" 
        @click="filterTodo('completed')"
        >
            Completed
    </b-button>
    <h5>{{remaningItem}} itmes left</h5>
  </div>
</template>

<script>
export default {
    props : {
        remaningItem : Number
    },
    methods : {
        filterTodo(updateFilter){
            this.$emit('applyFilter',updateFilter)
        }
    }

}
</script>

<style scoped>
.todo-footer {
    margin: 15px auto;
    display: flex;
    justify-content: space-between;
}
.btn {
    margin-right: 10px;
}
</style>