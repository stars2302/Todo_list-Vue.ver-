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
      },
      clickEdit(){
        this.$emit('toggle-mode',{id: this.todo.id, mode: 'edit'});
      }

    }

  }
</script>

<template>
  <!-- <h2>{{ todo.text }} Edit</h2> -->
  <div class="form-check" :data-id="todo.id">
    <label for="exampleFormControlInput1" class="form-label">수정..</label>
    <input type="text" class="form-control" id="exampleFormControlInput1" :value="todo.text">
    <!-- <label class="form-check-label" :for="`input${todo.id}`" :style="todo.checked ? 'text-decoration: line-through; opacity:0.5':''">
      {{todo.text}}
    </label> -->
    <button type="button" class="btn btn-warning btn-sm ms-2" @click="clickEdit">수정완료</button>
  </div>
</template>