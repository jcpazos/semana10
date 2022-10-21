<template>
  <TodoTitle msg="Welcome to Your TODOs App"/>
  <LoginComponent @user-login="onUserLogin" v-if="!loggedIn"></LoginComponent>
  <TodoMain v-if="loggedIn"></TodoMain>
</template>

<script>
import TodoTitle from './components/TodoTitle.vue'
import TodoMain from './components/TodoMain.vue'
import LoginComponent from './components/LoginComponent.vue'

export default {
  name: 'App',
  components: {
    TodoTitle,
    TodoMain,
    LoginComponent
  },
  data() {
    return {
      loggedIn: false,
    }
  },
  methods: {
    onUserLogin() {
      this.loggedIn = true;
    }
  },
  created() {
    if (sessionStorage.getItem('username')) {
      this.loggedIn = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
