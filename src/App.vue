<template>
  <div id="app">
    <user-form></user-form>
  </div>
</template>

<script>
import UserForm from './components/formulaires.vue';

export default {
  components: {
    UserForm
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  padding: 20px;
  background-color: #f5f5f5;
  margin: 0;
}

#app {
  max-width: 1600px;
  margin: 0 auto;
}
</style>
