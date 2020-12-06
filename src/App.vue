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

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
button {
    width: 8.33%;
    border: 2px solid #41B883;
    background-color: #fff;
    padding: 8px 16px;
    border-radius: 2px;
    color: #41B883;
    font-weight: bold;
    margin: 0 auto;
    cursor: pointer;
    transition: all .2s linear;
    outline: none;
}
button:hover {
    background-color: #41B883;
    color: #fff;
}
button:active {
    background-color: #318f65;
    border-color: #318f65;
}
</style>
