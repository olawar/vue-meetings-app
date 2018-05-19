<template>
  <div id="app">

    <h1 class="app-title">{{ msg }}</h1>
    <login-form v-if="!isAuthenticated" @login="logMeIn($event)" :button-label="'Wchodzę'"/>
    <content-page v-else @logout="logMeOut()" :user="authenticatedUsername" />
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import ContentPage from "./ContentPage";
export default {
  name: 'app',
  data () {
    return {
      msg: 'System zapisów na zajęcia',
      email: '',
      isAuthenticated: false,
    }
  },
  methods: {
    logMeIn(username) {
      this.authenticatedUsername = username;
      this.isAuthenticated = true;
    },
    logMeOut() {
      this.authenticatedUsername = '';
      this.isAuthenticated = false;
    }
  },
  components: {
    ContentPage,
    LoginForm},
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 40px auto;
  max-width: 80%;
}

.app-title {
  text-align: center;
}

h1, h2 {
  font-weight: normal;
}

ul {
  padding: 0;
}

/*li {*/
  /*display: inline-block;*/
  /*margin: 0 10px;*/
/*}*/

a {
  color: #42b983;
}

hr {
  margin: 1rem 0;
}
</style>
