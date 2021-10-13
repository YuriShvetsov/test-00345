<template>
  <div class="tabs"
    ref="container"
  >
    <div class="tabs__button-list">
      <button class="tabs__button"
        v-for="(item, index) in items"
        v-bind:key="index"
        v-bind:class="{ 'tabs__button_active': activeTabIndex === index }"
        v-on:click="activeTabIndex = index"
      >{{ item.caption }}</button>
    </div>
    <div class="tabs__active-content">
      <div class="tabs__active-caption">{{ activeContent.caption }}</div>
      <location class="tabs__location"
        v-for="location of activeContent.scheduleLocations"
        v-bind:key="location.id"
        v-bind:location="location"
      ></location>
    </div>
    <div class="tabs__button-list tabs__button-list_pos_bottom">
      <button class="tabs__button tabs__button_pos_bottom"
        v-for="(item, index) in items"
        v-bind:key="index"
        v-bind:class="{ 'tabs__button_active': activeTabIndex === index }"
        v-on:click="onClickBottomButton(index)"
      >{{ item.caption }}</button>
    </div>
  </div>
</template>

<script>
import Location from './Location.vue'

export default {
  name: 'days',
  components: {
    Location
  },
  props: {
    items: {
      type: Array
    }
  },
  data() {
    return {
      activeTabIndex: 0
    }
  },
  computed: {
    activeContent() {
      return this.items[this.activeTabIndex]
    }
  },
  methods: {
    onClickBottomButton(index) {
      this.activeTabIndex = index
      this.$refs.container.scrollIntoView()
    }
  }
}
</script>

<style lang="scss" scoped>
.tabs__button-list {
  display: flex;
}
.tabs__button-list_pos_bottom {
  margin-top: 12px;
  border-top: 2px solid #556080;
}
.tabs__button {
  padding: 10px 15px;
  font-size: 16px;
  color: #333;
  background-color: #fff;
  border: 1px solid #556080;
  border-bottom-width: 0;
  border-bottom-left-radius: unset;
  border-bottom-right-radius: unset;
  box-shadow: unset;
}
.tabs__button:not(:last-child) {
  margin-right: 3px;
}
.tabs__button_pos_bottom {
  border: 1px solid #556080;
  border-top-width: 0;
  border-radius: 3px;
  border-top-left-radius: unset;
  border-top-right-radius: unset;
}
.tabs__button_active {
  color: #fff;
  background-color: #556080;
}
.tabs__active-caption {
  padding: 10px 0px 10px 0px;
  font-size: 22px;
  color: #fff;
  text-align: center;
  background-color: #556080;
  box-shadow: 1px 2px 7px 0px rgba(0, 0, 0, 0.2);
}
.tabs__location:not(:last-child) {
  margin: 20px 0;
}
</style>
