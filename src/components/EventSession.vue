<template>
  <div class="event-session">

    <div class="event-session__time">
      <div class="event-session__time-value">{{ session.timePeriod }}</div>
    </div>

    <div class="event-session__content">
      <dropdown v-bind:opened="false">

        <template v-slot:opener>
          <div class="event-session__caption">{{ session.caption }}</div>
        </template>

        <template v-slot:desc>
          <div class="event-session__desc">{{ session.description }}</div>
        </template>

        <template v-slot:content>

          <moderator-info class="event-session__moderator-list"
            v-if="hasModerators"
            v-bind:persons="session.eventSessionModerators"
          ></moderator-info>

          <report class="event-session__report"
            v-for="report in session.eventSessionItems"
            v-bind:key="report.id"
            v-bind:reportData="report"
          ></report>

          <div class="event-session__info"
            v-if="session.url"
          >
            <a class="event-session__link"
              v-bind:href="session.url"
            >Подробнее о мероприятии</a>
          </div>

        </template>

      </dropdown>
    </div>

  </div>
</template>

<script>
import Dropdown from './Dropdown.vue'
import Report from './Report.vue'
import ModeratorInfo from './ModeratorInfo.vue'

export default {
  name: 'event-session',
  components: {
    Dropdown,
    Report,
    ModeratorInfo
  },
  props: {
    session: {
      type: Object
    }
  },
  data() {
    return {

    }
  },
  computed: {
    hasModerators() {
      return this.session.eventSessionModerators.length > 0
    }
  }
}
</script>

<style lang="scss" scoped>
.event-session {
  display: flex;
  align-items: flex-start;
}
.event-session__time {
  width: 100%;
  max-width: 300px;
  margin-top: 36px;
  position: relative;
  background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0) 50%, gainsboro 50%, gainsboro calc(50% + 1px), rgba(255, 255, 255, 0) calc(50% + 1px), rgba(255, 255, 255, 0));
}
.event-session__time::before {
  content: '';
  width: 19px;
  height: 19px;
  position: absolute;
  right: calc((100% - 120px) / 2);
  top: 6px;
  transform: translateX(50%);
  display: block;
  background-color: white;
  border: 6px solid gainsboro;
  border-radius: 50%;
}
.event-session__time-value {
  width: 120px;
  padding: 5px 0;
  font-size: 14px;
  color: #fff;
  text-align: center;
  background-color: #52ae32;
  box-shadow: 1px 2px 7px 0px rgba(0, 0, 0, 0.2);
}
.event-session__content {
  width: 100%;
  padding: 32px 20px 20px;
  position: relative;
  border-left: 1px solid gainsboro;
}
.event-session__content::before {
  content: '';
  width: 60px;
  height: 1px;
  position: absolute;
  left: 0;
  top: 51px;
  display: block;
  background-color: gainsboro;
}
.event-session__content::after {
  content: '';
  width: 5px;
  height: 5px;
  position: absolute;
  left: 60px;
  top: 49px;
  display: block;
  background-color: gainsboro;
  border-radius: 50%;
}
.event-session__content-header {
  margin-bottom: 20px;
}
.event-session__caption {
  padding-left: 60px;
  font-size: 18px;
}
.event-session__desc {
  margin-top: 10px;
  margin-bottom: 20px;
  padding-left: 60px;
}
.event-session__report:not(:last-child) {
  margin-bottom: 20px;
}
.event-session__moderator-list {
  margin-bottom: 20px;
}
.event-session__info {
  padding: 20px 0;
  display: flex;
  justify-content: flex-end;
  border-top: 1px solid #eee;
}
.event-session__link {
  margin-left: auto;
  padding: 6px 12px;
  display: block;
  text-decoration: none;
  color: #333;
  background-color: #fff;
  border: 1px solid #ccc;
}
.event-session__link:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}

@media screen and (max-width: 991px) {

  .event-session__caption {
    padding-left: 20px;
    font-size: 16px;
  }

  .event-session__desc {
    margin-top: 0;
    padding-left: 20px;
  }

  .event-session__time {
    max-width: 140px;
    margin-top: 32px;

    &::before {
      display: none;
    }
  }

  .event-session__content {


    &::before {
      width: 20px;
      top: 47px;
    }

    &::after {
      left: 20px;
      top: 45px;
    }
  }

  .event-session__report:not(:last-child) {
    margin-bottom: 15px;
  }

}

@media screen and (max-width: 640px) {

  .event-session {
    display: block;
    margin-top: 20px;
    margin-bottom: 20px;
  }

  .event-session__content {
    border-bottom: 1px solid gainsboro;
  }

  .event-session__time {
    width: 100%;
    max-width: unset;
    margin-top: 0;
    display: flex;
    justify-content: center;
    background-image: none;
  }

  .event-session__time::before {
    display: block;
    left: 1px;
    transform: translate(-50%, 0);
    z-index: 1;
  }

  .event-session__time::after {
    content: '';
    display: block;
    width: calc(50% - 60px);
    height: 50%;
    position: absolute;
    left: 0;
    top: 50%;
    transform: unset;
    background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0) 0%, gainsboro 0%, gainsboro calc(0% + 1px), rgba(255, 255, 255, 0) calc(0% + 1px), rgba(255, 255, 255, 0));
    border-left: 1px solid gainsboro;
    border-radius: 0;
  }

}
</style>
