<template>
  <div>
    <nuxt />
  </div>
</template>

<style>
html {
  font-family: Source Sans Pro, -apple-system, BlinkMacSystemFont, Segoe UI,
    Roboto, Helvetica Neue, Microsoft YaHei, Source Han Sans SC,
    Noto Sans CJK SC, Arial, sans-serif;
  /* font-family: -apple-system, BlinkMacSystemFont, Helvetica Neue, PingFang SC,
    Microsoft YaHei, Source Han Sans SC, Noto Sans CJK SC, WenQuanYi Micro Hei,
    sans-serif; */
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--pink {
  display: inline-block;
  border-radius: 6px;
  border: 2px solid rgb(239, 147, 186);
  color: rgb(239, 147, 186);
  text-decoration: none;
  padding: 10px 30px;
  transition: 0.3s;
}

.button--pink:hover {
  color: #fff;
  background-color: rgb(239, 147, 186);
}

.button--grey {
  display: inline-block;
  border-radius: 6px;
  border: 2px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  transition: 0.3s;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.tategaki-text {
  -webkit-writing-mode: vertical-rl;
  -moz-writing-mode: vertical-rl;
  -ms-writing-mode: vertical-rl;
  -writing-mode: vertical-rl;
}
</style>
