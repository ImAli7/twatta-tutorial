<template>
  <div id="app">
    <UserProfile/>
  </div>
</template>

<script>
import UserProfile  from "./components/UserProfile";

export default {
  name: 'App',
  components: {
      UserProfile
  }
}
</script>

<style lang="scss">
body {
  background-color: #eceff3;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
</style>
