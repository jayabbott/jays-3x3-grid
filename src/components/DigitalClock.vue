<template>
  <div class="grid-inside">
    <p>
      Right now it is:<br>
      <span class="time">
        {{ now }}
      </span>
    </p>
  </div>
</template>

<script>

var obj = {
  now: 'before',
}

function update()
{
  var now = new Date()
  obj.now = now.toLocaleTimeString('en-GB')
  
  setTimeout(update, 1000)
}


export default {
  name: 'DigitalClock',
  data: function(){
    return obj
  },
  beforeMount(){
    update()
  },
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
.time {
  font-family: 'DSEG14Modern', monospace;
  font-size: 6em;
  font-weight: bold;
}
</style>
