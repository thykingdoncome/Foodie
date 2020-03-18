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
import Meal from "./components/Meal";
import Header from "./components/Header";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Meal,
    Header,
    Footer
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
}

#app {
  background: #fbd791;
  min-height: 100vh;
  padding: 0 3em;
}

.main-wrapper {
  padding-top: 1em;
  max-width: 1440px;
  margin: 0 auto;
}

.header {
  color: rgb(21, 99, 99);
  font-family: fantasy;
  letter-spacing: 3px;
  text-align: center;
}

button {
  padding: 0.5em 3em;
  border: none;
  background: black;
  color: rgb(252, 236, 214);
  outline: 0;
  border-radius: 2em;
  font-size: 1.2em;
  font-weight: 700;
  transition: 0.4s;
}

button:hover {
  background: gray;
}

a {
  text-decoration: none;
  color: rgb(21, 99, 99);
}

@media screen and (max-width: 780px) {
  button {
    padding: 0.5em 1em;
    font-size: .9em;
  }

  .header {
    letter-spacing: 1px;
    font-weight: 100;
     font-family: monospace;
  }

  #app {
    padding: 0 .5em;
  }
}
</style>
