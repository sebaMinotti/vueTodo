<template>
<MyTodoList />

</template>

<script>
import MyTodoList from './components/MyTodolist.vue'

export default {
  name: 'App',
  components: {
     MyTodoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;

}
</style>
