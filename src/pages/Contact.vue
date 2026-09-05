<template>
  <div class="contact-page">
    <Header />
    <main class="contact-hero">
      <div class="contact-inner container">
        <div class="left-decor">
          <img class="contact-img" src="../assets/images/home/contact.png" alt="contact" width="433" height="465" />
        </div>

        <div class="right-content">
          <h2 class="about-title">ABOUT <br> ME</h2>
          <p class="about-desc">copywriting copywriting copywriting copywriting</p>
        </div>

      </div>
      <div class="contact-container">
        <div class="contact-items">
          <div class="contact-item item-green">
            <div class="item-left">Contact Email</div>
            <div class="item-right"><img src="../assets/images/home/icon-email.png" alt="email" /></div>
          </div>
          <div class="contact-item item-white">
            <div class="item-left">YouTube</div>
            <div class="item-right"><img src="../assets/images/home/YouTube.png" alt="youtube" /></div>
          </div>
          <div class="contact-item item-brown">
            <div class="item-left">Voice of Our Own Participation</div>
            <div class="item-right"><img src="../assets/images/home/link.png" alt="link" /></div>
          </div>
          <div class="contact-item item-gray">
            <div class="item-left">Collaboration Inquiry</div>
            <div class="item-right"><img src="../assets/images/home/join.png" alt="join" /></div>
          </div>
        </div>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.contact-hero {
  background: #f8f7ef;
  padding: 80px 0 120px;
}
.contact-inner.container {
  max-width: 1366px;
  margin: 0 auto;
  display: flex;
  align-items: flex-start;
  gap: 60px;
  position: relative;
}
.left-decor { position: relative; }
.contact-img {
  width: 433px;
  height: 465px;
  object-fit: cover;
  display: block;
}
.right-content {
  flex: 1;
  padding-top: 12px;
}
.about-title {
  font-family: $font-serif;
  font-size: 68px;
  font-weight: 800;
  font-style: italic;
  margin: 0 0 12px;
  line-height: 0.95;
}
.about-desc {
  color: #444;
  margin-bottom: 40px;
  font-size: 32px;
}
.contact-items {
  display: flex;
  flex-direction: column;
  gap: 24px;
}
.contact-item {
  width: 890px;
  height: 163px;
  border-radius: 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 28px;
  box-sizing: border-box;
  box-shadow: 0 8px 18px rgba(0,0,0,0.05);
}
.item-left {
  font-family: $font-serif;
  font-size: 38px;
  color: #0e0a06;
}
.item-right img {
  width: 100%;
  height: 100%;
}
.icon-email{

}
.item-green { background: #adc3bb; }
.item-white { background: #ffffff; }
.item-brown { background: #d1c4b4; }
.item-gray { background: #e9e8e6; }

.contact-container{
  margin-top: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
@media (max-width: 900px) {
  .contact-inner.container { flex-direction: column; align-items: center; }
  .left-decor { order: -1; }
  .contact-btn { width: calc(100% - 40px); height: 56px; border-radius: 28px; }
}
</style>

