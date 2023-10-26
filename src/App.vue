<script>
  export default{
    data(){
      return{
        todoText: '',//text입력시 바뀔 값
        todos: [
          {id: 1, text:'앨범사기', checked: false},
          {id: 2, text:'스밍돌리기', checked: false}
        ]

      }
    }
  }
</script>

<template>
  <div class="container">
    <h1 class="text-center">Todo App</h1>

    <div class="mb-3">
      <label for="todo" class="form-label">Todo Input</label>
      <input type="text" class="form-control" id="todo" placeholder="오늘의 할 일을 작성해주세요!">
    </div>
    <hr>
    <Todo v-for="todo in todos" :key="todo.id" :text="todo.text"/>
  </div>
</template>

<style scoped>

</style>
