<template>
  <div id="app">
    <header class='header'>
      <h4 @click='showCreate'>Create</h4>
      <h1>Battle Bots</h1>
      <h4 @click='showCollection'>Collection</h4>
    </header>
    <hr/>
    <section v-if='showForm'>
      <Create 
        v-bind:getBots='getBots'
        v-bind:showCollection='showCollection'
      />
    </section>
    <section v-else>
      <Botlist 
        :bots='bots'
        :retire='retire'
      />
    </section>
  </div>
</template>

<script>
import Create from './components/Create';
import Botlist from './components/Botlist';

export default {
  name: 'Home',
  data() {
    return {
      showForm: true,
      bots: []
    }
  },
  methods: {
    showCreate() {
      this.showForm = true
    },
    showCollection() {
      this.showForm = false
    },
    getBots(botArray) {
      this.bots.push(botArray);
    },
    retire(botName) {
      this.bots = this.bots.filter(bot => botName !== bot.botName);
    }
  },
  components: {
    Create,
    Botlist
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header {
  display: flex;
  justify-content: space-between;
}
</style>
