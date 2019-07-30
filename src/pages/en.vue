<template>
   <section class="page-home">
    <div class="page-home-content">
      <div class="page-home-jumbotron">
        <div class="page-home-logo" :class="{ 'logo-animate': logoAnimateReady }">
          <img src="../assets/logo.jpg" alt="">
          <p class="page-home-title">Mint UI</p>
          <p></p>
        </div>
        <p class="page-home-desc" :class="{ 'logo-animate': descAnimateReady }">Mobile UI elements for Vue.js</p>
        <div class="page-home-buttons">
          <a href="/fx-doc" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>Documentation</span></a>
          <a href="//fx-mobile.github.io/fx-mui" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>Demo</span></a>
        </div>
        <div class="page-home-gitbtn">
          <iframe src="https://ghbtns.com/github-btn.html?user=ElemeFE&repo=fx-mui&type=star&count=true" frameborder="0" scrolling="0" width="110px" height="20px" v-show="descAnimateReady" transition="enter"></iframe>
          <iframe src="https://ghbtns.com/github-btn.html?user=ElemeFE&repo=fx-mui&type=fork&count=true" frameborder="0" scrolling="0" width="95px" height="20px" v-show="descAnimateReady" transition="enter"></iframe>
        </div>

        <div class="page-home-lang">
          <lang-button v-show="descAnimateReady" transition="enter"></lang-button>
        </div>
      </div>

      <p class="page-home-sector">Quick Start</p>
      <div class="page-home-start" :style="{ 'width': smallScreen ? '90%' : '650px' }">
        <code>
          <span class="page-home-comment">// install</span>
          <span class="page-home-comment"># for Vue 2.0</span>
          <span>
            <span class="pl-smi">npm install fx-mui -S</span>
          </span>
        </code>
      </div>
      <div class="page-home-start" :style="{ 'width': smallScreen ? '90%' : '650px' }">
        <code>
          <span class="page-home-comment">// import all components</span>
          <span>
            <span class="pl-k">import </span><span class="pl-smi">Vue </span><span class="pl-k">from </span><span class="pl-s">'vue'</span><span class="pl-smi">;</span>
          </span>
          <span>
            <span class="pl-k">import </span><span class="pl-smi">Mint </span><span class="pl-k">from </span><span class="pl-s">'fx-mui'</span><span class="pl-smi">;</span>
          </span>
          <span>
            <span class="pl-smi">Vue.</span><span class="pl-en">use</span><span class="pl-smi">(Mint);</span>
          </span>
        </code>
        <code>
          <span class="page-home-comment">// import only on demand</span>
          <span>
            <span class="pl-k">import </span><span class="pl-smi">{ Cell, Checklist } </span><span class="pl-k">from </span><span class="pl-s">'fx-mui'</span><span class="pl-smi">;</span>
            </span>
          <span>
            <span class="pl-smi">Vue.</span><span class="pl-en">component</span><span class="pl-smi">(Cell.name, Cell);</span>
          </span>
          <span>
            <span class="pl-smi">Vue.</span><span class="pl-en">component</span><span class="pl-smi">(Checklist.name, Checklist);</span>
        </code>
      </div>

      <p class="page-home-sector page-home-sector--dark">Features</p>
      <div class="page-home-show">
        <div class="page-home-left">
          <ul class="page-home-feature" :style="{ 'width': smallScreen ? '100%' : '650px' }">
            <li>
              <i class="iconfont icon-zujian"></i>
              <span>Mint UI provides abundant CSS and JS components for building mobile applications. With it, you can create web pages in cohesive style ever faster.</span>
            </li>
            <li>
              <i class="iconfont icon-anxufufei"></i>
              <span>Load on demand. Importing components and their style sheets only when needed truly liberates you from excessive file sizes.</span>
            </li>
            <li>
              <i class="iconfont icon-xingnengtongji"></i>
              <span>To avoid unnecessary repaint and reflows, Mint UI handles animations using CSS3, so that users can enjoy smooth motions even on mobile devices.</span>
            </li>
            <li>
              <i class="iconfont icon-shiliangzhinengduixiang9"></i>
              <span>Thanks to the efficient component-based approach of Vue.js, Mint UI is pretty light-weight. When all imported, the compressed code takes only ~30kb (JS + CSS) gzip space.</span>
            </li>
          </ul>       
        </div>

        <div class="page-home-phone" v-if="!smallScreen">
          <iframe src="//fx-mobile.github.io/fx-mui" frameborder="0"></iframe>
        </div>
      </div>

      <footer class="page-home-footer">
        <a href="https://github.com/thethreekingdoms">© https://github.com/thethreekingdoms</a>
      </footer>
    </div>
  </section>
</template>

<script type="text/babel">
  import '../font/iconfont.css';
  import { MessageBox } from 'fx-mui';
  import 'fx-mui/lib/message-box/style.css';

  export default {
    data() {
      return {
        smallScreen: true,
        isMobile: false,
        logoAnimateReady: false,
        descAnimateReady: false
      };
    },

    methods: {
      handleResize() {
        this.smallScreen = document.body.clientWidth <= 650;
      }
    },

    compiled() {
      this.logoAnimateReady = true;
      setTimeout(() => {
        this.descAnimateReady = true;
      }, 500);
      this.handleResize();
      window.addEventListener('resize', () => {
        this.handleResize();
      });
      this.isMobile = document.body.clientWidth <= 500;
    },

    ready() {
      if (!localStorage.getItem('noticed')) {
        localStorage.setItem('noticed', true);
        setTimeout(() => {
          MessageBox.alert('Mint UI now supports Vue 2.0', 'FX-MUI published!');
        }, 1000);
      }
    },

    beforeDestroy() {
      window.removeEventListener('resize', () => {
        this.handleResize();
      });
    }
  };
</script>
