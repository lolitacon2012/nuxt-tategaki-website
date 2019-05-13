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

.tool-box-item > h1 {
  font-size: 5rem;
}

.tool-box-item > h2 {
  font-size: 1.2rem;
  font-weight: 100;
}

.tool-box-item > h3 {
  font-size: 0.8rem;
  font-weight: 100;
}
@media (max-width: 768px) {
  .tool-box-item {
    padding: 1rem 0;
    text-align: center;
    width: 33.333333333333333333333%;
  }

  .tool-box-item > h1 {
    font-size: 4rem;
  }

  .tool-box-item > h2 {
    font-size: 1rem;
    font-weight: 100;
  }

  .tool-box-item > h3 {
    font-size: 0.8rem;
    font-weight: 100;
  }

  .hide-on-mobile {
    display: none;
  }
}
</style>
