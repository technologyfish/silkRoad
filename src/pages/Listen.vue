<template>
  <div class="listen-page">
    <Header />
    <main class="listen-hero">
      <div class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_1" src="../assets/images/home/text_1.png" alt="text" />
        <div class="main-content-box">
          <h3 class="mc-title">Main content:</h3>
          <div class="mc-paragraphs">
            <p>● Different experiences of young and experienced inheritors;<br>
              How to study and comprehend "Manas";<br>
              Why do oral performances change;</p>

            <p>● Digital media communication;<br>
              What makes "Manas" a "living tradition".</p>
          </div>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar" />
            <div class="name-group">
              <div class="name">Tokom &amp; Suyundouke</div>
            </div>
          </div>
        </div>

        <div v-show="!expandedSections[0]" class="down-indicator" @click="toggleExpand(0)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      <!-- Expandable content for section 1 -->
      <div v-if="expandedSections[0]" class="expand-content">
        <div class="howto-video">
          <div class="video-placeholder">
            <div class="play-circle">
              <img src="../assets/images/home/icon-play.png" alt="play" />
            </div>
          </div>
        </div>
        <h3 class="expand-title">Description</h3>
        <p class="expand-desc">Copywriting, copywriting copywriting, copywriting<br>Copywriting, copywriting copywriting, copywriting</p>
        <h3 class="expand-title">Edric Commentary</h3>
        <ul class="expand-list">
          <li>Why I chose this clip</li>
          <li>What I noticed</li>
          <li>What changed my understanding</li>
          <li>What question it raised</li>
        </ul>
        <div class="collapse-indicator" @click="toggleExpand(0)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
    </main>
    <!-- Second section: same layout, alt background and content -->
    <main class="listen-hero alt">
      <div class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_2" src="../assets/images/home/text_2.png" alt="text2" />
        <div class="main-content-box">
          <h3 class="mc-title">Performance / Audience Perspective</h3>
          <div class="mc-paragraphs">
            <p>● Personal stories behind musicians and their instruments; <br>
              How to introduce young audiences to unfamiliar traditions.<br>
              Academic / Research Perspective</p>

            <p>● Preservation vs. Development;<br>
              How to understand different music systems:<br>
              ● Ethnic music and field research methods</p>
          </div>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-2" />
            <div class="name-group">
              <div class="name">买迪娜 &amp; 吐尔洪教授</div>
            </div>
          </div>
        </div>

        <div v-show="!expandedSections[1]" class="down-indicator" @click="toggleExpand(1)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      <div v-if="expandedSections[1]" class="expand-content">
        <div class="howto-video">
          <div class="video-placeholder">
            <div class="play-circle">
              <img src="../assets/images/home/icon-play.png" alt="play" />
            </div>
          </div>
        </div>
        <h3 class="expand-title">Description</h3>
        <p class="expand-desc">Copywriting, copywriting copywriting, copywriting<br>Copywriting, copywriting copywriting, copywriting</p>
        <h3 class="expand-title">Edric Commentary</h3>
        <ul class="expand-list">
          <li>Why I chose this clip</li>
          <li>What I noticed</li>
          <li>What changed my understanding</li>
          <li>What question it raised</li>
        </ul>
        <div class="collapse-indicator" @click="toggleExpand(1)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
    </main>
    <!-- Third section: same layout as second, white background, different content -->
    <main class="listen-hero">
      <div class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_3" src="../assets/images/home/text_3.png" alt="text3" />
        <div class="main-content-box">
          <h3 class="mc-title">Main content:</h3>
          <div class="mc-paragraphs">
            <p>● Tradition and Adaptation ;<br>
              ● What can be changed;<br>
              ● What needs to be retained;<br>
              ● Traditional Performance vs. Adapted Performance.</p>
          </div>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar" />
            <div class="name-group">
              <div class="name">尼玛</div>
            </div>
          </div>
        </div>

        <div v-show="!expandedSections[2]" class="down-indicator" @click="toggleExpand(2)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      <div v-if="expandedSections[2]" class="expand-content">
        <div class="howto-video">
          <div class="video-placeholder">
            <div class="play-circle">
              <img src="../assets/images/home/icon-play.png" alt="play" />
            </div>
          </div>
        </div>
        <h3 class="expand-title">Description</h3>
        <p class="expand-desc">Copywriting, copywriting copywriting, copywriting<br>Copywriting, copywriting copywriting, copywriting</p>
        <h3 class="expand-title">Edric Commentary</h3>
        <ul class="expand-list">
          <li>Why I chose this clip</li>
          <li>What I noticed</li>
          <li>What changed my understanding</li>
          <li>What question it raised</li>
        </ul>
        <div class="collapse-indicator" @click="toggleExpand(2)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
    </main>
    <!-- Fourth section: alt background, different left image and person -->
    <main class="listen-hero alt">
      <div class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_4" src="../assets/images/home/text_4.png" alt="text4" />
        <div class="main-content-box">
          <h3 class="mc-title">Main content:</h3>
          <div class="mc-paragraphs">
            <p>● Oral teaching;<br>
              ● Learn sentence by sentence;<br>
              ● Transmission among students;<br>
              ● Performance Practice ;<br>
              ● Voice, body, clothing, and emotion.</p>
          </div>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-2" />
            <div class="name-group">
              <div class="name">乌图那生</div>
            </div>
          </div>
        </div>

        <div v-show="!expandedSections[3]" class="down-indicator" @click="toggleExpand(3)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      <div v-if="expandedSections[3]" class="expand-content">
        <div class="howto-video">
          <div class="video-placeholder">
            <div class="play-circle">
              <img src="../assets/images/home/icon-play.png" alt="play" />
            </div>
          </div>
        </div>
        <h3 class="expand-title">Description</h3>
        <p class="expand-desc">Copywriting, copywriting copywriting, copywriting<br>Copywriting, copywriting copywriting, copywriting</p>
        <h3 class="expand-title">Edric Commentary</h3>
        <ul class="expand-list">
          <li>Why I chose this clip</li>
          <li>What I noticed</li>
          <li>What changed my understanding</li>
          <li>What question it raised</li>
        </ul>
        <div class="collapse-indicator" @click="toggleExpand(3)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
    </main>
    <!-- Fifth section: same layout as fourth, alt background -->
    <main class="listen-hero">
      <div class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_5" src="../assets/images/home/text_5.png" alt="text5" />
        <div class="main-content-box">
          <h3 class="mc-title">Main content:</h3>
          <div class="mc-paragraphs">
            <p>● Improvisation ;<br>
              ● Dombra ;<br>
              ● Real-time Response ;<br>
              ● Humor / Competition ;<br>
              ● Audience Interaction.</p>
          </div>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-3" />
            <div class="name-group">
              <div class="name">MORE</div>
            </div>
          </div>
        </div>

        <div v-show="!expandedSections[4]" class="down-indicator" @click="toggleExpand(4)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      <div v-if="expandedSections[4]" class="expand-content">
        <div class="howto-video">
          <div class="video-placeholder">
            <div class="play-circle">
              <img src="../assets/images/home/icon-play.png" alt="play" />
            </div>
          </div>
        </div>
        <h3 class="expand-title">Description</h3>
        <p class="expand-desc">Copywriting, copywriting copywriting, copywriting<br>Copywriting, copywriting copywriting, copywriting</p>
        <h3 class="expand-title">Edric Commentary</h3>
        <ul class="expand-list">
          <li>Why I chose this clip</li>
          <li>What I noticed</li>
          <li>What changed my understanding</li>
          <li>What question it raised</li>
        </ul>
        <div class="collapse-indicator" @click="toggleExpand(4)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

const expandedSections = reactive([false, false, false, false, false])

const toggleExpand = (index) => {
  expandedSections[index] = !expandedSections[index]
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.listen-hero {
  background-color: #fff;
  position: relative;
  padding-bottom: 40px;
}

.text-left {
  position: absolute;
  left: 0;
  top: 20px;

  height: auto;
}

.text_1{
  width: 129px;
}
.text_2{
  width: 128px;
}
.text_3{
  width: 124px;
}
.text_4{
  width: 71px;
}
.text_5{
  width: 126px;
}
.listen-hero.alt {
  background-image: url('../assets/images/home/bg4.png');
  background-repeat: no-repeat;
  background-position: center top;
  background-size: cover;
  padding-bottom: 40px;
}

.avatar.avatar-2 {
  background-image: url('../assets/images/home/person_2.png');
  background-size: cover;
  background-position: center;
}

.avatar.avatar-3 {
  background-image: url('../assets/images/home/person_3.png');
  background-size: cover;
  background-position: center;
}

.listen-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 751px;
  position: relative;
}

.main-content-box {
  width: 640px;
  margin-left: 220px;
}
.mc-title {
  font-family: $font-sans;
  font-size: 20px;
  margin-bottom: 24px;
}
.mc-paragraphs p {
  font-size: 20px;
  line-height: 1.6;
  color: #111;
  margin-bottom: 24px;
}

.people-column {
  width: 280px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  margin-right: 80px;
}

.person-row {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.avatar {
  width: 375px;
  height: 420px;
  background-color: #aec3bc;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  margin: 0 auto 16px;
}

.name-group {
  text-align: center;
}

.name {
  font-family: $font-serif;
  font-size: 18px;
}

.down-indicator {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 24px;
  cursor: pointer;
}
.down-indicator img {
  width: 48px;
  height: 48px;
  opacity: 0.9;
  transition: transform 0.3s ease;
}
.down-indicator img.arrow-up {
  transform: rotate(180deg);
}

/* Expand content area */
.expand-content {
  padding: 60px 0;
  text-align: center;
  //max-width: 800px;
  margin: 0 auto;
}

.expand-title {
  font-family: $font-serif;
  font-size: 28px;
  font-weight: 400;
  color: #0e0a06;
  margin: 0 0 20px;
}

.expand-desc {
  font-size: 16px;
  color: #444;
  font-style: italic;
  line-height: 1.8;
  margin-bottom: 40px;
}

.expand-list {
  list-style: disc;
  display: inline-block;
  text-align: center;
  padding: 0;
  margin: 0 0 40px;

  li {
    font-size: 16px;
    color: #222;
    margin-bottom: 8px;
    list-style: disc inside;
  }
}

.collapse-indicator {
  cursor: pointer;
  display: flex;
  justify-content: center;
  margin-top: 20px;

  img {
    width: 48px;
    height: 48px;
    opacity: 0.9;
    transition: transform 0.3s ease;
  }
  img.arrow-up {
    transform: rotate(180deg);
  }
}
.howto-video {
  display: flex;
  justify-content: center;
  margin-bottom: 36px;
}
.video-placeholder {
  width: 1055px;
  height: 480px;
  background: #aec3bc;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
  position: relative;
}
.play-circle {
  width: 86px;
  height: 86px;
  border-radius: 50%;
}
.play-circle img {
  width: 100%;
  height:  100%;
}
@media (max-width: 1200px) {
  .listen-inner { width: 100%; padding: 0 20px; box-sizing: border-box; }
  .text-left { display: none; }
  .main-content-box { width: 60%; margin-left: 20px; }
  .people-column { display: none; }
}
</style>

