<script>
  import ListView from './ListView.vue';
  import ListEdit from './ListEdit.vue';

  export default {
    components:{
      ListView,
      ListEdit
    },
    props:{
      todo:{
        type:Object, //데이터 타입
        required:true //필수여부
      }
    }
  }
</script>

<template>
  <ListView 
    v-if="todo.mode === 'view'"
    @toggle-mode="$emit('toggle-mode')"
    :todo="todo"
  />  
  <ListEdit v-else :todo="todo" />
  <!-- <h2>{{ todo.text }}</h2> -->
</template>