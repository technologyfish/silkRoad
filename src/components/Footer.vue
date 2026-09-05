<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section about">
        <a href="#/"><img src="../assets/images/home/logo2.png" alt="Logo" class="footer-logo" /></a>
        <p>Exploring the intangible cultural heritage of the Silk Road</p>
      </div>

      <div class="footer-section links">
        <h2>Quick Links</h2>
        <ul>
          <li><a href="#/">HOME | 首页</a></li>
          <li><a href="#/performance">UNDERSTAND | 理解</a></li>
          <li><a href="#/listen">LISTEN | 倾听</a></li>
          <li><a href="#/voice">VOICE OF OUR OWN</a></li>
          <li><a href="#/contact">CONTACT | 联系</a></li>
        </ul>
      </div>

      <div class="footer-section contact">
        <h2>Contact</h2>
        <p>Address: Silk Road Intangible Cultural Heritage Organization, Xinjiang, Shenzhen</p>
        <p>Email: contact@silkroadich.com</p>
        <p>Tel: +852-46194670</p>
      </div>
    </div>

    <div class="footer-bottom">
      <p>© Edric's 2026 Silk Road Intangible Cultural Heritage Research. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
</script>
<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.footer {

  background-color: #854529;
  color: #ffffff;
  padding: 60px 5%;
  font-family: $font-serif;

  .footer-content {
    max-width: 1366px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    margin: 0 auto;
  }

  .footer-section {
    flex: 1;
    min-width: 250px;
    margin-right: 20px;

    &:last-child {
      margin-right: 0;
    }

    h2 {
      font-size: 1.4em;
      margin-bottom: 18px;
      color: #fff;
      font-weight: 600;
    }

    p,
    li a {
      font-size: 1em;
      line-height: 1.8;
      color: rgba(255,255,255,0.9);
      text-decoration: none;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    li {
      margin-bottom: 10px;
    }

    li a:hover {
      text-decoration: underline;
    }
  }

  .footer-logo {
    height: 60px;
    margin-bottom: 15px;
  }

  .footer-bottom {
    text-align: center;
    padding-top: 30px;
    border-top: 1px solid rgba(255,255,255,0.12);
    font-size: 0.9em;
    color: rgba(255,255,255,0.8);
  }
}
</style>