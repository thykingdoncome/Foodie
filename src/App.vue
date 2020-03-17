<template>
  <div id="app">
   <div class="main-wrapper">
      <Header />
    <h2 class="header">Welcome to Foodie Random Meal Generator</h2>   
    <Meal />
    <Footer />
   </div>
  </div>
</template>

<script>
import Meal from './components/Meal'
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
   Meal,
   Header,
   Footer
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
  background: #FBD791;
  min-height: 100vh;
  padding: 0 3em;
}

.main-wrapper {
  padding-top: 1em;
  max-width: 1440px;
  margin: 0 auto;
}

.header {
  text-align: center;
  color: rgb(21, 99, 99);
  font-family: fantasy;
  letter-spacing: 3px;
}

button {
  padding: .5em 3em;
  border: none;
  background: black;
  color: rgb(252, 236, 214);
  outline: 0;
  border-radius: 2em;
  font-size: 1.2em;
  font-weight: 700;
  transition: .4s;
}

button:hover {
  background: gray;
}

a {
  text-decoration: none;
}
</style>
