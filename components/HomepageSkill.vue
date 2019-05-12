<template>
  <div class="tool-box-item">
    <h1><font-awesome-icon :icon="['fab', 'python']" /></h1>
  </div>
</template>

<style>
.tool-box-item {
  padding: 0.5rem 4rem;
  width: 9rem;
  text-align: center;
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
@media (max-width: 767px) {
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
}
</style>
