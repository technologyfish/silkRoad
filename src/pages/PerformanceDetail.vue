<template>
  <div class="performance-detail-page">
    <Header />
    <main class="main-content">
      <!-- Section 1: Video Area with Black Background - 1366 x 627 -->
      <section class="video-section">
        <div class="video-container">
          <div class="play-button">
            <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
          </div>
        </div>
      </section>

      <!-- Section 2: Title and Text -->
      <section class="text-section">
        <h1 class="main-title">{{ currentData.title }}</h1>
        <h2 class="sub-title">What Are We Watching?</h2>
        <p class="description">Copywriting, copywriting, copywriting, copywriting</p>
      </section>

      <!-- Section 3: Music & Instruments - Two centered rectangles -->
      <section class="instruments-section">
        <h2 class="section-title">Music &amp; Instruments</h2>
        <div class="instruments-cards">
          <div class="instrument-card green">
            <div class="card-left"></div>
            <div class="card-right">
              <p class="info-item">Name</p>
              <p class="info-item">Image</p>
              <p class="info-item">Role in the Performance</p>
              <p class="info-item">Cultural / Musical Context</p>
              <p class="info-item">Why It Matters</p>
            </div>
          </div>
          <div class="instrument-card tan"></div>
        </div>
      </section>

      <!-- Section 4: Oral / Cultural Context with Swiper -->
      <section class="context-section">
        <h2 class="section-title">Oral / Cultural Context</h2>
        <div class="carousel-wrap">
          <div class="carousel-arrow arrow-left" @click="swiperPrev">
            <img src="../assets/images/home/icon-left.png" alt="prev" />
          </div>
          <Swiper
            class="context-swiper"
            :modules="swiperModules"
            :slides-per-view="3"
            :space-between="20"
            :centered-slides="true"
            :loop="true"
            @swiper="onSwiper"
          >
            <SwiperSlide v-for="(slide, idx) in slides" :key="idx" v-slot="{ isActive }">
              <div :class="['slide-box', { 'slide-active': isActive }]">
                <img :src="slide.img" alt="slide" class="slide-img" />
              </div>
            </SwiperSlide>
          </Swiper>
          <div class="carousel-arrow arrow-right" @click="swiperNext">
            <img src="../assets/images/home/icon-right.png" alt="next" />
          </div>
        </div>
      </section>

      <!-- Section 5: Expert Perspective - video 718x335 -->
      <section class="expert-section">
        <h2 class="section-title">Expert Perspective</h2>
        <div class="expert-content">
          <div class="expert-video">
            <div class="play-button small">
              <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
            </div>
          </div>
          <div class="expert-text">
            <p>Copywriting, copywriting</p>
            <p>copywriting, copywriting</p>
            <p>Copywriting, copywriting</p>
            <p>copywriting, copywriting</p>
          </div>
        </div>
      </section>

      <!-- Section 6: Related Materials - 1233 width, 330x330 circles -->
      <section class="materials-section">
        <h2 class="section-title">Related Materials</h2>
        <div class="materials-circles">
          <div class="material-circle"></div>
          <div class="material-circle"></div>
          <div class="material-circle"></div>
        </div>
        <div class="next-button-wrap">
          <img src="../assets/images/home/next-btn.png" alt="NEXT" class="next-btn-img" @click="goToNext" />
        </div>
      </section>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'
import 'swiper/css'
import img01 from '../assets/images/home/img01.png'
import img02 from '../assets/images/home/img02.png'

const swiperModules = [Navigation]

const slides = [
  { img: img02 },
  { img: img01 },
  { img: img02 },
  // { img: img01 },
]

const swiperInstance = ref(null)

const onSwiper = (swiper) => {
  swiperInstance.value = swiper
}

const swiperPrev = () => {
  if (swiperInstance.value) swiperInstance.value.slidePrev()
}

const swiperNext = () => {
  if (swiperInstance.value) swiperInstance.value.slideNext()
}

const performanceData = {
  manas: { title: 'MANAS', zh: '《玛纳斯》' },
  muqam: { title: 'MUQAM', zh: '木卡姆' },
  jangar: { title: 'JANGAR', zh: '《江格尔》' },
  mongolian: { title: 'MONGOLIAN LONG SONG', zh: '蒙古族长调' },
  aitys: { title: 'AITYS', zh: '阿肯阿依特斯' },
}

const performanceOrder = ['manas', 'muqam', 'jangar', 'mongolian', 'aitys']

const getCurrentId = () => {
  const hash = window.location.hash
  const match = hash.match(/\/performance-detail\/(\w+)/)
  return match ? match[1] : 'manas'
}

const currentId = ref(getCurrentId())

const currentData = computed(() => {
  return performanceData[currentId.value] || performanceData.manas
})

const updateId = () => {
  currentId.value = getCurrentId()
}

onMounted(() => {
  window.addEventListener('hashchange', updateId)
})

onBeforeUnmount(() => {
  window.removeEventListener('hashchange', updateId)
})

const goToNext = () => {
  const currentIdx = performanceOrder.indexOf(currentId.value)
  const nextIdx = (currentIdx + 1) % performanceOrder.length
  const nextId = performanceOrder[nextIdx]
  window.location.hash = `#/performance-detail/${nextId}`
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.performance-detail-page {
  font-family: $font-sans;
  color: $color-text-dark;
  background-image: url('../assets/images/home/bg.png');
  background-repeat: repeat;
  background-position: top center;
  background-size: auto;
}

.main-content {
  width: 100%;
  max-width: 1253px;
  margin: 0 auto;
}

/* Section 1: Video */
.video-section {
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 627px;
  width: 100vw;
  margin-left: calc(-50vw + 50%);
  background-color: #000;
}

.video-container {
  width: 1366px;
  height: 627px;
  background-color: #000;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.play-button {
  width: 80px;
  height: 80px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  &.small {
    width: 60px;
    height: 60px;
  }
  .play-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
}

/* Section 2: Text */
.text-section {
  padding: 60px 20px;
  text-align: center;
}

.main-title {
  font-family: $font-serif;
  font-size: 72px;
  font-weight: 900;
  color: #0e0a06;
  margin: 0 0 60px;
  letter-spacing: 8px;
}

.sub-title {
  font-family: $font-serif;
  font-size: 32px;
  font-weight: 400;
  color: #0e0a06;
  margin: 0 0 20px;
}

.description {
  font-size: 18px;
  color: #0e0a06;
  font-style: italic;
}

/* Section 3: Instruments */
.instruments-section {
  padding: 60px 20px;
}

.section-title {
  font-family: $font-serif;
  font-size: 32px;
  font-weight: 400;
  text-align: center;
  margin-bottom: 40px;
  color: #0e0a06;
}

.instruments-cards {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
}

.instrument-card {
  width: 1016px;
  height: 368px;
  border-radius: 12px;
  display: flex;
  &.green { background-color: #aec3bc; }
  &.tan { background-color: #d1c4b4; }

  .card-left {
    width: 180px;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .card-right {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-end;
    padding-right: 60px;
    text-align: right;
  }
}

.info-item { font-size: 18px; color: #0e0a06; margin: 6px 0; }

/* Section 4: Carousel (Swiper) */
.context-section {
  padding: 60px 0;
}

.carousel-wrap {
  position: relative;
  width: 100%;
  max-width: 1100px;
  margin: 0 auto;
}

.carousel-arrow {
  position: absolute;
  top: 50%;
  z-index: 20;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;

  img {
    width: 36px;
    height: auto;
  }
  &:hover { opacity: 0.7; }

  &.arrow-left {
    left: 110px;
    transform: translateY(50%);
  }
  &.arrow-right {
    right: 110px;
    transform: translateY(50%);
  }
}

.context-swiper {
  width: 100%;
  padding-bottom: 15px;

  :deep(.swiper-slide) {
    display: flex;
    align-items: flex-end;
    justify-content: center;
    height: 540px;
  }
}

.slide-box {
  width: 270px;
  height: 410px;
  border-radius: 8px;
  overflow: hidden;
  transition: width 0.4s ease, height 0.4s ease;

  &.slide-active {
    width: 340px;
    height: 525px;
  }

  .slide-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
}

/* Section 5: Expert */
.expert-section {
  padding: 60px 20px;
  background-color: #e0e0e0;
  width: 100vw;
  margin-left: calc(-50vw + 50%);
}

.expert-content {
  max-width: 1233px;
  margin: 0 auto;
  display: flex;
  gap: 40px;
  align-items: center;
  justify-content: flex-start;
}

.expert-video {
  width: 718px;
  height: 335px;
  background-color: #000;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
}

.expert-text {
  text-align: left;
  p { font-size: 16px; color: #0e0a06; margin: 8px 0; }
}

/* Section 6: Materials */
.materials-section {
  padding: 60px 20px 100px;
  max-width: 1233px;
  margin: 0 auto;
}

.materials-circles {
  display: flex;
  justify-content: space-between;
  margin-bottom: 60px;
}

.material-circle {
  width: 330px;
  height: 330px;
  border-radius: 50%;
  background-color: #aec3bc;
}

.next-button-wrap {
  display: flex;
  justify-content: center;
}

.next-btn-img {
  cursor: pointer;
  height: auto;
  display: block;
  //transition: opacity 0.3s;
  //&:hover { opacity: 0.8; }
}

/* Responsive */
@media (max-width: 1100px) {
  .instrument-card { width: 100%; max-width: 1016px; }
  .video-container { width: 100%; }
  .expert-video { width: 100%; max-width: 718px; }
  .material-circle { width: 200px; height: 200px; }
}

@media (max-width: 900px) {
  .instrument-card {
    flex-direction: column;
    height: auto;
    padding: 30px;
    .card-left { width: 100%; height: 100px; }
    .card-right { align-items: center; text-align: center; padding-right: 0; }
  }
  .expert-content { flex-direction: column; }
}
</style>
