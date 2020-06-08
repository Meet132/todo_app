<template>
  <div class="todo-display">
      <b-list-group>
            <b-list-group-item 
                v-for="(todo,index) in todos" :key="index"
                @dblclick="editTodo(todo)"
                :class="{completed : todo.completed}"
            >
            <div class="todo-list-item-box">
                <b-form-checkbox 
                    v-model="todo.completed"
                />
                <span
                    v-if="!todo.isEditing"
                >
                    {{todo.text}}
                </span>
                <b-form-input
                    v-else 
                    v-model="todo.text"
                    @keyup.enter="doneEditTodo(todo)"
                    @keyup.esc ="closeEditTodo(todo)" 
                />
            </div>
                <span 
                    class="todo-remove-button"
                    @click="removeTodo(index)"
                >
                    &times;
                </span>
          </b-list-group-item>
      </b-list-group>
  </div>
</template>

<script>
export default {
    props : {
        todos : Array,
    },
    data () {
        return {
            beforeText : ''
        }
    },
    methods : {
        removeTodo(index) {
            this.$emit('removeTodo',index)
        },
        editTodo (todo) {
            this.beforeText = todo.text
            this.$emit('editTodo',todo)
        },
        doneEditTodo(todo) {
            if(todo.text.length > 0) {
                this.$emit('editTodoDone',todo)
            }
        },
        closeEditTodo(todo){
            todo.text = this.beforeText
            this.$emit('closeEditTodo',todo)
        }
    }

}
</script>

<style scoped>
.todo-display {
    margin: 25px auto;
}
.todo-remove-button {
    float: right;
    font-size: 20px;
    cursor: pointer;
}
.list-group-item {
    display: flex;
    justify-content: space-between;
    word-break: break-all;
}
.todo-list-item-box {
    display: flex;
}
.completed {
    text-decoration: line-through;
    color: gray;
}
</style>