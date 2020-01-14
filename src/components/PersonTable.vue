<template>
  <div class="grid-inside">
    <h2>
      PersonTable
    </h2>

    <table class="people-table">
      <tr>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Age</th>
        <th>Delete</th>
      </tr>
      <!-- loop -->      
      <tr v-for="(person, personIndex) in people" v-bind:key="personIndex">
        <td>{{ person.firstName }}</td>
        <td>{{ person.lastName }}</td>
        <td>{{ person.age }}</td>
        <td><button class="button is-primary is-small" id="delete" @click="deleteEntry(personIndex)">Delete</button></td>
      </tr>
      <!-- loop -->
    </table>



  </div>
</template>

<script>

var people = [
  {
    firstName: 'Jay',
    lastName: 'Abbott',
    age: 25,
  },
  {
    firstName: 'Bobby',
    lastName: 'Tables',
    age: 10,
  },
  {
    firstName: 'Katie',
    lastName: 'Miles',
    age: 47,
  },
  {
    firstName: 'Edward',
    lastName: 'Morton',
    age: 20,
  },
  {
    firstName: 'Isaac',
    lastName: 'Swift',
    age: 27,
  },
  {
    firstName: 'Zachary',
    lastName: 'Page',
    age: 47,
  },
  {
    firstName: 'Eva',
    lastName: 'Bird',
    age: 66,
  },
  {
    firstName: 'Freya',
    lastName: 'Ross',
    age: 27,
  },
  {
    firstName: 'Jordan',
    lastName: 'Sanderson',
    age: 30,
  },
]
export default {
  name: 'PersonTable',
  data: function() {
    return {
      people: people
    }
  },
  props: {
    personToAdd: {
      type: Object
    }
  },
  methods: {
    deleteEntry: function(personIndex) {
      this.people.splice(personIndex, 1)
    },
  },
  watch: {
    personToAdd: function() {
      this.people.push(this.personToAdd);
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

.people-table {
  margin-left: 5%;
  width: 90%;
}

.people-table tr th {
  width: 25%;
}

.people-table tr td {
  padding-top: 0.2em;
  padding-bottom: 0.2em;
}

tr:nth-child(even) {
  background-color: rgba(255, 255, 255, 0.25);
}


</style>
