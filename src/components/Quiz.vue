<template>
    <div class="grid-inside">
        <p>
            Quiz
        </p>

        <ol>
            <li class="question" v-for="(quizItem, questionIndex) in quiz" v-bind:key="questionIndex">
                {{ questionIndex + 1 }}. {{ quizItem.question }}
                <div class="control columns is-desktop">
                <div class="column is-one-third-desktop is-one-third-widescreen is-one-third-fullhd answer-options" v-for="(answer, answerIndex) in quizItem.answers" v-bind:key="answerIndex">
                    <input type="radio" v-bind:name="'q' + questionIndex + 'radios'" v-bind:id="'q' + questionIndex + 'a' + answerIndex" v-bind:value="'q' + questionIndex + 'a' + answerIndex" v-model="quizItem.chosenAnswer">
                    <label class="answer-label" v-bind:for="'q' + questionIndex + 'a' + answerIndex">{{ answer }}</label>
                </div>
                </div>
            </li>
        </ol>
        <div class="button-container lick">
            <button class="button is-primary" id="submit" @click="checkAnswers">Submit</button>
        </div>

    </div>

</template>

<script>

var quiz = [
  {
    question: 'When the 🌑 hits your 👁️ like a big 🍕🥧, that\'s...',
    answers: [
      'Wtf?',
      'Amore',
      'An old song',
    ],
    correctAnswer: 1,
    chosenAnswer: null,
  },
  {
    question: 'A thing is moving away from you and you bouce a signal (such as sound, light or a radio signal) off it. What happens to your perception of the frequency of the singal you get back?',
    answers: [
      'Nothing',
      'It gets higher',
      'It gets lower',
    ],
    correctAnswer: 2,
    chosenAnswer: null,
  },
  {
    question: 'How many corners does a cube have?',
    answers: [
      '6',
      '8',
      '10',
    ],
    correctAnswer: 1,
    chosenAnswer: null,
  },
  {
    question: 'Whats the name of the first geezer to talk about the thing in question 2?',
    answers: [
      'Jay made it up',
      'Friedrich Hasenöhrl',
      'Christian Doppler',
    ],
    correctAnswer: 2,
    chosenAnswer: null,
  },
]


export default {
  name: 'Quiz',
  data: function() {
    return {
      quiz: quiz,
      picked: '',
    }
  },
  methods: {
    checkAnswers: function() {
      var allCorrect = true
      for (const quizItem of this.quiz)
      {
        var questionCorrect = ((quizItem.chosenAnswer !== null) && (quizItem.chosenAnswer.charAt(3) == quizItem.correctAnswer))
      }

      if (!questionCorrect)
      {
        allCorrect = false
      }

      var goodSound = document.getElementById('goodSound');
      var badSound = document.getElementById('badSound');

      if(allCorrect)
      {
        console.log('Quiz: All correct')
        goodSound.play()
      }
      else
      {
        console.log('Quiz: Some not correct')
        badSound.play()
      }
    },
  },
  mounted() {
      var goodSound = document.createElement('audio')
      goodSound.setAttribute('src', '/quiz-sounds/good.mp3')
      goodSound.setAttribute('autostart', 'false')
      goodSound.setAttribute('id', 'goodSound')
      goodSound.setAttribute('type', 'audio/mp3')
      
      document.body.appendChild(goodSound)

      var badSound = document.createElement('audio')
      badSound.setAttribute('src', '/quiz-sounds/bad.mp3')
      badSound.setAttribute('autostart', 'false')
      badSound.setAttribute('id', 'badSound')
      badSound.setAttribute('type', 'audio/mp3')
      
      document.body.appendChild(badSound)
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

.question {
    margin-top: 1.5em;
    width: 95%;
}

.answer-label {
    padding-left: 0.7em;
}

.button-container {
  padding-top: 2em;
  padding-bottom: 2em;
}

.lick, button {
  cursor: url('../assets/tongue.png'), auto; 
}
</style>
