<template>
   <section class="page-home">
    <div class="page-home-content">
      <div class="page-home-jumbotron">
        <div class="page-home-logo" :class="{ 'logo-animate': logoAnimateReady }">
          <img src="../assets/logo.jpg" alt="">
          <p class="page-home-title">fx-mobile</p>
          <p></p>
        </div>
        <p class="page-home-desc" :class="{ 'logo-animate': descAnimateReady }">基于 Vue.js 的移动端组件库</p>
        <div class="page-home-buttons">
          <a href="//fx-mobile.github.io/fx-doc" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>开始使用</span></a>
          <a href="//fx-mobile.github.io/fx-mui" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>组件示例</span></a>
          <a href="//www.github.com/fx-mobile/fx-ued" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>UED规范</span></a>
          <a href="//www.github.com/fx-mobile/fx-fed" class="page-home-button" v-show="descAnimateReady" transition="enter" target="_blank"><span>FED规范</span></a>
        </div>
        <div class="page-home-gitbtn">
          <iframe src="https://ghbtns.com/github-btn.html?user=fx-mobile&repo=fx-mui&type=star&count=true" frameborder="0" scrolling="0" width="110px" height="20px" v-show="descAnimateReady" transition="enter"></iframe>
          <iframe src="https://ghbtns.com/github-btn.html?user=fx-mobile&repo=fx-mui&type=fork&count=true" frameborder="0" scrolling="0" width="95px" height="20px" v-show="descAnimateReady" transition="enter"></iframe>
        </div>

        <div class="page-home-lang">
          <lang-button v-show="descAnimateReady" transition="enter"></lang-button>
        </div>
      </div>

      <p class="page-home-sector">快速开始</p>
      <div class="page-home-start" :style="{ 'width': smallScreen ? '90%' : '650px' }">
        <code>
          <span class="page-home-comment">// 安装</span>
          <span class="page-home-comment"># Vue 2.0</span>
          <span>
            <span class="pl-smi">npm install fx-mui -S</span>
          </span>
        </code>
      </div>
      <div class="page-home-start" :style="{ 'width': smallScreen ? '90%' : '650px' }">
        <code>
          <span class="page-home-comment">// 引入全部组件</span>
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
          <span class="page-home-comment">// 按需引入部分组件</span>
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

      <p class="page-home-sector page-home-sector--dark">特性介绍</p>
      <div class="page-home-show">
        <div class="page-home-left">
          <ul class="page-home-feature" :style="{ 'width': smallScreen ? '100%' : '650px' }">
            <li>
              <i class="iconfont icon-zujian"></i>
              <span>FX MUI 包含丰富的 CSS 和 JS 组件，能够满足日常的移动端开发需要。通过它，可以快速构建出风格统一的页面，提升开发效率。</span>
            </li>
            <li>
              <i class="iconfont icon-anxufufei"></i>
              <span>真正意义上的按需加载组件。可以只加载声明过的组件及其样式文件，无需再纠结文件体积过大。</span>
            </li>
            <li>
              <i class="iconfont icon-xingnengtongji"></i>
              <span>考虑到移动端的性能门槛，FX MUI 采用 CSS3 处理各种动效，避免浏览器进行不必要的重绘和重排，从而使用户获得流畅顺滑的体验。</span>
            </li>
            <li>
              <i class="iconfont icon-shiliangzhinengduixiang9"></i>
              <span>依托 Vue.js 高效的组件化方案，FX MUI 做到了轻量化。即使全部引入，压缩后的文件体积也仅有 ~30kb (JS + CSS) gzip。</span>
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
      // if (!localStorage.getItem('noticed')) {
      //   localStorage.setItem('noticed', true);
      //   setTimeout(() => {
      //     MessageBox.alert('FX MUI 现已支持 Vue 2.0', 'fx-mui 已发布！');
      //   }, 1000);
      // }
    },

    beforeDestroy() {
      window.removeEventListener('resize', () => {
        this.handleResize();
      });
    }
  };
</script>
