<template>
  <div class="home-page">
    <Header />
    <main class="main-content">
      <!-- Hero Section -->
      <section class="banner-section">
        <div class="banner-content">
          <div class="banner-left">
            <h1>Exploring <br> the intangible <br> cultural <br>heritage of <br>the Silk Road</h1>
            <div class="banner-button"></div>
          </div>

          <div class="banner-right">
            <img src="../assets/images/home/img_1.png" alt="Silk Road Heritage" class="hero-right-img" />
          </div>
        </div>
      </section>

      <!-- Intro Section -->
      <section class="intro-section">
        <div class="title">Hero Section</div>
        <div class="desc">Stories live because people keep telling them.</div>
        <div class="intro-cards">
          <div class="card">
            <img src="../assets/images/home/img_4.png" alt="Understand" />
          </div>
          <div class="card">
            <img src="../assets/images/home/img_3.png" alt="Preserve" />
          </div>
          <div class="card">
            <img src="../assets/images/home/img_2.png" alt="VOUCHER BERLIN" />
          </div>
        </div>
      </section>

      <!-- Opening Statement -->
      <section class="opening-statement-section">
        <div class="title">Opening Statement</div>
        <div class="opening-box">
          <p>
            For generations, stories have traveled through voices.<br>
            They have been spoken, sung, remembered, and performed.
            Some of them are still carried this way today.
          </p>

          <p>
            During my fieldwork in Xinjiang, I encountered cultural traditions not as something preserved behind glass,<br>
            but as something still being sung, performed, taught, and reshaped by the people who carry them.<br>
            I watched performances of Maqam, Muqam, Jangar, Mongolian Long Song, and Aitys, and spoke with performers,<br>
            inheritors, teachers, and researchers about what these traditions mean to them today.
          </p>

          <p>
            These experiences made me interested not only in what a tradition is,<br>
            but in what allows it to remain meaningful over time. I began to think
            about what changes<br> when a tradition moves between generations, places,
            languages, and different forms of performance.
          </p>
        </div>
      </section>

      <!-- Vision Section -->
      <section class="vision-section">
        <h2 class="title">Vision</h2>

        <div class="vision-content">
          <div class="vision-image-wrapper">
            <img src="../assets/images/home/img_5.png" alt="Vision" />
          </div>

          <div class="vision-text">
            <div class="vision-text-bar"></div>
            <p>We envision a future in which oral and musical traditions are not<br>
              only preserved as cultural heritage, but remain part of the present.</p>
            <p>Traditions such as Manas have traveled across time through voice,<br>
              memory, music, and performance. Their forms may change, but they continue<br>
              to connect people with stories, histories, and communities.</p>
            <p>We hope these traditions can continue to spark curiosity, conversation,<br>
              and new connections across generations and cultures.</p>
          </div>
        </div>
      </section>

      <!-- Mission Section -->
      <section class="mission-section">
        <h2 class="mission-title">Mission</h2>
        <div class="mission-text">
          <p>Our mission is to create a clear way for young audiences to experience, <br></br>understand, and take part in these traditions.</p>
          <p>Through <strong class="caps">PERFORMANCE</strong>, we begin with the traditions as they are experienced in sound, music, instruments, movement, and live performance. Through <strong class="caps">LISTEN</strong>, we document the perspectives of the performers, inheritors, teachers, and researchers who continue to carry and interpret these traditions today.</p>
          <p>Finally, through <strong class="highlight">VOICE OF OUR OWN</strong>, we focus on Manas and provide scripts,<br> educational resources, and performance tools that allow young people<br> and educators to engage with the epic in a thoughtful and participatory way.</p>
          <p class="mission-conclude">Together, these three parts move from experiencing a tradition,
            to understanding the people<br> behind it,
            to creating a meaningful opportunity for a new generation to participate.</p>
        </div>
      </section>

      <!-- Fieldwork Map Section -->
      <section class="fieldwork-map-section">
        <h2 class="fieldwork-title">Fieldwork Map</h2>
        <div class="map-content">
          <div class="map-legend">
            <ul>
              <li>Kashgar | 喀什</li>
              <li>Akqi | 阿合奇</li>
              <li>Tacheng | 塔城</li>
              <li>Urumqi | 乌鲁木齐</li>
            </ul>
          </div>
          <div class="map-image">
            <img src="../assets/images/home/img_6.png" alt="Fieldwork Map" />
          </div>
        </div>
      </section>

      <!-- Call to Action Section (bottom images) -->
      <section class="call-to-action-section">
        <div class="cta-item">
          <img src="../assets/images/home/btn_2.png" alt="CTA 1" />
        </div>
        <div class="cta-item">
          <img src="../assets/images/home/btn_3.png" alt="CTA 2" />
        </div>
        <div class="cta-item">
          <img src="../assets/images/home/btn_4.png" alt="CTA 3" />
        </div>
      </section>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.home-page {
  font-family: 'SourceHanSansCN-Regular';
  color: $color-text-dark;
  line-height: 1.6;
  /* page background image */
  background-image: url('/src/assets/images/home/bg.png');
  background-repeat: repeat;
  background-position: top center;
  background-size: auto;
}

.main-content {
  width: 100%;
  max-width: 1253px;
  margin: 0 auto;
}

/* Hero Section */
.banner-section {
  padding: 80px 0;
  .banner-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    //gap: 40px;
  }

  .banner-left {
    padding-left: 50px;

    h1 {
      font-family: 'SourceHanSansCN-Regular';
      font-size: 60px;       /* updated: 80px */
      line-height: 80px;     /* updated: 80px */
      color: #0e0a06;
      font-weight: 500;
      font-style: italic;
      margin: 0 0 80px 0;
    }

    .banner-button {
      width: 245px;
      height: 100px;
      background: url("../assets/images/home/btn_1.png") no-repeat;
      background-size: 100% 100%;
      display: inline-block;
      border: none;
      width: 245px;
      height: 100px;
      cursor: pointer;
    }
  }

  .banner-right {
    position: relative;
    width: 740px; /* user requested width */
    height: auto;
    display: flex;
    align-items: center;
    justify-content: center;
  }



  .banner-right-img {
    position: relative;
    height: auto;
  }


  @media (max-width: 900px) {
    .hero-content {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .hero-right {
      width: 320px;
      height: 260px;
    }

    .hero-right-img {
      width: 300px;
      height: 220px;
    }
  }
}

/* Hero Section */
.hero-section {
  padding: 80px 0;
  //background-color: $color-background-light;

  .hero-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    //gap: 40px;
  }

  .hero-left {
    //flex: 1;
    //max-width: 520px;
    padding-left: 50px;

    h1 {
      font-family: 'SourceHanSansCN-Regular';
      font-size: 60px;       /* updated: 80px */
      line-height: 80px;     /* updated: 80px */
      color: #0e0a06;
      font-weight: 500;
      font-style: italic;
      margin: 0 0 80px 0;
    }

    .hero-button {
      width: 245px;
      height: 100px;
      background: url("../assets/images/home/btn_1.png") no-repeat;
      background-size: 100% 100%;
      display: inline-block;
      border: none;
      width: 245px;
      height: 100px;
      cursor: pointer;
    }
  }

  .hero-right {
    position: relative;
    width: 740px; /* user requested width */
    height: auto;
    display: flex;
    align-items: center;
    justify-content: center;
  }



  .hero-right-img {
    position: relative;
    //width: 751px; /* match requested width */
    height: auto;
    //object-fit: cover;
    //box-shadow: 0 12px 30px rgba(0,0,0,0.18);
    //background: #fff;
  }


  @media (max-width: 900px) {
    .hero-content {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .hero-right {
      width: 320px;
      height: 260px;
    }

    .hero-right-img {
      width: 300px;
      height: 220px;
    }
  }
}

/* Intro Section */
.intro-section {
  text-align: center;
  padding: 20px 0;

  .title {
    font-size: 58px;
    margin-bottom: 20px;
    color: #0e0a06;
  }

  .desc {
    color: 0e0a06;
    font-size: 24px;
    margin-bottom: 100px;

  }

  .intro-cards {
    display: flex;
    justify-content: center;
    gap: 65px;
    flex-wrap: wrap;
    margin-bottom: 20px;

    .card {
      text-align: center;

      img {
        width: 357px;
        height: 357px;
        border-radius: 50%;
        object-fit: cover;
        margin-bottom: 15px;
        //box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      }
    }
  }
}

/* Opening Statement Section */
.opening-statement-section {
  padding: 60px 20px;
  text-align: center;

  .title {
    font-size: 58px;
    margin-bottom: 40px;
    color: #0e0a06;
  }

  .opening-box {
    margin: 0 auto;
    max-width: 100%;
    background-color: #adc3bb;
    padding: 34px 10px;
    border-radius: 2px;
    text-align: center;
  }

  .opening-box p {
    font-family: 'font-primary';
    margin: 0 0 12px 0;
    color: #fff;
    font-size: 18px;
    line-height: 1.7;
    margin-bottom: 30px;
  }
  .opening-box p:last-of-type{
    margin-bottom: 0;
  }
}

/* Vision Section */
.vision-section {
  padding: 80px 0;
  text-align: center;

  h2.title {
    font-family: $font-serif;
    font-size: 38px;
    color: #222;
    font-weight: 500;
    margin-bottom: 40px; /* Adjusted margin-bottom for title as per design */
  }

  .vision-content {
    display: flex;
    align-items: flex-start; /* Align items at the start as per design */
    justify-content: center;
    gap: 50px;
    margin: 0 auto;
  }

  .vision-image-wrapper { /* New wrapper for image and text overlay */
    position: relative;
    width: 357px;
    height: 357px;
    img {
      max-width: 100%;
      height: auto;
      display: block;
    }
  }

  .vision-text { /* Right side text content */
    flex: 0 0 740px; /* Fixed width for text box */
    text-align: left;
    font-family: $font-serif;

    .vision-text-bar { /* Horizontal bar above text */
      position: relative;
      width: 835px;
      height: 20px;
      background-color: #adc3bb;
      margin-top: 20px;
      margin-bottom: 40px;
      margin-left: -100px;
    }

    p {
      text-align: right;
      font-size: 18px;
      margin-bottom: 15px;

      &:last-child {
        margin-bottom: 0;
      }
    }
  }
}

/* Mission Section */
.mission-section {
  padding: 100px 0;
  text-align: center;

  .mission-title {
    font-family: $font-serif;
    font-size: 48px;
    font-weight: 400;
    color: #0e0a06;
    margin-bottom: 30px;
  }

  .mission-text {
    max-width: 890px;
    margin: 0 auto;
    text-align: center;
    font-family: $font-serif;
    font-size: 21px;
    color: #222;
    line-height: 1.2;
  }

  .mission-text p {
    margin-bottom: 22px;
  }
  
  .mission-conclude {
    margin-top: 24px;
    font-size: 20px;
    line-height: 1.6;
    text-align: center;
    font-style: normal;
    color: #222;
  }
  .caps {
    font-weight: 700;
    letter-spacing: 1px;
  }

  .highlight {
    color: #fff;
    display: inline-block;
    background: #854529;
    padding: 4px 8px;
    border-radius: 3px;
    font-weight: 700;
  }
}

/* Fieldwork Map Section */
.fieldwork-map-section {
  text-align: center;
 
  h2 {
    font-size: 2.5em;
    margin-bottom: 40px;
    color: #4A4A4A;
  }

  .fieldwork-title {
    font-family: $font-serif;
    font-size: 48px;
    color: #0e0a06;
    font-weight: 400;
    //margin-bottom: 40px;
  }

  .map-content {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 50px;
    flex-wrap: wrap;
  }

  .map-legend ul {
    list-style: none;
    padding: 0;
    text-align: left;
    margin: 0;
  }

  .map-legend ul li {
    position: relative;
    padding-left: 28px;
    margin-bottom: 18px;
    color: #854529;
    font-size: 20px;
    line-height: 1.4;
    font-weight: 600;
  }

  .map-legend ul li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 8px;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: #854529;
  }

   .map-image{
     position: relative;
     top: 120px;
   }
  .map-image img {
    max-width: 760px;
    width: 100%;
    height: auto;
    border-radius: 0;
    box-shadow: none;
    display: block;
  }

  .map-image img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
    //box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  }
}

/* Call to Action Section */
.call-to-action-section {
  min-height: 520px;
  padding: 0 0 70px 0;
  display: flex;
  align-items: flex-end; /* place buttons toward bottom of background image */
  justify-content: center;
  gap: 30px;
  flex-wrap: wrap;
  background-image: url('/src/assets/images/home/img_7.png');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;

  .cta-item {
    position: relative;
    text-align: center;

    img {
      height: auto;
      object-fit: cover;
    }
  }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .hero-section {
    flex-direction: column;
    text-align: center;
  }

  .hero-text {
    padding-right: 0;
    margin-bottom: 30px;
  }

  .vision-content,
  .map-content {
    flex-direction: column;
  }
}

</style>
