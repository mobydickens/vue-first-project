<template>
  <div>
    <div>
      <p>Bot #1: {{ bot1 }}</p>
      <p>Bot #2: {{ bot2 }}</p>
    </div>
    <div>
      <template v-if='!showBattleButton'>
        <button disabled='true' @click='battle'>Battle</button>
      </template>
      <template v-else>
        <button @click='battle'>Battle</button>
      </template>
      <button @click='clearBattle'>Clear</button>
    </div>
    <hr/>
    <Bot
      v-for='(bot, i) in bots'
      :key='i'
      :bot='bot'
      :index='i'
      :getBot='getBot'
      :retire='retire'
    />
  </div>
</template>

<script>
import Bot from './Bot'
export default {
  name: 'Botlist',
  props: ['bots', 'retire'],
  data() {
    return {
      bot1: 'Select a bot below',
      bot2: 'Select a bot below',
      showBattleButton: false
    }
  },
  methods: {
    getBot(botName) {
      if(this.bot1 === botName) {
        return alert("You can't battle yourself!")
      }
      if(this.bot1 === 'Select a bot below') {
        this.bot1 = botName
      } else {
        this.bot2 = botName
        this.showBattleButton = true
      }
    },
    clearBattle() {
      this.bot1 = 'Select a bot below'
      this.bot2 = 'Select a bot below'
      this.showBattleButton = false;
    },
    battle() {
      let empty = 'Select a bot below'
      if(this.bot1 === empty || this.bot2 === empty) {
        return alert("Pick 2 bots to fight!")
      }
      let min = 1;
      let max = 3;
      let winner = Math.floor(Math.random() * (max - min)) + min;
      if(winner === 1) {
        alert(`${this.bot1} is the winner!`)
      } else {
        alert(`${this.bot2} is the winner!`)
      }
      this.clearBattle();
    }
  },
  components: {
    Bot
  }
}
</script>

<style>

</style>


