<script>
  import Todo from './components/Todo.vue';

  export default{
    components:{
      Todo
    },
    data(){
      return{
        todoText: '',//text입력시 바뀔 값
        todos: [
          {id: 1, text:'앨범사기', checked: false, mode: 'view'},
          {id: 2, text:'스밍돌리기', checked: false, mode: 'edit'}
        ]

      }
    },
    methods:{
      AddTodo(e){
        // console.log(e.target.value);
        this.todos.push({
          id: Math.random(), 
          text: e.target.value, 
          checked: false,
          mode: 'view'
        });
        this.todoText ='';
      },
      toggleCheck({id,checked}){
        const idx = this.todos.findIndex(todo => todo.id === id); //조건에 부합하는 아이의 index를 추출
        this.todos[idx].checked = checked;
      },
      deleteTodo(id){
        if(confirm('정말 삭제하시겠습니까?')){
          const idx = this.todos.findIndex(todo => todo.id === id);
          this.todos.splice(idx,1);
        }
      },
      toggleMode({id,mode}){
        const idx = this.todos.findIndex(todo => todo.id === id);
        this.todos[idx].mode = mode;
      }
    }
  }
</script>

<template>
  <div class="container">
    <h1 class="text-center">Todo App</h1>

    <div class="mb-3">
      <label for="todo" class="form-label">Todo Input</label>
      <input 
        type="text" 
        class="form-control" 
        id="todo" 
        placeholder="오늘의 할 일을 작성해주세요!"
        @keyup.enter="AddTodo"
        v-model="todoText"
      >
    </div>
    <hr>
    <Todo 
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo" 
      @toggle-checkbox="toggleCheck" 
      @click-delete="deleteTodo"
      @toggle-mode="toggleMode"
    />
    
  </div><!--container-->
</template>

<style scoped>

</style>
