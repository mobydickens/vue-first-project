<template>
  <div class='box'>
    <div class=inputs>
      <label for="">Bot Name*</label>
      <input type="text" v-model="botName">
      <label for="">Attack Value*</label>
      <input type="text" v-model="attackVal">
      <label for="">Health Value*</label>
      <input type="text" v-model="healthVal">
      <div>
        <button @click="savePost">Submit</button>
        <button>Clear</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Create',
  props: ["getBots", "showCollection"],
  data() {
    return {
      botName: '',
      attackVal: '',
      healthVal: '',
      bot: {}
    }
  },
  methods: {
    savePost() {
      this.bot["botName"] = this.botName;
      this.bot["attackVal"] = this.attackVal;
      this.bot["healthVal"] = this.healthVal;
      console.log(this.bot);
      this.botName = '';
      this.attackVal = '';
      this.healthVal = '';
      this.getBots(this.bot);
      this.showCollection();
    }
  }
}
</script>

<style>
.box {
  width: 30%;
  margin: 0 auto;
  padding: 40px;
  border: 1px black solid;
}
.inputs {
  display: flex;
  flex-direction: column;
}
</style>

