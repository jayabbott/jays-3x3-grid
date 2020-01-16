<template>
  <div class="grid-inside">
    <div id="magicEightBall" @click="shake">
      <div id="answerWindow">
        <div id="floatingPolyhedron">
        <span>{{ response }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

let responses = [
  "It is certain.",
  "It is decidedly so.",
  "Without a doubt.",
  "Yes - definitely.",
  "You may rely on it.",
  "As I see it, yes.",
  "Most likely.",
  "Outlook good.",
  "Yes.",
  "Signs point to yes.",
  "Reply hazy, try again.",
  "Ask again later.",
  "Better not tell you now.",
  "Cannot predict now.",
  "Concentrate and ask again.",
  "Don't count on it.",
  "My reply is no.",
  "My sources say no.",
  "Outlook not so good.",
  "Very doubtful.",
]

export default {
  name: 'MagicEightBall',
  data: function() {
    return {
      response: 'Shake me',
      responses: responses,
    }
  },
  methods: {
    shake: function() {
      let chosenResponseIndex = Math.floor(Math.random() * this.responses.length)
      this.response = responses[chosenResponseIndex]
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

#magicEightBall {
  position: relative;
  margin-left: auto;
  margin-right: auto;
  height: 31vh;
  width: 31vh;
  background-size: cover;
  background-image: url('/8ball.png');
}

#answerWindow {
  position: relative;
  margin-left: auto;
  margin-right: auto;
  background-color: rgba(255, 255, 255, 0.8);
  top: 35%;
  width: 40%;
}

</style>
