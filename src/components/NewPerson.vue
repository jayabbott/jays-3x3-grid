<template>
  <div class="grid-inside">
    <h2>
      NewPerson
    </h2>
    <form action="javascript:void(0);">
      <div class="form-item">
        <label class="form-label" for="inputFirstName">First Name</label><br>
        <input id="inputFirstName" v-model="userToAdd.firstName" type="text"><br>
      </div>
      <div class="form-item">
        <label class="form-label" for="inputLastName">Last Name</label><br>
        <input id="inputLastName" v-model="userToAdd.lastName" type="text"><br>
      </div>
      <div class="form-item">
        <label class="form-label" for="inputAge">Age</label><br>
        <input id="inputAge" v-model="userToAdd.age" type="number"><br>
      </div>
      <button class="button is-white" id="addPerson" @click="addPerson">Add Person</button>
    </form>
  </div>
</template>

<script>

function personValidToAdd(person)
{
  if (person.firstName == '')
  {
    return false
  }
  if (person.lastName == '')
  {
    return false
  }
  if (person.age < 1)
  {
    return false
  }
  if (person.age > 150)
  {
    return false
  }
  return true
}

const blankUser =  {
  firstName: '',
  lastName: '',
  age: null,
}

export default {
  name: 'NewPerson',
  data() {
    return {
      userToAdd: {
        firstName: '',
        lastName: '',
        age: null,
      }
    };
  },
  methods: {
    addPerson: function() {
      if (personValidToAdd(this.userToAdd))
      {
        this.$emit('inputData', this.userToAdd)
        this.userToAdd = Object.assign({}, blankUser);
      }
    }
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

.form-item {
  margin-top: 0.3em;
}

button {
  margin-top: 0.5em;
}
</style>
