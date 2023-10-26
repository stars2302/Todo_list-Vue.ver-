<script>
  export default {
    props:{
      todo:{
        type:Object, //데이터 타입
        required:true //필수여부
      }
    },
    methods:{
      toggleCheckbox(e){
        this.$emit('toggle-checkbox',{
          id: this.todo.id,
          checked: e.target.checked
        })
      },
      clickDel(){
        //this.$emit('부모에게 받은 함수',함수에 넘길 파라미터)
        this.$emit('click-delete',this.todo.id);
      }
    }

  }
</script>

<template>
  <div class="form-check" :data-id="todo.id">
    <input 
      class="form-check-input" 
      type="checkbox" 
      value="" 
      :id="'input'+todo.id" 
      @change="toggleCheckbox"
    >
    <label class="form-check-label" :for="`input${todo.id}`" :style="todo.checked ? 'text-decoration: line-through; opacity:0.5':''">
      {{todo.text}}
    </label>
    <button type="button" class="btn btn-danger btn-sm ms-2" @click="clickDel">Delete</button>
  </div>
</template>