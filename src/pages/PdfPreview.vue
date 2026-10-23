<template>
  <div class="pdf-preview-page">
    <Header />
    <main class="pdf-main">
      <div class="pdf-toolbar">
        <h2 class="pdf-title">{{ pdfTitle }}</h2>
        <a :href="pdfUrl" target="_blank" rel="noopener" class="download-btn">Download PDF</a>
      </div>
      <div class="pdf-container">
        <div class="pdf-open-panel">
          <div class="pdf-open-icon">
            <img src="../assets/images/home/icon-download2.png" alt="PDF" />
          </div>
          <p class="pdf-open-name">{{ pdfFileName }}</p>
          <p class="pdf-open-hint">This document is hosted on our own server.<br />Click below to open it in a new tab.</p>
          <a :href="pdfUrl" target="_blank" rel="noopener" class="open-btn">View PDF</a>
        </div>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { computed } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

// PDFs are hosted on our own server (Aliyun, managed via BT panel),
// NOT bundled into the site (GitHub Pages).
// Note: absolute http URL + open in a new tab, because GitHub Pages is https
// and embedding an http iframe would be blocked as mixed content.
const PDF_BASE = 'http://8.148.30.7/pdfs/'

const pdfMap = {
  'manas-kyrgyz': { title: 'Manas Epic — Kyrgyz Language', file: PDF_BASE + 'manas-kyrgyz.pdf', fileName: 'Manas_in_Kyrgyz.pdf' },
  'manas-chinese': { title: 'Manas Epic — Chinese Language', file: PDF_BASE + 'manas-chinese.pdf', fileName: 'Manas_in_Chinese.pdf' },
  'muqam-uyghur': { title: 'The Twelve Muqam — Uyghur Language', file: PDF_BASE + 'muqam-uyghur.pdf', fileName: 'Muqam_in_Uyghur.pdf' },
  'muqam-chinese': { title: 'The Twelve Muqam — Chinese Language', file: PDF_BASE + 'muqam-chinese.pdf', fileName: 'Muqam_in_Chinese.pdf' },
  'jangar-tod': { title: 'Jangar Epic — Mongolian Tod', file: PDF_BASE + 'jangar-tod.pdf', fileName: 'Jangar_in_Tod_Script.pdf' },
  'jangar-hudum': { title: 'Jangar Epic — Mongolian Hudum', file: PDF_BASE + 'jangar-hudum.pdf', fileName: 'Jangar_in_Hudum_Script.pdf' },
  'jangar-chinese': { title: 'Jangar Epic — Chinese Language', file: PDF_BASE + 'jangar-chinese.pdf', fileName: 'Jargar_in_Chinese.pdf' },
  'jangar-english': { title: 'Jangar Epic — English Language', file: PDF_BASE + 'jangar-english.pdf', fileName: 'Jangar_Epic_English.pdf' },
}

// Register the 11 English volumes: #/pdf-preview/manas-english-1-1 ... 4-2
const manasEnglishVols = [
  '1-1', '1-2', '1-3', '1-4',
  '2-1', '2-2', '2-3',
  '3-1', '3-2',
  '4-1', '4-2',
]
manasEnglishVols.forEach((vol) => {
  pdfMap[`manas-english-${vol}`] = {
    title: `Manas Epic — English Language ${vol}`,
    file: `${PDF_BASE}manas-english-${vol}.pdf`,
    fileName: `Manas_Epic_English_${vol}.pdf`,
  }
})

const pdfKey = computed(() => {
  const hash = window.location.hash || ''
  const parts = hash.replace('#/pdf-preview/', '')
  return parts
})

const currentPdf = computed(() => pdfMap[pdfKey.value] || {})
const pdfTitle = computed(() => currentPdf.value.title || 'PDF Preview')
const pdfUrl = computed(() => currentPdf.value.file || '')
const pdfFileName = computed(() => currentPdf.value.fileName || 'document.pdf')
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.pdf-preview-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.pdf-main {
  flex: 1;
  display: flex;
  flex-direction: column;
  background-color: #f5f5f5;
}

.pdf-toolbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1100px;
  width: 100%;
  margin: 0 auto;
  padding: 24px 40px 16px;
}

.pdf-title {
  font-family: $font-serif;
  font-size: 22px;
  font-weight: 700;
  color: #333;
  margin: 0;
}

.download-btn {
  display: inline-block;
  padding: 10px 28px;
  background-color: #854529;
  color: #fff;
  font-size: 14px;
  font-weight: 600;
  text-decoration: none;
  border-radius: 6px;
  transition: opacity 0.3s;
  &:hover {
    opacity: 0.85;
  }
}

.pdf-container {
  flex: 1;
  max-width: 1100px;
  width: 100%;
  margin: 0 auto;
  padding: 0 40px 60px;
}

.pdf-open-panel {
  max-width: 460px;
  margin: 0 auto;
  background-color: #aec3bc;
  border-radius: 16px;
  padding: 60px 40px;
  text-align: center;
}

.pdf-open-icon {
  width: 72px;
  height: 72px;
  margin: 0 auto 24px;
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    filter: brightness(0) invert(1);
    opacity: 0.85;
  }
}

.pdf-open-name {
  font-family: $font-serif;
  font-size: 18px;
  font-weight: 700;
  color: #222;
  margin: 0 0 12px;
  word-break: break-all;
}

.pdf-open-hint {
  font-size: 14px;
  line-height: 1.7;
  color: #333;
  margin: 0 0 28px;
}

.open-btn {
  display: inline-block;
  padding: 12px 48px;
  background-color: #854529;
  color: #fff;
  font-size: 15px;
  font-weight: 600;
  text-decoration: none;
  border-radius: 6px;
  transition: opacity 0.3s;
  &:hover {
    opacity: 0.85;
  }
}
</style>
