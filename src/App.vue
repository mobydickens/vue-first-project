<template>
  <div id="app">
    <header class='header'>
      <h4 @click='showCreate'>Create</h4>
      <h1>Battle Bots</h1>
      <h4 @click='showCollection'>Collection</h4>
    </header>
    <hr/>
    <section v-if='showForm'>
      <h1>Create here</h1>
    </section>
    <section v-else>
      <h1>Collection here</h1>
    </section>
  </div>
</template>

<script>
import Create from './components/Create';
export default {
  name: 'Home',
  data() {
    return {
      showForm: true,
    }
  },
  methods: {
    showCreate() {
      this.showForm = true
    },
    showCollection() {
      this.showForm = false
    }
  },
  components: {
    Create
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
