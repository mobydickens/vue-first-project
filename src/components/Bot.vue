<template>
  <div class='bot'>
    <h1>{{ bot.botName }}</h1>
    <p>Attack: {{ bot.attackVal }}</p>
    <p>Health: {{ bot.healthVal }}</p>
    <div>
      <button @click='getBot(bot.botName)'>Select</button>
      <button @click='retire(bot.botName)'>Retire</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Bot',
  props: ["bot", "index", "getBot", "retire"]
}
</script>

<style>
.bot {
  border: 1px black solid;
  width: 20%;
  height: 20%;
  padding: 20px;
  margin: 0 auto;
  margin-top: 5px;
}
</style>