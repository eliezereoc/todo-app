<template>
  <div>
    <h1>Todo-Item</h1>
  </div>

  <div>
      <InputText v-model="description"/>
      <Button @click="salveTodo">Salvar</Button>
  </div>

  <div>
    <Button @click="cancel">Voltar</Button>     
  </div>
</template>

<script>
 

export default {
  data() {
      return {
          description: ""
      }
  },
  methods: {
      cancel() {
          this.$emit('cancel');
      },
      salveTodo() {
          this.$emit('salveTodo', {description: this.description});
      }
  }
}
</script>

<style scoped>
 
</style>