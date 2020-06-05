<template>
  <div class="todo-container">
        <b-form-input 
            v-model="newText" 
            placeholder="Enter todo"
            @keyup.enter="addTodos"
        >
        </b-form-input>
        <DisplayTodo 
            :todos = "todoFilter"
            @removeTodoFromList = "todos = $event"
        />
        <TodoFooter 
            @applyFilter = "filter = $event"
            :remaningItem = "remaning"
        />
  </div>
</template>

<script>
import DisplayTodo from './DisplayTodo.vue'
import TodoFooter from './TodoFooter.vue'
export default {
    name : 'todo-list',
    components : {
        DisplayTodo,
        TodoFooter
    },
    data () {
        return {
            newText : '',
            nextTodoId : 3,
            filter : "",
            todos : [
                {
                    id : '1',
                    text : 'Hello',
                    completed : false,
                    isEditing : false
                },
                {
                    id : '2',
                    text : 'Second',
                    completed : false,
                    isEditing : false
                }
            ]
        }
    },
    methods : {
        addTodos () {
            if(this.newText.length > 0 ){
                this.todos.push({
                    id : this.nextTodoId,
                    text : this.newText,
                    completed : false,
                    isEditing : false
                })
                this.nextTodoId++;
                this.newText =''
            }
        }
    },
    computed : {
        todoFilter() {
            if(this.filter === 'all'){
                return this.todos
            }
            else if(this.filter === 'active'){
                return this.todos.filter(todo => !todo.completed)
            }
            else if(this.filter === "completed"){
                return this.todos.filter(todo => todo.completed)
            }
            else {
                return this.todos
            }
        },
        remaning() {
            return  this.todos.filter(todo => !todo.completed).length
        },
        
    }
}
</script>

<style scoped>
.todo-container {
    width: 40%;
    margin: 25px auto;
}
.form-control {
    line-height: 2.5;
}
</style>