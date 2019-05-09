<template>
  <section class="container">
    <h1 class="title title-rt">
      <transition name="fade" mode="out-in">
        <span :key="lang_reading">{{ lang_reading }}</span>
      </transition>
    </h1>
    <h1 class="title">
      紀葉清
    </h1>
    <img class="title--image" src="@/static/img/sakura.png" />
    <h2 class="subtitle">
      Front-End Engineer, Linguaphile, Pilgrim
    </h2>
    <div class="links">
      <nuxt-link to="/" class="button--pink"
        >Awesome Pages Coming Soon</nuxt-link
      >
    </div>
  </section>
</template>

<script>
// import Logo from '~/components/Logo.vue'

const RT_LANGUAGES = [
  'Kino Hasumi',
  'きのはすみ',
  'Kỷ Diệp Thanh',
  '기　잎　청',
  'Jì Yè Qīng'
]
export default {
  // components: {
  //   Logo
  // }
  head() {
    return {
      title: 'Kino Hasumi - Website',
      meta: [
        {
          hid: 'Kino Hasumi - Personal Website',
          name: 'Kino Hasumi - Personal Website',
          content: 'Kino Hasumi - Personal Website Project'
        }
      ]
    }
  },
  data: () => {
    return {
      lang_reading: RT_LANGUAGES[RT_LANGUAGES.length - 1],
      time_interval_ref: null
    }
  },
  created() {
    let currentRtIndex = 0
    this.time_interval_ref = setInterval(() => {
      this.lang_reading = RT_LANGUAGES[currentRtIndex]
      currentRtIndex = (currentRtIndex + 1) % RT_LANGUAGES.length
    }, 5000)
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  display: block;
  font-weight: 100;
  font-size: 7rem;
  color: #35495e;
  letter-spacing: 1rem;
}

.title-rt {
  position: relative;
  font-size: 2.5rem;
  letter-spacing: 0.5rem;
  line-height: 2.5rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease-out;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0.1;
}

.title--image {
  display: inline-block;
  width: 50vw;
  max-width: 480px;
  height: auto;
  margin: 32px 0;
}

.subtitle {
  font-weight: 100;
  font-size: 2rem;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

@media (max-width: 767px) {
  .title {
    display: block;
    font-weight: 100;
    font-size: 5rem;
    color: #35495e;
    letter-spacing: 0.5rem;
  }
  .title-rt {
    font-size: 1.7rem;
    letter-spacing: 0.1rem;
    transition: 0.3s;
    line-height: 1.7rem;
  }
  .subtitle {
    font-weight: 100;
    font-size: 1.8rem;
    color: #526488;
    padding-bottom: 25px;
  }
}
</style>
