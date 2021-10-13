<template>
  <div class="app">
    <div class="app__container">
      <program-conf v-bind:schedule="scheduleData"></program-conf>
    </div>
  </div>
</template>

<script>
import data from '../data/schedule.json'
import ProgramConf from './ProgramConf.vue'

export default {
  components: {
    ProgramConf
  },
  data() {
    return {
      scheduleData: {}
    }
  },
  methods: {
    getScheduleData() {
      this.scheduleData = data
    }
  },
  created() {
    this.getScheduleData()
  }
}
</script>

<style lang="scss" scoped>
.app {
  background-color: whitesmoke;
}
.app__container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 16;
}
</style>
