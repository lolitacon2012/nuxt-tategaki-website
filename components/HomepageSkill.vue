<template>
  <div
    :class="{
      'hide-on-mobile': hideOnMobile,
      'element-scaled': elementVisible
    }"
    class="tool-box-item"
  >
    <font-awesome-icon class="tool-box-item-icon" :icon="[prefix, context]" />
  </div>
</template>
<script>
import { elementInViewport } from './utils.js'
export default {
  props: {
    prefix: {
      type: String,
      default: 'fab'
    },
    context: {
      type: String,
      default: ''
    },
    hideOnMobile: {
      type: Boolean,
      default: false
    }
  },
  data: function() {
    return {
      elementVisible: true
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.elementVisible = elementInViewport(this.$el)
    }
  }
}
</script>
<style>
.tool-box-item {
  padding: 0;
  width: 10rem;
  transition: transform 1.2s;
  -webkit-transition: -webkit-transform 1.2s;
  transform: scale(0);
  -webkit-transform: scale(0);
  transition-timing-function: ease-in-out;
}

.tool-box-item > .tool-box-item-icon {
  width: 4.8rem;
  height: 4.8rem;
}

.element-scaled {
  transform: scale(1);
  -webkit-transform: scale(1);
}

@media (max-width: 768px) {
  .tool-box-item {
    padding: 1rem 0;
    text-align: center;
    width: 33.333333333333333333333%;
  }
  .tool-box-item > .tool-box-item-icon {
    width: 3.2rem;
    height: 3.2rem;
  }
  .hide-on-mobile {
    display: none;
  }
}
</style>
