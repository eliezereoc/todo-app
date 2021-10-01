<template>
  <div>
    <h1>Todo-Item</h1>
  </div>

  <div>
      <InputText v-model="description"/>      
  </div>

  <div class="div-botoes">
    <Button class="btn-voltar" @click="cancel">Voltar</Button>     
    <Button @click="salveTodo">Salvar</Button>
  </div>
</template>

<script>
 

export default {
  data() {
      return {
          description: ""
      }
  },
    props: {
    todo: Object
  }, 
  created() {
      if (this.todo) {
          this.description = this.todo.description;
      }
  },
  methods: {
      cancel() {
          this.$emit('cancel');
      },
      salveTodo() {
          this.$emit('salveTodo', { ...this.todo , description: this.description});
      }
  }
}
</script>

<style scoped>
    .div-botoes {
        margin-top: 1rem;
    }

    .btn-voltar {
        margin-right: 1rem;
    }
</style>