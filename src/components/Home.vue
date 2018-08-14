<template>
  <div class="container">
    <div class="game__container">

    </div>
    <div class="prompt__container">
      <div class="prompt__dataContainer">
        <div class="prompt__line" v-for="(line, lineIndex) in data" :key="lineIndex">
          <p>{{ line }}</p>
        </div>
      </div>
      <div class="prompt__inputContainer">
        <span class="prompt__chevron">></span>
        <input class="prompt__input" type="text" ref="prompt" v-model="prompt" @keyup.enter="submit">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      prompt: '',
      data: []
    }
  },
  methods: {
    submit () {
      this.data.push(this.prompt)
      this.prompt = ''
    },
    focus () {
      console.log('test')
    }
  },
  mounted () {
    this.$refs.prompt.focus()
  }
}
</script>

<style>
.game__container {
  height: 65vh;
  background-color: #DDDDDD;
}

.prompt__container {
  box-sizing: border-box;
  height: 35vh;
  background-color: #000000;
  color: #00FF00;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 10px;
}

.prompt__dataContainer {
  overflow-y: scroll;
  overflow-x: hidden;
  font-size: 1.3em;
}

.prompt__inputContainer {
  display: flex;
  align-items: center;
  min-height: 30px;
}

.prompt__chevron {
  flex: initial;
  font-size: 1.5em;
  font-weight: bold;
  margin-right: 5px;
}

.prompt__input {
  flex: 1;
  border: none;
  font-size: 1.5em;
  color: #00FF00;
  background-color: #000000;
}

.prompt__input:focus {
  outline: none;
}
</style>
