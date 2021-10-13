<template>
  <div class="report">
    <div class="report__duration">{{ reportData.duration }}</div>
    <div class="report__side">
      <!-- <img class="report__img" src="" /> -->
      <div class="report__img-plug"></div>
    </div>
    <div class="report__content">
      <div class="report__speaker"
        v-if="reportData.speaker"
      >
        <div class="report__speaker-name">{{ reportData.speaker.caption }}</div>
        <div class="report__speaker-country">{{ reportData.speaker.countryName }}</div>
        <div class="report__speaker-comment">{{ reportData.speaker.comment }}</div>
      </div>
      <div class="report__caption">{{ reportData.caption }}</div>
      <a class="report__link"
        v-if="reportData.videoUrl"
        v-bind:href="reportData.videoUrl"
      >
        <i class="report__link-icon icofont-video"></i><span class="report__link-name">Посмотреть лекцию</span><i class="report__link-icon icofont-lock"></i>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'report',
  props: {
    reportData: {
      type: Object
    }
  }
}
</script>

<style lang="scss" scoped>
.report {
  padding: 12px;
  position: relative;
  display: flex;
  background-color: #fff;
  padding: 20px 10px;
  box-shadow: 1px 2px 7px 0px rgba(0, 0, 0, .2);
}
.report__duration {
  padding: 0 10px;
  position: absolute;
  left: -140px;
  top: 50%;
  transform: translateY(-50%);
  color: #fff;
  background-color: gainsboro;
}
.report__duration::before {
  content: '';
  width: 99px;
  height: 1px;
  position: absolute;
  left: 100%;
  top: 50%;
  display: block;
  background-color: gainsboro;
}
.report__side {
  width: 100px;
  padding-left: 10px;
  flex-shrink: 0;
}
.report__img-plug {
  width: 70px;
  height: 70px;
  background-color: gainsboro;
  border-radius: 50%;
}
.report__caption {
  margin-top: 8px;
  font-size: 16px;
}
.report__speaker-name,
.report__speaker-country {
  font-size: 16px;
  font-weight: bold;
}
.report__link {
  margin-top: 8px;
  display: block;
  font-size: 14px;
  color: #337ab7;
  text-decoration: none;
}
.report__link-name {
  margin: 0 3px;
}
.report__link-icon {
  font-size: 18px;
  color: #888;
}
.report__link:hover .report__link-name {
  text-decoration: underline;
}
</style>
