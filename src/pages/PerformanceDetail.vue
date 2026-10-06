<template>
  <div class="performance-detail-page">
    <Header />
    <main class="main-content">
      <!-- Section 1: Video Cover Area -->
      <section class="video-section">
        <div class="video-container" :style="{ backgroundImage: `url(${currentData.cover})` }">
          <a v-if="currentData.videoUrl" :href="currentData.videoUrl" target="_blank" class="play-button">
            <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
          </a>
          <div v-else class="play-button">
            <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
          </div>
        </div>
      </section>

      <!-- Section 2: Title -->
      <section class="title-section">
        <h1 class="main-title">{{ currentData.title }}</h1>
      </section>

      <!-- Performer Introduction (MANAS style) -->
      <section v-if="currentData.performerIntro" class="intro-section">
        <h2 class="section-heading">Performer Introduction</h2>
        <p v-for="(para, i) in currentData.performerIntro.split('\n\n')" :key="i" class="intro-text">{{ para }}</p>
      </section>

      <!-- What Are We Watching? (MUQAM style) -->
      <section v-if="currentData.watching" class="watching-section">
        <h2 class="section-heading">What Are We Watching?</h2>
        <p class="watching-text">{{ currentData.watching }}</p>
      </section>

      <!-- Story Parts - two columns (MUQAM style) -->
      <section v-if="currentData.storyParts && currentData.storyParts.length" class="story-section">
        <div class="story-columns">
          <div v-for="(part, idx) in currentData.storyParts" :key="idx" class="story-col">
            <h3 class="story-part-title">{{ part.title }}</h3>
            <h4 class="story-part-subtitle">{{ part.subtitle }}</h4>
            <p class="story-part-text">{{ part.text }}</p>
          </div>
        </div>
      </section>

      <!-- Music & Instruments with expand/collapse -->
      <section v-if="currentData.instruments && currentData.instruments.length" class="instruments-section">
        <h2 class="section-heading">Music &amp; Instruments</h2>
        <div class="instruments-list">
          <div v-for="(inst, idx) in currentData.instruments" :key="idx"
               :class="['inst-card', { expanded: expandedInst[idx] }, inst.color || (idx % 2 === 0 ? 'green' : 'tan')]"
               @click="toggleInst(idx)">
            <div class="inst-header">
              <div class="inst-img-wrap">
                <img v-if="inst.image" :src="inst.image" :alt="inst.name" class="inst-img" />
              </div>
              <div class="inst-info">
                <h3 class="inst-name">{{ inst.name }}</h3>
                <p class="inst-type">{{ inst.type }}</p>
                <p class="inst-label">Introduction</p>
                <p class="inst-label">History &amp; Origin</p>
                <p class="inst-label">Instrument Features</p>
              </div>
            </div>
            <div v-if="!expandedInst[idx]" class="inst-expand-btn" @click.stop="toggleInst(idx)">
              <img src="../assets/images/home/icon-arrow3.png" alt="expand" class="expand-icon" />
            </div>
            <Transition name="inst-expand">
              <div v-if="expandedInst[idx]" class="inst-detail" @click.stop>
                <div class="inst-detail-header">
                  <div class="inst-detail-img-wrap">
                    <img v-if="inst.image" :src="inst.image" :alt="inst.name" class="inst-img" />
                  </div>
                  <div class="inst-detail-meta">
                    <h3 class="inst-name">{{ inst.name }}</h3>
                    <p class="inst-type">{{ inst.type }}</p>
                  </div>
                </div>
                <h4 class="detail-label">Introduction</h4>
                <p class="detail-text">{{ inst.introduction }}</p>
                <h4 class="detail-label">History &amp; Origin</h4>
                <p class="detail-text">{{ inst.history }}</p>
                <h4 class="detail-label">Instrument Features</h4>
                <p class="detail-text">{{ inst.features }}</p>
                <div class="inst-collapse-btn" @click.stop="toggleInst(idx)">
                  <img src="../assets/images/home/icon-arrow3.png" alt="collapse" class="collapse-icon" />
                </div>
              </div>
            </Transition>
          </div>
        </div>
      </section>

      <!-- Oral / Cultural Context -->
      <section v-if="currentData.contextCards && currentData.contextCards.length" class="context-section">
        <h2 class="section-heading">Oral / Cultural Context</h2>
        <div class="context-cards">
          <a v-for="(card, idx) in currentData.contextCards" :key="idx" :href="card.url" target="_blank" class="context-card">
            <div class="card-icon">
              <img src="../assets/images/home/icon-download2.png" alt="icon" />
            </div>
            <p class="card-label">{{ card.label }}</p>
            <p class="card-sub">{{ card.sub }}</p>
          </a>
        </div>
      </section>

      <!-- Expert Perspective -->
      <section v-if="currentData.expert" class="expert-section">
        <h2 class="section-heading">Expert Perspective</h2>
        <div class="expert-top">
          <a v-if="currentData.expert.videoUrl" :href="currentData.expert.videoUrl" target="_blank" class="expert-video">
            <div class="play-button small">
              <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
            </div>
          </a>
          <div v-else class="expert-video">
            <div class="play-button small">
              <img src="../assets/images/home/icon-play.png" alt="play" class="play-icon" />
            </div>
          </div>
          <div class="expert-intro">
            <p>{{ currentData.expert.intro }}</p>
          </div>
        </div>
        <div class="expert-body">
          <p v-for="(para, i) in currentData.expert.paragraphs" :key="i">{{ para }}</p>
        </div>
      </section>

      <!-- Bottom: NEXT Button -->
      <section class="next-section">
        <img src="../assets/images/home/next-btn.png" alt="NEXT" class="next-btn-img" @click="goToNext" />
      </section>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { ref, reactive, computed, onMounted, onBeforeUnmount } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import manasCover from '../assets/images/home/manas-detail-cover.png'
import muqamCover from '../assets/images/home/muqam-cover.jpg'
import bg9 from '../assets/images/home/bg9.png'
import imgDap from '../assets/images/music/乐器-Dap.png'
import imgRawap from '../assets/images/music/乐器-Rawap.png'
import imgTash from '../assets/images/music/乐器-Tash.png'
import imgKomuz from '../assets/images/music/乐器-Komuz.png'
import imgMorinKhuur from '../assets/images/music/乐器-Morin Khuur.png'
import imgTobshuur from '../assets/images/music/乐器-Tubshuur.png'
import jangarCover from '../assets/images/home/jangar-cover.jpg'
import longsongCover from '../assets/images/home/longsong-cover.jpg'
import aitysCover from '../assets/images/home/aitys-cover.jpg'
import imgDombra from '../assets/images/music/乐器-Dombra.png'

const expandedInst = reactive({})

const toggleInst = (idx) => {
  expandedInst[idx] = !expandedInst[idx]
}

const performanceData = {
  manas: {
    title: 'M A N A S',
    cover: manasCover,
    videoUrl: 'https://youtu.be/wsSshEm5lDo',
    performerIntro: 'Toktosun is a new-generation Manas inheritor from Akqi County, Xinjiang. He began learning to perform the Epic of Manas at the age of eight and can perform it in both Kyrgyz and Mandarin. As a university-educated young inheritor, he is currently recognized as a county-level Manas inheritor in Akqi County, Kizilsu Prefecture, Xinjiang. He promotes the Epic of Manas through both traditional stage performances and new media platforms such as Douyin, WeChat Channels, and Kuaishou.',
    contextCards: [
      { label: 'Manas Epic', sub: 'Kyrgyz language', url: 'https://www.mediafire.com/file/n2rt2fwjzapy9e1/Manas_in_Kyrgyz.pdf/file' },
      { label: 'Manas Epic', sub: 'Chinese language', url: 'https://www.mediafire.com/file/6fb445xf0f0k16v/Manas_in_Chinese.pdf/file' },
    ],
  },
  muqam: {
    title: 'M U Q A M',
    cover: muqamCover,
    videoUrl: 'https://youtu.be/B8_drszW2jU',
    watching: 'Strings of the Satar developed from a selected passage of Muqam into an immersive contemporary Muqam music-and-dance production. It tells the legendary story of Amannisa Khan, the great poet and musician born in 1526. Amannisa Khan was the consort of Rashid Khan, the second ruler of the Yarkand Khanate, and is remembered for collecting and organizing the Twelve Muqam.',
    storyParts: [
      {
        title: 'Part I:',
        subtitle: 'A Legendary Encounter',
        text: 'Amannisa Khan was born into the family of a woodcutter. Gifted from a young age, she was already able to write poetry and perform Muqam by the age of thirteen. According to legend, Rashid Khan encountered her while traveling on a hunting trip and stayed at her family home in disguise. Seeing a tambur hanging on the wall, he asked the family to perform. Amannisa Khan spontaneously sang an excerpt from Panjgah Muqam, with lyrics that even mentioned Rashid Khan himself. Impressed by her talent, he then asked her to compose another poem on the spot. She did so immediately. Rashid Khan revealed his identity and asked to marry her.',
      },
      {
        title: 'Part II:',
        subtitle: 'Her Work in the Palace',
        text: 'After becoming a royal consort, Amannisa Khan devoted much of her energy to the preservation and organization of Muqam rather than to palace life. At the time, Uyghur Muqam had been transmitted for generations and contained a wide range of materials. With the support of Rashid Khan, she worked with the court musician Qadiri Khan and brought together folk musicians and singers to collect, organize, and develop Muqam traditions. She replaced some older and more difficult lyrics with poetry closer to everyday life and human emotion. This work ultimately contributed to the organization of the Twelve Muqam into a structured artistic tradition combining music, dance, and poetry.',
      },
    ],
    instruments: [
      {
        name: 'Dap',
        type: 'Uyghur · Percussion Instrument',
        image: imgDap,
        introduction: 'The Dap (also known as \'Nagara\') is one of the most important percussion instruments in Uyghur music. It is a frame drum with iron rings embedded inside the drum frame, producing a crisp and bright sound when struck. The Dap is an essential accompanying instrument for the Twelve Muqam, the grand classical music suite of the Uyghur people.',
        history: 'The Dap has a history of over 1,500 years in Xinjiang. Ancient murals from the Kizil Thousand Buddha Caves depict musicians playing frame drums similar to the Dap. During the Tang Dynasty, the Dap was widely used in court music and became an important instrument along the Silk Road. Over centuries, it has been refined and is now an indispensable part of Uyghur musical tradition.',
        features: 'The Dap typically has a diameter of 25-40 cm and is made from animal skin stretched over a wooden frame. Small iron or brass rings are attached inside the frame, creating a jingling sound when the drum is shaken or struck. The player holds the drum vertically and uses fingers and palm to produce various rhythms. It is known for its bright, penetrating tone that can cut through ensemble music.',
      },
      {
        name: 'Rawap',
        type: 'Uyghur · Plucked Instrument',
        image: imgRawap,
        introduction: 'The Rawap is a traditional plucked string instrument of the Uyghur people, featuring a distinctive long neck and resonator covered with animal skin. It has a wide range and bright, penetrating tone, making it an important accompanying instrument for the Twelve Muqam and a popular solo instrument.',
        history: 'The Rawap originated in ancient Persia and was introduced to Xinjiang via the Silk Road over 1,000 years ago. It evolved from the Persian \'Rubab\' and was adapted to Uyghur musical preferences. By the Ming and Qing dynasties, the Rawap had become a central instrument in Uyghur music, especially in the performance of Muqam suites.',
        features: 'The Rawap typically has 5 main strings and 8-10 sympathetic strings that resonate when played. The body is carved from a single piece of mulberry wood, with the resonator covered with snake skin or fish skin. The long neck allows for expressive slides and ornaments. Its tone is bright, metallic, and carries well in ensemble settings.',
      },
      {
        name: 'Tash',
        type: 'Uyghur · Percussion Instrument',
        color: 'grey',
        image: imgTash,
        introduction: 'The Tash is a unique traditional stone percussion instrument of the Uyghur people. It consists of two specially selected stones that are struck together to produce clear, resonant tones. The Tash is one of the oldest percussion instruments, reflecting the ancient origins of Uyghur musical culture.',
        history: 'The Tash is believed to be one of the earliest musical instruments, dating back to prehistoric times when early humans discovered that certain stones could produce musical tones when struck. In Uyghur culture, the Tash has been used for thousands of years in folk music and ceremonial contexts. The stones are carefully selected from riverbeds for their acoustic properties.',
        features: 'The Tash consists of two smooth, flat stones of different sizes, typically made from basalt or other dense volcanic rock. The stones are held in one hand and struck together rhythmically. Despite its simple construction, the Tash requires great skill to play expressively. Its clear, bell-like tone adds a unique percussive element to ensemble music.',
      },
      {
        name: 'Komuz',
        type: 'Kyrgyz · Plucked Instrument',
        color: 'green',
        image: imgKomuz,
        introduction: 'The Komuz is the most representative musical instrument of the Kyrgyz people. It is a three-stringed plucked instrument with a pear-shaped body and short neck. The Komuz is central to Kyrgyz cultural identity and is used to accompany epic singing, folk songs, and instrumental pieces.',
        history: 'The Komuz has a history of over 2,000 years among Turkic peoples. Ancient Chinese texts from the Han Dynasty mention similar instruments. The Komuz was particularly important during the Kyrgyz Khaganate period (6th-10th centuries). Legend says the instrument was created by a hunter who was inspired by the sounds of wind and water.',
        features: 'The Komuz is traditionally carved from a single piece of apricot or juniper wood. It has three strings made from horsehair or gut. The body is pear-shaped with a flat soundboard. The instrument is played by plucking the strings with the right hand while pressing the strings against the neck with the left. Its tone is clear, bright, and resonant.',
      },
    ],
    contextCards: [
      { label: 'The Twelve Muqam', sub: 'Uyghur language', url: 'https://www.mediafire.com/file/dt0oln046ec2v3a/Muqam_in_Uyghur.pdf/file' },
      { label: 'The Twelve Muqam', sub: 'Chinese language', url: 'https://www.mediafire.com/file/ombdgafyckjwriw/Muqam_in_Chinese.pdf/file' },
    ],
    expert: {
      videoUrl: 'https://youtu.be/sjfZW9LWsFs',
      intro: 'Professor Turghun has long taught courses on Chinese traditional and folk music, the music of Xinjiang\'s ethnic communities, Muqam musical structure, and Muqam appreciation. He has also conducted many years of field research on ethnic music across Xinjiang, visiting more than seventy counties. The interview therefore begins with his experience in both teaching and field research.',
      paragraphs: [
        'Professor Turghun emphasizes that Xinjiang Muqam is not a single musical form. He introduces several regional traditions, including the Twelve Muqam, Dolan Muqam, Turpan Muqam, and Hami Muqam, and compares their differences in length, structure, instrumentation, dance, and performance duration. The Twelve Muqam, for example, is extremely large in scale and contains multiple sections, while Dolan Muqam follows a different structure and performance format.',
        'He also discusses how traditional music should be understood and studied. Muqam contains a strong element of improvisation, meaning that even the same performer may sing or play differently from one day to the next. It therefore cannot be understood simply as a fixed musical score. Analytical tools from Western music, including notation, part-writing, and major/minor tonality, can be useful, but they should not be applied mechanically to the traditional music of Xinjiang. Drawing on his own long-term fieldwork, Professor Turghun repeatedly stresses that truly understanding a folk music tradition requires more than books or a single interview. Researchers need to go into the field, watch and listen, speak with different people, and then consider those observations alongside existing scholarship.',
      ],
    },
  },
  jangar: {
    title: 'J A N G A R',
    cover: jangarCover,
    videoUrl: 'https://youtu.be/O4LqQY__9Lw',
    performerIntro: 'Dorji Nyima is an autonomous-region-level inheritor of the Jangar epic from Hoboksar County, Tacheng, Xinjiang. His grandfather and other members of his family were also Jangar inheritors. Growing up surrounded by performances of the epic, he was deeply influenced by his elders and naturally became part of the next generation carrying the tradition forward.\n\nIn addition to performing Jangar in traditional stage settings, Dorji Nyima has worked with other artists to develop new arrangements of its music and presentation. These adaptations aim to make the epic more engaging for younger audiences while preserving its traditional foundation. Through both performance and creative collaboration, he has played an active role in promoting Jangar and bringing the tradition to contemporary audiences.',
    instruments: [
      {
        name: 'Morin Khuur',
        type: 'Mongolian · Bowed Instrument',
        color: 'green',
        image: imgMorinKhuur,
        introduction: 'The Morin Khuur (Horse-head Fiddle) is the most iconic instrument of the Mongolian people. It is a two-stringed bowed instrument with a trapezoidal body and a scroll carved in the shape of a horse\'s head. The Morin Khuur is considered the symbol of Mongolian music and culture.',
        history: 'The Morin Khuur dates back to the 12th century during the Mongol Empire. Legend tells of a shepherd who created the first Morin Khuur from the bones and hair of his beloved horse after it died. The instrument became a symbol of the deep bond between Mongolians and their horses. It was inscribed on UNESCO\'s Representative List of the Intangible Cultural Heritage of Humanity in 2009.',
        features: 'The Morin Khuur has a trapezoidal body with two strings made from horsehair. The bow is also strung with horsehair. The scroll is carved in the shape of a horse\'s head, giving the instrument its name. The instrument is played while seated, held between the legs. Its tone is deep, warm, and reminiscent of the Mongolian steppe. It can imitate the sounds of horses galloping and the wind on the grasslands.',
      },
      {
        name: 'Tobshuur',
        type: 'Mongolian · Plucked Instrument',
        color: 'tan',
        image: imgTobshuur,
        introduction: 'The Tobshuur is a traditional Mongolian plucked instrument with two strings. It has a round or oval body covered with animal skin and a short neck. The Tobshuur is commonly used for dance accompaniment and folk songs, producing a crisp, rhythmic sound.',
        history: 'The Tobshuur is one of the oldest Mongolian instruments, with origins dating back to the time of Genghis Khan. It was played by warriors and nomads alike, serving as both entertainment and a means of preserving oral history. The instrument has remained largely unchanged for centuries, maintaining its traditional form and playing style.',
        features: 'The Tobshuur has a small, round body carved from a single piece of wood, covered with camel skin or goat skin. It has two strings made from horsehair. The short neck has no frets, allowing for flexible pitch control. The instrument is played by strumming or plucking with the right hand. Its tone is bright, percussive, and well-suited for rhythmic accompaniment.',
      },
    ],
    contextCards: [
      { label: 'Jiang Geer Epic', sub: 'Mongolian Togd Togd', url: 'https://www.mediafire.com/file/ieg6i16rjtyk3f5/Jangar_in_Tod_Script.pdf/file' },
      { label: 'Jiang Geer Epic', sub: 'Mongolian Hudum', url: 'https://www.mediafire.com/file/5d3liz0rozy4w9s/Jangar_in_Hudum_Script.pdf/file' },
      { label: 'Jiang Geer Epic', sub: 'Chinese language', url: 'https://www.mediafire.com/file/18t86agpto7eun5/Jargar_in_Chinese.pdf/file' },
    ],
  },
  mongolian: {
    title: 'MONGOLIAN LONG SONG',
    cover: longsongCover,
    videoUrl: 'https://youtu.be/l8rV6WqlFiA',
    performerIntro: 'D. Utunason is a national-level inheritor of Mongolian Long Song, a form of intangible cultural heritage. As a member of an older generation, he learned Long Song through the traditional method of oral transmission from senior inheritors. He continues to use this approach in his own teaching today, guiding students through melodies and lyrics one line at a time and asking them to learn by listening and repeating.\n\nStudents who can read staff notation or numbered musical notation may use scores as an additional tool, but the ability to read music is not required. One notable part of his teaching method is that students who learn more quickly may help teach their classmates, while he continues to guide the process. This creates a transmission structure in which the teacher teaches students, and students then help teach one another.\n\nUtunason has been teaching continuously since around 2005 and has worked with dozens of students over the years. He also brings students to performances, cultural events, and competitions at both the Tacheng and Xinjiang regional levels.',
    instruments: [
      {
        name: 'Morin Khuur',
        type: 'Mongolian · Bowed Instrument',
        color: 'green',
        image: imgMorinKhuur,
        introduction: 'The Morin Khuur (Horse-head Fiddle) is the most iconic instrument of the Mongolian people. It is a two-stringed bowed instrument with a trapezoidal body and a scroll carved in the shape of a horse\'s head. The Morin Khuur is considered the symbol of Mongolian music and culture.',
        history: 'The Morin Khuur dates back to the 12th century during the Mongol Empire. Legend tells of a shepherd who created the first Morin Khuur from the bones and hair of his beloved horse after it died. The instrument became a symbol of the deep bond between Mongolians and their horses. It was inscribed on UNESCO\'s Representative List of the Intangible Cultural Heritage of Humanity in 2009.',
        features: 'The Morin Khuur has a trapezoidal body with two strings made from horsehair. The bow is also strung with horsehair. The scroll is carved in the shape of a horse\'s head, giving the instrument its name. The instrument is played while seated, held between the legs. Its tone is deep, warm, and reminiscent of the Mongolian steppe. It can imitate the sounds of horses galloping and the wind on the grasslands.',
      },
      {
        name: 'Tobshuur',
        type: 'Mongolian · Plucked Instrument',
        color: 'tan',
        image: imgTobshuur,
        introduction: 'The Tobshuur is a traditional Mongolian plucked instrument with two strings. It has a round or oval body covered with animal skin and a short neck. The Tobshuur is commonly used for dance accompaniment and folk songs, producing a crisp, rhythmic sound.',
        history: 'The Tobshuur is one of the oldest Mongolian instruments, with origins dating back to the time of Genghis Khan. It was played by warriors and nomads alike, serving as both entertainment and a means of preserving oral history. The instrument has remained largely unchanged for centuries, maintaining its traditional form and playing style.',
        features: 'The Tobshuur has a small, round body carved from a single piece of wood, covered with camel skin or goat skin. It has two strings made from horsehair. The short neck has no frets, allowing for flexible pitch control. The instrument is played by strumming or plucking with the right hand. Its tone is bright, percussive, and well-suited for rhythmic accompaniment.',
      },
    ],
    contextCards: [],
  },
  aitys: {
    title: 'A I T Y S',
    cover: aitysCover,
    videoUrl: 'https://youtu.be/tkZAkURHLag',
    performerIntro: 'Local inheritors usually perform and promote Aqyn Aitys with the organization and support of the county cultural center. Beyond performance itself, the team also explains what kind of art Aqyn Aitys is. To make it easier for audiences to understand, the inheritors sometimes compare it with familiar Chinese performance forms such as xiangsheng (comic dialogue) and errenzhuan (a traditional duet performance), while emphasizing that Aitys has its own distinctive structure.\n\nAn Aqyn performs while playing the dombra, listening carefully to an opponent, and immediately creating new poetic lines in response to what has just been said. The other performer then answers in the same way, creating a continuous exchange that is both collaborative and competitive. Through these improvised verses, audiences experience the performers\' poetic skill, quick thinking, wit, and humor.\n\nAqyn Aitys therefore combines music, poetry, debate, cultural knowledge, and real-time improvisation. Each Aqyn has a distinctive voice, melodic style, and way of expression. In male-female duets, the exchange may also include humor, romance, teasing, and other themes drawn closely from everyday life.',
    instruments: [
      {
        name: 'Dombra',
        type: 'Kazakh · Plucked Instrument',
        color: 'green',
        image: imgDombra,
        defaultExpanded: true,
        introduction: 'The Dombra is the most popular musical instrument among the Kazakh people. It is a two-stringed plucked lute with a long neck and pear-shaped body. The Dombra is the primary accompanying instrument for Aken Aytes (improvisational singing contests) and is essential to Kazakh folk music.',
        history: 'The Dombra has been played by Kazakhs for over 1,000 years. It is believed to have originated from ancient Turkic lutes. The instrument was central to the nomadic lifestyle, as it was portable and could accompany singing around campfires. Famous Kazakh poets and musicians like Abai Kunanbayev were known for their Dombra playing.',
        features: 'The Dombra has a pear-shaped body carved from a single piece of wood, typically pine or birch. It has two strings made from horsehair or gut, tuned a fourth or fifth apart. The long neck has frets tied with gut or string. The instrument is played by strumming or plucking. Its tone is warm, mellow, and well-suited for both accompaniment and solo performance.',
      },
    ],
    contextCards: [],
  },
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

const initExpanded = () => {
  Object.keys(expandedInst).forEach(k => delete expandedInst[k])
  const data = performanceData[currentId.value]
  if (data && data.instruments) {
    data.instruments.forEach((inst, idx) => {
      if (inst.defaultExpanded) expandedInst[idx] = true
    })
  }
}

const updateId = () => {
  currentId.value = getCurrentId()
  initExpanded()
}

onMounted(() => {
  window.addEventListener('hashchange', updateId)
  initExpanded()
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
}

/* Section 1: Video Cover */
.video-section {
  padding: 0;
  width: 100%;
}

.video-container {
  width: 100%;
  height: 800px;
  background-color: #000;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.play-button {
  width: 70px;
  height: 70px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
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

/* Section 2: Title */
.title-section {
  padding: 60px 20px 40px;
  text-align: center;
}

.main-title {
  font-family: $font-serif;
  font-size: 72px;
  font-weight: 900;
  color: #0e0a06;
  margin: 0;
  letter-spacing: 12px;
}

/* Shared section heading */
.section-heading {
  font-family: $font-serif;
  font-size: 32px;
  font-weight: 400;
  text-align: center;
  margin: 0 0 24px;
  color: #0e0a06;
}

/* Performer Introduction (MANAS) */
.intro-section {
  max-width: 900px;
  margin: 0 auto;
  padding: 60px 40px;
  text-align: center;
}

.intro-text {
  font-size: 16px;
  line-height: 1.8;
  color: #333;
  text-align: center;
  margin: 0;
}

/* What Are We Watching? (MUQAM) */
.watching-section {
  max-width: 860px;
  margin: 0 auto;
  padding: 60px 40px;
  text-align: center;
}

.watching-text {
  font-size: 16px;
  line-height: 1.8;
  color: #333;
  text-align: center;
  margin: 0;
}

/* Story Parts - two columns */
.story-section {
  max-width: 1100px;
  margin: 0 auto;
  padding: 40px 40px 60px;
}

.story-columns {
  display: flex;
  gap: 60px;
}

.story-col {
  flex: 1;
}

.story-part-title {
  font-family: $font-serif;
  font-size: 18px;
  font-weight: 400;
  color: #0e0a06;
  margin: 0 0 4px;
}

.story-part-subtitle {
  font-family: $font-serif;
  font-size: 22px;
  font-weight: 400;
  color: #0e0a06;
  margin: 0 0 20px;
}

.story-part-text {
  font-size: 14px;
  line-height: 1.7;
  color: #333;
  margin: 0;
}

/* Music & Instruments */
.instruments-section {
  max-width: 800px;
  margin: 0 auto;
  padding: 60px 40px;
}

.instruments-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.inst-card {
  border-radius: 16px;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.3s ease;

  &.green { background-color: #aec3bc; }
  &.tan { background-color: #d1c4b4; }
  &.grey { background-color: #e8e8e8; }

  &.expanded {
    cursor: default;
  }
}

.inst-header {
  display: flex;
  align-items: center;
  padding: 24px 40px;
  gap: 40px;
}

.inst-img-wrap {
  width: 240px;
  height: 150px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.inst-img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.inst-info {
  flex: 1;
  text-align: right;
}

.inst-name {
  font-family: $font-serif;
  font-size: 24px;
  font-weight: 700;
  color: #5a3e28;
  margin: 0 0 2px;
}

.inst-type {
  font-size: 13px;
  color: #555;
  font-style: italic;
  margin: 0 0 14px;
}

.inst-label {
  font-family: $font-serif;
  font-size: 15px;
  font-weight: 700;
  color: #0e0a06;
  margin: 4px 0;
}

/* Expanded detail */
.inst-detail {
  padding: 0 40px 30px;
}

.inst-detail-header {
  display: flex;
  align-items: center;
  gap: 40px;
  margin-bottom: 24px;
}

.inst-detail-img-wrap {
  width: 260px;
  height: 180px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.inst-detail-meta {
  text-align: right;
  flex: 1;
}

.detail-label {
  font-family: $font-serif;
  font-size: 18px;
  font-weight: 700;
  text-align: right;
  color: #0e0a06;
  margin: 24px 0 8px;
}

.detail-text {
  font-size: 14px;
  line-height: 1.7;
  color: #333;
  text-align: right;
  margin: 0;
}

.inst-expand-btn {
  display: flex;
  justify-content: center;
  padding: 8px 0 16px;
  cursor: pointer;
}

.expand-icon {
  width: 22px;
  height: 22px;
  opacity: 0.5;
  &:hover { opacity: 0.8; }
}

.inst-collapse-btn {
  display: flex;
  justify-content: center;
  margin-top: 24px;
  cursor: pointer;
}

.collapse-icon {
  width: 22px;
  height: 22px;
  transform: rotate(180deg);
  opacity: 0.5;
  &:hover { opacity: 0.8; }
}

.inst-card.expanded .inst-header {
  display: none;
}

/* Oral / Cultural Context */
.context-section {
  max-width: 900px;
  margin: 0 auto;
  padding: 60px 40px;
  text-align: center;
}

.context-cards {
  display: flex;
  justify-content: center;
  gap: 40px;
}

.context-card {
  width: 200px;
  height: 200px;
  background-color: #aec3bc;
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  text-decoration: none;
  cursor: pointer;
  transition: opacity 0.3s;
  &:hover { opacity: 0.85; }
}

.card-icon {
  width: 50px;
  height: 50px;
  margin-bottom: 16px;
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    filter: brightness(0) invert(1);
    opacity: 0.8;
  }
}

.card-label {
  font-family: $font-serif;
  font-size: 16px;
  font-weight: 700;
  color: #222;
  margin: 0 0 4px;
}

.card-sub {
  font-size: 14px;
  font-weight: 700;
  color: #222;
  margin: 0;
}

/* Expert Perspective */
.expert-section {
  max-width: 1100px;
  margin: 0 auto;
  padding: 60px 40px;
}

.expert-top {
  display: flex;
  gap: 30px;
  align-items: flex-start;
  margin-bottom: 30px;
}

.expert-video {
  width: 500px;
  height: 280px;
  background-color: #000;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
  border-radius: 4px;
}

.expert-intro {
  flex: 1;
  text-align: right;
  p {
    font-size: 14px;
    line-height: 1.7;
    color: #333;
    margin: 0;
  }
}

.expert-body {
  p {
    font-size: 14px;
    line-height: 1.7;
    color: #333;
    margin: 0 0 16px;
    text-align: right;
  }
}

/* Bottom: NEXT */
.next-section {
  padding: 60px 20px 100px;
  display: flex;
  justify-content: center;
}

.next-btn-img {
  cursor: pointer;
  width: 120px;
  height: auto;
  display: block;
}

/* Responsive */
@media (max-width: 900px) {
  .story-columns { flex-direction: column; gap: 30px; }
  .expert-top { flex-direction: column; }
  .expert-video { width: 100%; }
  .context-cards { flex-direction: column; align-items: center; }
  .inst-header { flex-direction: column; text-align: center; }
  .inst-info { text-align: center; }
  .detail-label, .detail-text { text-align: center; }
}
</style>

<!-- Unscoped styles for instrument expand animation -->
<style lang="scss">
.inst-expand-enter-active,
.inst-expand-leave-active {
  transition: all 0.4s ease;
  max-height: 1200px;
  overflow: hidden;
}
.inst-expand-enter-from,
.inst-expand-leave-to {
  max-height: 0;
  opacity: 0;
  overflow: hidden;
}
</style>
