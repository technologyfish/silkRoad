<template>
  <div class="contact-page">
    <Header />
    <main class="contact-hero">
      <div class="about-section container">
        <div class="about-layout">
          <!-- Top: portrait left, heading + first paragraph right -->
          <div class="about-top">
            <div class="portrait-wrap">
              <img
                class="portrait-img"
                src="../assets/images/home/aboutme.jpg"
                alt="Edric"
                width="433"
                height="580"
              />
            </div>

            <div class="about-intro">
              <h2 class="about-title">ABOUT<br />ME</h2>
              <p class="about-text">
                I’m Edric, the creator of this project. It began with my research on intangible cultural heritage in Xinjiang, my father’s hometown, where I interviewed Uyghur, Kazakh, Mongol, and Kyrgyz oral performers and studied how heritage preservation is governed. Writing about it left one question unresolved for me: when a community’s story is performed on stage, who gets to decide how it is told? This project is my attempt to answer it in practice, by putting the question to students in a classroom.
              </p>
            </div>
          </div>

          <!-- Bottom: remaining paragraphs span full width, below the portrait -->
          <p class="about-text">
            Outside this project, I serve as captain and teaching assistant for my school’s Speech and Debate program, the Barracudas, and as editor-in-chief of our school newspaper, the Cuda Column. I have also worked with college professors on academic research, and my interests span comparative literature, sociology and anthropology, politics, and international relations.
          </p>

          <p class="about-text">
            Questions about the framework, pilot inquiries, and feedback are welcome at
            <a class="about-email" href="mailto:edriczrwang@gmail.com">edriczrwang@gmail.com</a>.
          </p>
        </div>

        <div class="about-divider" aria-hidden="true"></div>
      </div>

      <div class="contact-container">
        <div class="contact-items">
          <a class="contact-item item-green" href="mailto:edriczrwang@gmail.com">
            <div class="item-left">Contact Email</div>
            <div class="item-right"><img src="../assets/images/home/icon-email.png" alt="" /></div>
          </a>
          <a
            class="contact-item item-white"
            href="https://www.youtube.com/channel/UCSenox9n96GImoU0JnuX6TQ"
            target="_blank"
            rel="noopener noreferrer"
          >
            <div class="item-left">YouTube</div>
            <div class="item-right"><img src="../assets/images/home/YouTube.png" alt="" /></div>
          </a>
          <a class="contact-item item-brown" href="#/voice">
            <div class="item-left">Voices of Our Own Participation</div>
            <div class="item-right"><img src="../assets/images/home/link.png" alt="" /></div>
          </a>
          <a class="contact-item item-gray" href="mailto:edriczrwang@gmail.com">
            <div class="item-left">Collaboration Inquiry</div>
            <div class="item-right"><img src="../assets/images/home/join.png" alt="" /></div>
          </a>
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

.about-section.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 40px;
}

.about-layout {
  display: flex;
  flex-direction: column;
  width: 890px;
  max-width: 100%;
  margin: 0 auto;
}

.about-top {
  display: flex;
  align-items: flex-start;
  gap: 90px;
  margin-bottom: 48px;
}

.portrait-wrap {
  position: relative;
  flex: 0 0 400px;
  max-width: 400px;
}

.portrait-img {
  position: relative;
  z-index: 1;
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  object-position: center top;
}

.about-intro {
  flex: 0 0 400px;
  max-width: 400px;
  min-width: 0;
  padding-top: 8px;
}

.about-title {
  font-family: $font-serif;
  font-size: 68px;
  font-weight: 700;
  font-style: italic;
  margin: 0 0 28px;
  line-height: 0.98;
  letter-spacing: 0.02em;
  color: #111;
}

.about-text {
  font-family: $font-serif;
  font-size: 18px;
  line-height: 1.75;
  color: #1a1a1a;
  margin: 0 0 1.35em;
  text-align: left;
}

.about-email {
  color: inherit;
  text-decoration: underline;
  text-underline-offset: 3px;

  &:hover {
    color: $color-brown-dark;
  }
}

.about-divider {
  width: 890px;
  max-width: 100%;
  height: 1px;
  margin: 8px auto 0;
  background: #b89a6d;
  opacity: 0.85;
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
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.05);
  text-decoration: none;
  color: inherit;
  transition: transform 0.2s ease, box-shadow 0.2s ease;

  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
  }
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

.item-green { background: #adc3bb; }
.item-white { background: #ffffff; }
.item-brown { background: #d1c4b4; }
.item-gray { background: #e9e8e6; }

.contact-container {
  margin-top: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

@media (max-width: 1100px) {
  .about-top {
    gap: 72px;
  }

  .portrait-wrap {
    flex-basis: 340px;
  }

  .about-intro {
    flex-basis: 340px;
  }
}

@media (max-width: 960px) {
  .about-top {
    flex-direction: column;
    gap: 36px;
  }

  .portrait-wrap {
    flex-basis: auto;
    width: 100%;
    max-width: 340px;
  }

  .about-intro {
    flex-basis: auto;
    max-width: none;
    width: 100%;
  }

  .about-title {
    font-size: 48px;
  }

  .about-text {
    font-size: 16px;
  }

  .contact-item {
    width: calc(100% - 40px);
    max-width: 890px;
    height: auto;
    min-height: 100px;
    padding: 24px 28px;
  }

  .item-left {
    font-size: 28px;
  }
}

@media (max-width: 700px) {
  .contact-hero {
    padding: 48px 0 80px;
  }

  .about-section.container {
    padding: 0 24px;
  }

  .portrait-wrap {
    max-width: 280px;
  }

  .about-title {
    font-size: 40px;
  }

  .item-left {
    font-size: 22px;
  }
}
</style>
