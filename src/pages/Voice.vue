<template>
  <div class="voice-page">
    <Header />
    <main>
      <!-- Banner Section -->
      <section class="voice-banner">
        <img src="../assets/images/home/banner.png" alt="Banner" />
      </section>
      <!-- (How to Use section moved below Scripts) -->

      <!-- Project Overview Section -->
      <section class="project-overview">
        <div class="container">
          <h2 class="overview-title">Project Overview</h2>
          <div class="overview-desc">
            <p>Voices of Our Own is a drama-education framework that asks students to consider how cultures are represented on stage and who holds the authority to tell a community’s stories. It grew out of fieldwork in Xinjiang with oral tradition performers, whose retellings showed how a narrative shifts depending on who carries it. Students move through a cycle of choosing, assigning, preparing, rehearsing, performing, and reflecting, building their own interpretation from a shared text.</p>
            <p>The framework was developed collaboratively. Four groups across China and the U.S. co-wrote a 38-page adaptation of the Manas epic, and the model was then piloted in six schools, where trained student facilitators ran workshops independently. A toolkit and video guide allow other classrooms to adopt the approach without outside support.</p>
          </div>

          <div class="cards-row">
            <div class="card">
              <div class="card-box">
                <p>Classrooms where students from different backgrounds can perform and reinterpret traditions with care, in conversation with the communities those traditions belong to.</p>
                <div class="card-title">Vision</div>
              </div>
            </div>

            <div class="card">
              <div class="card-box">
                <p>To give students a practical way to engage with cultural stories on their own terms, treating representation as a skill to be practiced and questioned rather than only discussed.</p>
                <div class="card-title">Mission</div>
              </div>
            </div>

            <div class="card">
              <div class="card-box">
                <p>To make the framework easy to replicate, so that students and teachers anywhere can lead workshops themselves.</p>
                <div class="card-title">Goals</div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- Scripts Section -->
      <section class="scripts-section">
        <div class="container">
          <h2 class="overview-title">Scripts</h2>

          <div class="scripts-list">
            <a class="script-row" :href="docUrl('Full-Length-WHEN MANAS IS SPOKEN_script.docx')" download>
              <div class="script-label">Full-Length Script</div>
              <div class="script-name">WHEN MANAS IS SPOKEN</div>
              <div class="script-download">
                <img src="../assets/images/home/icon-download.png" alt="download" />
              </div>
            </a>

            <a class="script-row" :href="docUrl('YouthVersion-当玛纳斯被歌唱时.docx')" download>
              <div class="script-label">Youth Version</div>
              <div class="script-name">WHEN MANAS IS SUNG</div>
              <div class="script-download">
                <img src="../assets/images/home/icon-download.png" alt="download" />
              </div>
            </a>
          </div>
        </div>
      </section>

      <!-- From Script to Stage Section -->
      <section class="stage-section">
        <div class="container">
          <h2 class="stage-title">FROM SCRIPT TO STAGE</h2>
          <p class="stage-subtitle">Turning research and retelling into live performance.</p>

          <div class="stage-videos">
            <a class="stage-video" href="https://youtu.be/z1WNK0jEE_c" target="_blank">
              <img src="../assets/images/voice/cover1.png" alt="From Script to Stage performance 1" class="stage-cover" />
              <div class="stage-play">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </a>
            <a class="stage-video" href="https://youtu.be/D1DRhBCXrTs" target="_blank">
              <img src="../assets/images/voice/cover2.png" alt="From Script to Stage performance 2" class="stage-cover" />
              <div class="stage-play">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </a>
          </div>

          <p class="stage-caption">Performed at Shenzhen Children’s Palace · Shenzhen, China</p>
        </div>
      </section>

      <!-- Teacher Resources Section -->
      <section class="resources-section">
        <div class="container">
          <h2 class="resources-title">Teacher Resources</h2>

          <div class="resources-grid">
            <a class="resource-item" :href="docUrl('1. VOICES OF OUR OWN_Reflection Sheet.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Reflection <br>Sheet</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('2. VOICES OF OUR OWN_Teacher Guide.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Teacher <br>Guide</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('3. VOICES OF OUR OWN_Story Background.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Story <br>Background</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('4. VOICES OF OUR OWN_Role Assignment Worksheet.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Role Assignment <br>Worksheet</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('6. VOICES OF OUR OWN_Performance Checklist.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Performance <br>Checklist</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('7. VOICES OF OUR OWN_Character Guide.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Character <br>Guide</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('8. VOICES OF OUR OWN_Discussion Questions.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Discussion <br>Questions</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('9. VOICES OF OUR OWN_Rehearsal Guide.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Rehearsal <br>Guide</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>

            <a class="resource-item" :href="docUrl('10. VOICES OF OUR OWN_Resource Pack.docx')" download>
              <div class="resource-inner">
                <div class="resource-label">Download <br>Resource Pack</div>
                <div class="resource-icon"><img src="../assets/images/home/icon-download2.png" alt="download" /></div>
              </div>
            </a>
          </div>
        </div>
      </section>
      <!-- Future Community Section -->
      <section class="community-section">
        <div class="container">
          <h2 class="community-title">Future Community Section</h2>
<!--          <div class="community-list">-->
<!--            <div class="community-box box-green">Student Performances</div>-->
<!--            <div class="community-box box-white">Student Reflections</div>-->
<!--            <div class="community-box box-brown">Teacher Feedback</div>-->
<!--            <div class="community-box box-gray">Participating Schools</div>-->
<!--            <div class="community-box box-green">Community/World Map</div>-->
<!--          </div>-->
          <div class="map">
            <div class="community-note">
              <p>Voices of Our Own is still growing. After the initial pilots in six schools, the next step is to bring the framework into classrooms in more countries and to see how it holds up across different cultural and educational settings. This section will become a place to share what students and teachers learn along the way.</p>
              <p>If you are an educator or student interested in piloting the framework, please get in touch through the <a href="#/contact">Contact page</a>. Feedback, adaptations, and reflections from participating schools will be added here as they come in.</p>
            </div>
            <img src="../assets/images/home/map.png" alt="world map" />
          </div>
        </div>
      </section>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

// Documents live in public/voice/ so they are copied verbatim into dist/
// and served relative to the deployed site root.
const docUrl = (name) => encodeURI(`voice/${name}`)
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.voice-banner {
  img {
    margin: 0 auto;
    width: 1366px;
    display: block;
    //max-height: 480px;
    object-fit: cover;
  }
}

.project-overview {
  background: #f8f7ef;
  padding: 60px 0 120px;
}
.project-overview .container {
  max-width: 1253px;
  margin: 0 auto;
  text-align: center;
}
.overview-title {
  font-family: $font-serif;
  font-size: 40px;
  margin-bottom: 48px;
  margin-top: 60px;
}
.overview-desc {
  width: 1160px;
  max-width: 100%;
  margin: 0 auto 40px;
  color: #0d0a07;
  font-family: $font-serif;
  font-size: 18px;
  line-height: 1.8;
  text-align: justify;
}
.cards-row {
  margin-top: 72px;
  display: flex;
  justify-content: center;
  gap: 40px;
  align-items: flex-start;
}
.card {
  text-align: center;
  .card-box {
    width: 360px;
    max-width: 100%;
    height: 440px;
    background: #adc3bb;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 auto;
    padding: 36px 32px 30px;
    box-sizing: border-box;

    p {
      color: #ffffff;
      font-family: $font-serif;
      font-size: 18px;
      line-height: 1.7;
      margin: auto 0;
      text-align: left;
    }
  }
  .card-box.large {
    width: 660px;
  }
  .card-title {
    font-family: $font-serif;
    font-size: 28px;
    font-weight: 700;
    color: #111;
    margin-top: 20px;
  }
}

/* Scripts section */
.scripts-section {
  background: #e2e1d9;
  padding: 60px 0 80px;
}
.scripts-section .container {
  max-width: 1253px;
  margin: 0 auto;
}
.scripts-section .container { text-align: center; }
.scripts-list {
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.script-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  padding: 36px 28px;
  background: transparent;
  text-decoration: none;
  color: inherit;
}
.script-label {
  width: 260px;
  text-align: left;
  font-family: $font-serif;
  font-size: 24px;
  font-weight: 700;
  color: #0d0905;
}
.script-name {
  flex: 1;
  text-align: center;
  font-family: $font-serif;
  font-size: 26px;
  letter-spacing: 0.08em;
  color: #0d0905;
}
.script-download img {
  width: 60px;
  height: 60px;
  cursor: pointer;
}

@media (max-width: 1024px) {
  .cards-row { flex-direction: column; align-items: center; }
  .card .card-box { width: 360px; max-width: 100%; height: 360px; }
  .card .card-box.large { width: 360px; height: 360px; }
}

/* From Script to Stage */
.stage-section {
  padding: 40px 0 80px;
  text-align: center;
}
.stage-section .container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 24px;
}
.stage-title {
  font-family: $font-serif;
  font-size: 34px;
  margin: 60px 0 10px;
  color: #0d0a07;
}
.stage-subtitle {
  font-family: $font-serif;
  font-size: 18px;
  color: #4A4A4A;
  margin: 0 0 40px;
}
.stage-videos {
  display: flex;
  justify-content: center;
  gap: 28px;
  flex-wrap: wrap;
}
.stage-video {
  position: relative;
  display: block;
  width: 420px;
  max-width: 100%;
  cursor: pointer;
  text-decoration: none;
}
.stage-cover {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 4px;
  //transition: transform 0.25s ease, box-shadow 0.25s ease;
}
.stage-video:hover .stage-cover {
  //transform: translateY(-4px);
  //box-shadow: 0 10px 26px rgba(0, 0, 0, 0.18);
}
.stage-play {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 64px;
  height: 64px;
  border-radius: 50%;
  //background: rgba(255, 255, 255, 0.88);
  display: flex;
  align-items: center;
  justify-content: center;
  //transition: transform 0.2s ease, background 0.2s ease;

  img {
    width: 43px;
    height: 43px;
  }
}
.stage-video:hover .stage-play {
  //transform: translate(-50%, -50%) scale(1.1);
  //background: #ffffff;
}
.stage-caption {
  font-family: $font-serif;
  font-size: 15px;
  color: #4A4A4A;
  margin-top: 22px;
}

/* Teacher Resources */
.resources-section {
  //background: #d1c4b4;
  padding: 60px 0 100px;
}
.resources-section .container {
  max-width: 1366px;
  background: #f8f7ef;
  margin: 0 auto;
  text-align: center;
}
.resources-title {
  font-family: $font-serif;
  font-size: 28px;
  margin-bottom: 30px;
}
.resources-grid {
  padding-top: 60px;
  display: grid;
  grid-template-columns: repeat(3, 265px);
  gap: 36px 40px;
  justify-content: center;
  align-items: center;
}
.resource-item {
  width: 240px;
  height: 240px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  color: inherit;
}
.resource-inner {
  width: 100%;
  height: 100%;
  background: #d1c4b4;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  box-sizing: border-box;
}
.resource-label {
  font-family: $font-serif;
  font-size: 24px;
  color: #fff;
  margin-bottom: 25px;
  text-align: center;
}
.resource-icon img {
  width: 62px;
  height: 73px;
  //opacity: 0.95;
}

@media (max-width: 900px) {
  .resources-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
  .resource-item { width: 45vw; height: 45vw; }
}

/* Future Community Section */
.community-section {
  background: transparent;
  padding: 60px 0 100px;
}
.community-section .container {
  max-width: 1253px;
  margin: 0 auto;
  text-align: center;
}
.community-title {
  font-family: $font-serif;
  font-size: 28px;
  margin-bottom: 30px;
}
.map{
  margin-top: 80px;

  img {
    width: 68%;
    height: auto;
    display: block;
    margin: 48px auto 0;
  }
}
.community-note {
  width: 1160px;
  max-width: 100%;
  margin: 0 auto;
  background: rgba(150, 150, 150, 0.35);
  padding: 32px 40px;
  box-sizing: border-box;
  text-align: left;

  p {
    color: #ffffff;
    font-family: $font-serif;
    font-size: 16px;
    line-height: 1.7;
    margin: 0 0 1em;

    &:last-child {
      margin-bottom: 0;
    }
  }

  a {
    color: #ffffff;
    text-decoration: underline;
    text-underline-offset: 3px;
  }
}
.community-list {
  display: flex;
  flex-direction: column;
  gap: 28px;
  align-items: center;
}
.community-box {
  width: 1002px;
  height: 221px;
  border-radius: 30px;
  display: flex;
  //align-items: center;
  padding-top: 30px;
  padding-left: 36px;
  font-family: $font-serif;
  font-size: 24px;
  font-weight: bolder;
  box-shadow: 0 8px 18px rgba(0,0,0,0.06);
  text-align: left;
}
.box-green {
  background: #adc3bb;
  color: #0e0a06;
}
.box-white {
  background: #ffffff;
  color: #111;
}
.box-brown {
  background: #d1c4b4;
  color: #111;
}
.box-gray {
  background: #e9e8e6;
  color: #111;
}

@media (max-width: 900px) {
  .community-box { width: 90%; height: 84px; border-radius: 14px; padding-left: 20px; }
  .community-note { padding: 24px; }
  .script-name { font-size: 20px; }
  .script-label { width: 140px; font-size: 18px; }
  .script-download img { width: 44px; height: 44px; }
}
</style>

