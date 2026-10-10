<template>
  <div class="pdf-preview-page">
    <Header />
    <main class="pdf-main">
      <div class="pdf-toolbar">
        <h2 class="pdf-title">{{ pdfTitle }}</h2>
        <a :href="pdfUrl" :download="pdfFileName" class="download-btn">Download PDF</a>
      </div>
      <div class="pdf-container">
        <iframe :src="pdfUrl" class="pdf-iframe" />
      </div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { computed } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

import manasKyrgyz from '../assets/pdf/Manas in Kyrgyz_compressed.pdf'
import manasChinese from '../assets/pdf/Manas in Chinese.pdf'
import muqamUyghur from '../assets/pdf/Muqam in Uyghur.pdf'
import muqamChinese from '../assets/pdf/Muqam in Chinese.pdf'
import jangarTod from '../assets/pdf/Jangar in Tod Script.pdf'
import jangarHudum from '../assets/pdf/Jangar in Hudum Script.pdf'
import jangarChinese from '../assets/pdf/Jargar in Chinese.pdf'

const pdfMap = {
  'manas-kyrgyz': { title: 'Manas Epic — Kyrgyz Language', file: manasKyrgyz, fileName: 'Manas_in_Kyrgyz.pdf' },
  'manas-chinese': { title: 'Manas Epic — Chinese Language', file: manasChinese, fileName: 'Manas_in_Chinese.pdf' },
  'muqam-uyghur': { title: 'The Twelve Muqam — Uyghur Language', file: muqamUyghur, fileName: 'Muqam_in_Uyghur.pdf' },
  'muqam-chinese': { title: 'The Twelve Muqam — Chinese Language', file: muqamChinese, fileName: 'Muqam_in_Chinese.pdf' },
  'jangar-tod': { title: 'Jangar Epic — Mongolian Tod', file: jangarTod, fileName: 'Jangar_in_Tod_Script.pdf' },
  'jangar-hudum': { title: 'Jangar Epic — Mongolian Hudum', file: jangarHudum, fileName: 'Jangar_in_Hudum_Script.pdf' },
  'jangar-chinese': { title: 'Jangar Epic — Chinese Language', file: jangarChinese, fileName: 'Jargar_in_Chinese.pdf' },
}

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
  padding: 0 40px 40px;
}

.pdf-iframe {
  width: 100%;
  height: 80vh;
  border: none;
  border-radius: 8px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.1);
}
</style>
