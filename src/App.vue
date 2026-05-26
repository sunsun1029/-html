<script setup>
import { onMounted, onUnmounted, ref } from "vue";
import heroImage from "../assets/hero-workspace.svg";

const isMenuOpen = ref(false);
const isScrolled = ref(false);

const navItems = [
  { href: "#about", label: "关于" },
  { href: "#work", label: "作品" },
  { href: "#experience", label: "经历" },
  { href: "#contact", label: "联系" },
];

const works = [
  {
    theme: "teal",
    meta: "Product Design · 2026",
    title: "个人知识库仪表盘",
    description:
      "为高频记录者设计的知识管理界面，强调快速捕捉、语义检索和复盘节奏。",
  },
  {
    theme: "coral",
    meta: "Web Experience · 2025",
    title: "独立品牌官网",
    description:
      "从品牌叙事、信息架构到响应式页面实现，建立更清晰的线上第一印象。",
  },
  {
    theme: "ink",
    meta: "Prototype · 2025",
    title: "AI 写作流程工具",
    description:
      "围绕灵感整理、提纲生成和版本对比，探索更自然的创作辅助方式。",
  },
];

const skills = ["产品设计", "前端开发", "品牌表达", "原型验证", "内容策略"];

function updateHeader() {
  isScrolled.value = window.scrollY > 24;
}

function closeMenu() {
  isMenuOpen.value = false;
}

onMounted(() => {
  updateHeader();
  window.addEventListener("scroll", updateHeader, { passive: true });
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateHeader);
});
</script>

<template>
  <header
    class="site-header"
    :class="{ scrolled: isScrolled, 'menu-open': isMenuOpen }"
  >
    <a class="brand" href="#top" aria-label="返回首页" @click="closeMenu">
      <span class="brand-mark">孙</span>
      <span>孙婉晴</span>
    </a>
    <button
      class="nav-toggle"
      type="button"
      aria-label="打开菜单"
      :aria-expanded="String(isMenuOpen)"
      @click="isMenuOpen = !isMenuOpen"
    >
      <span></span>
      <span></span>
      <span></span>
    </button>
    <nav class="site-nav" aria-label="主导航">
      <a
        v-for="item in navItems"
        :key="item.href"
        :href="item.href"
        @click="closeMenu"
      >
        {{ item.label }}
      </a>
    </nav>
  </header>

  <main id="top">
    <section class="hero" aria-labelledby="hero-title">
      <img
        class="hero-image"
        :src="heroImage"
        alt="明亮现代的个人工作空间"
      />
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <p class="eyebrow">Designer · Developer · Maker</p>
        <h1 id="hero-title">你好，我是孙婉晴。</h1>
        <p class="hero-copy">
          我专注于把清晰的想法做成好用、好看、可持续的数字产品。这里收集了我的项目、经历和最近正在思考的方向。
        </p>
        <div class="hero-actions">
          <a class="button primary" href="#work">查看作品</a>
          <a class="button secondary" href="mailto:hello@example.com">
            给我写信
          </a>
        </div>
      </div>
    </section>

    <section id="about" class="section intro-section">
      <div class="section-kicker">About</div>
      <div class="intro-grid">
        <h2>把复杂问题拆开，再把答案做得足够轻盈。</h2>
        <div class="intro-copy">
          <p>
            我习惯从人的真实需求出发，连接产品策略、视觉表达和工程落地。过去参与过工具型产品、品牌官网和数据体验设计，也喜欢在日常里记录灵感。
          </p>
          <p>
            目前关注 AI 辅助创作、个人知识管理和更有温度的人机协作界面。
          </p>
        </div>
      </div>
    </section>

    <section id="work" class="section work-section" aria-labelledby="work-title">
      <div class="section-heading">
        <div>
          <div class="section-kicker">Selected Work</div>
          <h2 id="work-title">近期作品</h2>
        </div>
        <a class="text-link" href="mailto:hello@example.com">索取完整作品集</a>
      </div>

      <div class="work-grid">
        <article v-for="work in works" :key="work.title" class="work-card">
          <div class="work-thumb" :class="work.theme"></div>
          <div class="work-body">
            <p class="work-meta">{{ work.meta }}</p>
            <h3>{{ work.title }}</h3>
            <p>{{ work.description }}</p>
          </div>
        </article>
      </div>
    </section>

    <section
      id="experience"
      class="section experience-section"
      aria-labelledby="experience-title"
    >
      <div class="section-kicker">Experience</div>
      <h2 id="experience-title">经历与能力</h2>
      <div class="timeline">
        <div class="timeline-item">
          <span>2024 - Now</span>
          <div>
            <h3>独立创作者 / 产品设计师</h3>
            <p>
              负责从需求澄清、原型设计到前端实现的完整流程，服务个人品牌和早期产品。
            </p>
          </div>
        </div>
        <div class="timeline-item">
          <span>2021 - 2024</span>
          <div>
            <h3>数字产品团队</h3>
            <p>
              参与 SaaS 工具、运营后台和内容平台建设，沉淀组件化设计与交互规范。
            </p>
          </div>
        </div>
        <div class="timeline-item">
          <span>Skills</span>
          <div class="skill-list" aria-label="技能列表">
            <span v-for="skill in skills" :key="skill">{{ skill }}</span>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="contact-section" aria-labelledby="contact-title">
      <div class="contact-inner">
        <p class="section-kicker">Contact</p>
        <h2 id="contact-title">有项目、合作或一个还没成形的想法？</h2>
        <p>欢迎把它丢过来，我们可以一起把它整理清楚。</p>
        <div class="contact-actions">
          <a class="button primary" href="mailto:hello@example.com">
            hello@example.com
          </a>
          <a
            class="button secondary"
            href="https://github.com/"
            target="_blank"
            rel="noreferrer"
          >
            GitHub
          </a>
          <a
            class="button secondary"
            href="https://www.linkedin.com/"
            target="_blank"
            rel="noreferrer"
          >
            LinkedIn
          </a>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <span>© 2026 孙婉晴</span>
    <a href="#top">回到顶部</a>
  </footer>
</template>
