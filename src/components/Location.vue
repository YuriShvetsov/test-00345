<template>
  <div class="location">
    <dropdown class="location__dropdown"
      v-bind:opened="true"
      v-bind:openerDark="true"
      v-bind:openerCenter="true"
    >
        <template
          v-slot:opener
        >
          <div class="location__caption">{{ location.caption }}</div>
        </template>
        <template
          v-slot:content
        >
          <event-session
            v-for="session of location.eventSessions"
            v-bind:key="session.id"
            v-bind:session="session"
          ></event-session>
        </template>
      </dropdown>
  </div>
</template>

<script>
import Dropdown from './Dropdown.vue'
import EventSession from './EventSession.vue'

export default {
  name: 'location',
  components: {
    Dropdown,
    EventSession
  },
  props: {
    location: {
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

</style>
