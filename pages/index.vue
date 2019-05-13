<template>
  <div>
    <section class="container container-pink-gradient container-full-height">
      <Triangle />
      <h1 class="title title-rt">
        <transition name="fade" mode="out-in">
          <span :key="lang_reading">{{ lang_reading }}</span>
        </transition>
      </h1>
      <h1 class="title">紀葉清</h1>
      <img class="title--image" src="@/static/img/sakura.png" />
      <h2 class="subtitle">
        <span class="avoidwrap">Front-End Engineer, </span>Linguaphile, Pilgrim
      </h2>
      <div class="links">
        <nuxt-link to="/" class="button--pink"
          >Awesome Pages Coming Soon</nuxt-link
        >
      </div>
    </section>
    <section class="container container-full-height">
      <div class="content-foreground">
        <div class="section-title-container flex-start ">
          <h1 class="section-title">
            I'm a Software Engineer.
          </h1>
          <h1 class="section-title-footnote">
            RN Developer @Shopee Pte. Ltd.
          </h1>
        </div>
        <div class="tool-box-container">
          <div class="tool-box-container-row">
            <HomepageSkill
              v-for="skill in skills"
              :key="skill.context"
              :context="skill.context"
              :hide-on-mobile="skill.hideOnMobile"
            />
          </div>
        </div>
        <div class="section-title-container flex-end ">
          <h1 class="section-title">
            <span class="avoidwrap">Here are some</span>
            <span class="avoidwrap">awesome tools</span>
            <span class="avoidwrap">I'd love to use.</span>
          </h1>
          <h1 class="section-title-footnote">
            <span class="avoidwrap">Play with </span>
            <span class="avoidwrap">
              <span
                ><a
                  target="_blank"
                  class="highlight"
                  href="https://www.coursera.org/account/accomplishments/specialization/certificate/QQEHCXPXJKUJ"
                  >Deep Learning</a
                ></span
              >also.</span
            >
          </h1>
        </div>
      </div>
      <div class="canvas-background">
        <canvas id="canvas"></canvas>
      </div>
    </section>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'

import HomepageSkill from '~/components/HomepageSkill'
import Triangle from '~/components/Triangle'
const RT_LANGUAGES = [
  'Kino Hasumi',
  'きのはすみ',
  'Kỷ Diệp Thanh',
  '기　잎　청',
  'Jì Yè Qīng'
]
const rnd = (min, max) => {
  return Math.floor(Math.random() * (max - min + 1) + min)
}
export default {
  components: {
    HomepageSkill,
    Triangle
  },
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
      time_interval_ref: null,
      skills: [
        { context: 'react', hideOnMobile: false },
        { context: 'vuejs', hideOnMobile: false },
        { context: 'js-square', hideOnMobile: false },
        { context: 'html5', hideOnMobile: false },
        { context: 'css3-alt', hideOnMobile: false },
        { context: 'java', hideOnMobile: false },
        { context: 'python', hideOnMobile: false },
        { context: 'ubuntu', hideOnMobile: false },
        { context: 'node-js', hideOnMobile: false },
        { context: 'github', hideOnMobile: true }
      ]
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
    this.renderTriangle()
    window.onresize = () => {
      this.renderTriangle()
    }
  },
  methods: {
    renderTriangle: (canvas = document.getElementById('canvas')) => {
      if (!canvas) {
        return
      }
      const max = Math.max(window.innerWidth, window.innerHeight)
      const canvasWidth = (canvas.width = max)
      const canvasHeight = (canvas.height = max)
      const ctx = canvas.getContext('2d')
      ctx.clearRect(0, 0, canvas.width, canvas.height)
      const heightScale = 0.866
      ctx.fillStyle = 'rgb(0,0,0)'
      ctx.fillRect(0, 0, canvasWidth, canvasHeight)
      ctx.lineWidth = 1
      const hueStart = 335
      const triSide = 120
      const halfSide = triSide / 2
      const rowHeight = Math.floor(triSide * heightScale)
      const columns = Math.ceil(canvasWidth / triSide) + 1
      const rows = Math.ceil(canvasHeight / rowHeight)
      let col, row
      for (row = 0; row < rows; row++) {
        const hue = hueStart + row * 3
        for (col = 0; col < columns; col++) {
          let x = col * triSide
          const y = row * rowHeight
          let clr
          if (row % 2 !== 0) {
            x -= halfSide
          }
          clr = 'hsl(' + hue + ', 70%, ' + rnd(94, 100) + '%)'
          ctx.fillStyle = clr
          ctx.strokeStyle = clr
          ctx.beginPath()
          ctx.moveTo(x, y)
          ctx.lineTo(x + halfSide, y + rowHeight)
          ctx.lineTo(x - halfSide, y + rowHeight)
          ctx.closePath()
          ctx.fill()
          ctx.stroke()
          clr = 'hsl(' + hue + ', 70%, ' + rnd(94, 100) + '%)'
          ctx.fillStyle = clr
          ctx.strokeStyle = clr
          ctx.beginPath()
          ctx.moveTo(x, y)
          ctx.lineTo(x + triSide, y)
          ctx.lineTo(x + halfSide, y + rowHeight)
          ctx.closePath()
          ctx.fill()
          ctx.stroke()
        }
      }
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  overflow: auto;
  position: relative;
}

.container-full-height {
  height: 100vh;
  min-height: 768px;
}

.container-pink-gradient {
  background: rgba(255, 255, 255, 1);
  background: -moz-linear-gradient(
    -45deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 46%,
    rgba(252, 233, 241, 1) 100%
  );
  background: -webkit-gradient(
    left top,
    right bottom,
    color-stop(0%, rgba(255, 255, 255, 1)),
    color-stop(46%, rgba(255, 255, 255, 1)),
    color-stop(100%, rgba(252, 233, 241, 1))
  );
  background: -webkit-linear-gradient(
    -45deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 46%,
    rgba(252, 233, 241, 1) 100%
  );
  background: -o-linear-gradient(
    -45deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 46%,
    rgba(252, 233, 241, 1) 100%
  );
  background: -ms-linear-gradient(
    -45deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 46%,
    rgba(252, 233, 241, 1) 100%
  );
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 1) 46%,
    rgba(252, 233, 241, 1) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#ffffff', endColorstr='#fce9f1', GradientType=1 );
}

.title {
  display: block;
  font-weight: 100;
  font-size: 7rem;
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
}

.subtitle {
  font-weight: 100;
  font-size: 2rem;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
  text-align: center;
}

.section-title-container {
  padding: 0 10rem;
}

.section-title-container.flex-start {
  align-self: flex-start;
  text-align: left;
}

.section-title-container.flex-end {
  align-self: flex-end;
  text-align: right;
}

.section-title {
  display: block;
  font-weight: 100;
  font-size: 4rem;
}

.section-title-footnote {
  display: block;
  font-weight: 100;
  font-size: 1.2rem;
}

.links {
  padding-top: 15px;
}

.canvas-background {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  overflow: hidden;
  z-index: 0;
}

.content-foreground {
  z-index: 1000;
  width: 100%;
  display: flex;
  height: 100vh;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  text-align: center;
}

.tool-box-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  -webkit-box-decoration-break: clone;
  box-decoration-break: clone;
  background: linear-gradient(to right, #ddbbff, #ffeeaa);
  padding: 6rem 0;
}

.tool-box-container-row {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
  flex-wrap: wrap;
}

.overflow-hidden {
  overflow: hidden;
}
@media (max-width: 1024px) {
  .section-title {
    font-size: 3rem;
  }
  .section-title-container {
    padding: 0 6rem;
  }
  .section-title-footnote {
    font-size: 1.1rem;
  }
}
@media (max-width: 768px) {
  .container-full-height {
    min-height: 100vmax;
  }
  .title {
    font-size: 5rem;
    letter-spacing: 0.5rem;
  }
  .title-rt {
    font-size: 1.7rem;
    letter-spacing: 0.1rem;
    transition: 0.3s;
    line-height: 1.7rem;
  }
  .subtitle {
    font-size: 1.8rem;
    padding-bottom: 25px;
    max-width: 16rem;
  }

  .section-title-container {
    padding: 0;
  }

  .section-title-container.flex-start {
    align-self: center;
    text-align: center;
  }

  .section-title-container.flex-end {
    align-self: center;
    text-align: center;
  }

  .section-title {
    font-size: 1.8rem;
  }

  .section-title-footnote {
    font-size: 1rem;
  }

  .tool-box-container {
    padding: 0;
  }
}
</style>
