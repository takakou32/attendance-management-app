<template>
    <div class="container mx-auto p-4">
      <Login v-if="!user" @login="handleLogin" />
      <MonthlyAttendance v-else :user="user" @logout="handleLogout" />
    </div>
  </template>
  
  <script>
  import { ref } from 'vue'
  import Login from './components/Login.vue'
  import MonthlyAttendance from './components/MonthlyAttendance.vue'
  
  export default {
    name: 'App',
    components: {
      Login,
      MonthlyAttendance
    },
    setup() {
      const user = ref(null)
  
      const handleLogin = (username) => {
        user.value = username
      }
  
      const handleLogout = () => {
        user.value = null
      }
  
      return {
        user,
        handleLogin,
        handleLogout
      }
    }
  }
  </script>
  