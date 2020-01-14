<template>
  <div class="grid-inside">
    <p>This is a login form. Use it to log in...</p>
    <form action="javascript:void(0);">
      <input v-model="inputUsername" type="text"><br>
      <input v-model="inputPassword" type="password"><br>
      <button class="button is-white" id="login" @click="login">Login</button>

      <div v-if="attemptedLogon">
        <div class="login-successful" v-if="isLoggedOn">Log-in Successful!<br>Hi, {{ loggedOnUser }}</div>
        <div v-else>Error: {{ errorOutput }}</div>
      </div>
    </form>
  </div>
</template>

<script>
import sha256 from 'js-sha256'

var validCredentials = [
  {username: 'jay', passwordHash: 'a7ed1eb62de9c5cd543c0d3590d9b9a730633e36f75a345bda7520811af6b228'},
  {username: 'admin', passwordHash: '8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918'},
]

export default {
  name: 'LoginForm',
  data: function() {
    return {
      attemptedLogon: false,
      isLoggedOn: false,
      loggedOnUser: null,
      inputUsername: '',
      inputPassword: '',
      errorOutput: '',
      validCredentials: validCredentials,
    }
  },
  methods: {
    login: function() {
      this.attemptedLogon = true
      this.isLoggedOn = false


      var userFound = false
      var correctPassword = false
      var enteredUser = ''

      for (const index in this.validCredentials) {
        if (this.inputUsername.toUpperCase() == validCredentials[index].username.toUpperCase())
        {
          userFound = true
          enteredUser = this.inputUsername
          // check password
          if (sha256(this.inputPassword) == validCredentials[index].passwordHash)
          {
            correctPassword = true
          }
          break
        }
      }
      if(userFound)
      {
        if (correctPassword)
        {
          this.isLoggedOn = true
          this.loggedOnUser = enteredUser
        }
        else
        {
          this.errorOutput = 'Password was wrong'
        }
      }
      else
      {
        this.errorOutput = 'User not found'
      }
      console.log(correctPassword)

    },
  }

}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.login-successful {
    background: #77dd77;
    margin-right: auto;
    margin-left: auto;
    max-width: fit-content;
    padding: 1em;
    margin-top: 1em;
    border: #333333 solid 2px;
}
</style>
