<template>
  <div id="app">
    <h1 class="header">Welcome You Hungry One</h1>   
    <Meal />
  </div>
</template>

<script>
import Meal from './components/Meal'

export default {
  name: 'App',
  components: {
   Meal
  }
}
</script>

<style>

* {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
}

#app {
  background: rgb(252, 236, 214);
  min-height: 100vh;
  padding: 1em;
}

.header {
  text-align: center;
  color: rgb(21, 99, 99);
  font-family: fantasy;
  letter-spacing: 3px;
}

button {
  padding: .5em 4em;
  border: none;
  background: black;
  color: rgb(252, 236, 214);
  outline: 0;
  border-radius: 4px;
  font-size: 1.2em;
  font-weight: 700;
  transition: .4s;
}

button:hover {
  background: gray;
}
</style>
