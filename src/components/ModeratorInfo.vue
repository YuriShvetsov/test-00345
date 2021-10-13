<template>
  <div class="moder-info">
    <div class="moder-info__title">Модераторы</div>
    <ul class="moder-info__list">
      <div class="moder-info__person"
        v-for="(item, index) in persons"
        v-bind:key="index"
      >{{ item.person.caption }}</div>
    </ul>
  </div>  
</template>

<script>
export default {
  name: 'moderator-info',
  props: {
    persons: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
.moder-info__title {
  font-size: 14px;
  font-weight: bold;
}
.moder-info__list {
  margin: 0;
  padding: 0;
  list-style: none;
}
.moder-info__person {
  font-size: 14px;
}
</style>
