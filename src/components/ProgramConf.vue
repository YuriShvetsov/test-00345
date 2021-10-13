<template>
  <div class="program-conf">
    <div class="program-conf__caption">{{ schedule.caption }}</div>
    <days class="program-conf__days"
      v-bind:items="schedule.scheduleDays"
    ></days>
  </div>
</template>

<script>
import Days from './Days.vue'

export default {
  name: 'program-conf',
  components: {
    Days
  },
  props: {
    schedule: {
      type: Object
    }
  },
  data() {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
.program-conf {
  padding: 16px;
}
.program-conf__caption {
  font-size: 2em;
  margin-top: 5px;
  margin-bottom: 10px;
}
</style>
