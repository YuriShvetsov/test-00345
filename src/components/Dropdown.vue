<template>
  <div class="dropdown">
    <div class="dropdown__opener"
      v-bind:class="{ 'dropdown__opener_active': isOpen, 'dropdown__opener_dark': openerDark, 'dropdown__opener_center': openerCenter }"
      v-bind:style="hasContent ? {} : { cursor: 'default' }"
      v-on:click="toggle"  
    > 
      <div class="dropdown__opener-header">
        <slot name="opener"></slot>
        <i class="dropdown__opener-caret icofont-caret-up" v-if="hasContent"></i>
      </div>
      <div class="dropdown__opener-desc">
        <slot name="desc"></slot>
      </div>
    </div>
    <div class="dropdown__content"
      ref="content"
      v-show="isOpen"
      v-if="hasContent"
    >
      <slot name="content"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'dropdown',
  props: {
    opened: {
      type: Boolean,
      default: false
    },
    openerDark: {
      type: Boolean,
      default: false
    },
    openerCenter: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      isOpen: false,
      hasContent: true
    }
  },
  methods: {
    toggle() {
      this.isOpen = !this.isOpen
    }
  },
  created() {
    this.isOpen = this.opened
  },
  mounted() {
    this.hasContent = this.$refs.content.children.length > 0
  }
}
</script>

<style lang="scss" scoped>
.dropdown__opener {
  font-size: 22px;
  font-weight: 400;
  color: #333;
  cursor: pointer;
  user-select: none;
}
.dropdown__opener-header {
  width: 100%;
  padding: 5px;
  display: flex;
  align-items: center;
  background-color: transparent;
}
.dropdown__opener_center .dropdown__opener-header {
  justify-content: center;
}
.dropdown__opener_dark .dropdown__opener-header {
  color: #fff;
  background-color: lightslategray;
}
.dropdown__opener-caret {
  font-size: 16px;
  transform: rotate(180deg);
}
.dropdown__opener_active .dropdown__opener-caret {
  transform: unset;
}
.dropdown__opener-desc {
  font-size: 14px;
  color: #333;
}

@media screen and (max-width: 991px) {

  .dropdown__opener {
    font-size: 18px;
  }

}
</style>
