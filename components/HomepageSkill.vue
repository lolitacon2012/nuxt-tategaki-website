<template>
  <div :class="{ 'hide-on-mobile': hideOnMobile }" class="tool-box-item">
    <font-awesome-icon class="tool-box-item-icon" :icon="[prefix, context]" />
  </div>
</template>
<script>
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
  }
}
</script>
<style>
.tool-box-item {
  padding: 0;
  width: 10rem;
}

.tool-box-item > .tool-box-item-icon {
  width: 5rem;
  height: 5rem;
}

@media (max-width: 768px) {
  .tool-box-item {
    padding: 1rem 0;
    text-align: center;
    width: 33.333333333333333333333%;
  }
  .tool-box-item > .tool-box-item-icon {
    width: 3.5rem;
    height: 3.5rem;
  }
  .hide-on-mobile {
    display: none;
  }
}
</style>
