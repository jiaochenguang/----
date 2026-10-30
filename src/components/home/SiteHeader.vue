<script setup>
import { assetUrl } from '@/utils/assets'

const navLinks = ['创作工具', '灵感广场', '赛事活动', '图片灵感']
</script>

<template>
  <header class="site-header">
    <div class="header-inner">
      <div class="left">
        <img class="logo" :src="assetUrl('logo.png')" alt="灵想剧创" />
        <nav class="nav">
          <a v-for="link in navLinks" :key="link" href="#">{{ link }}</a>
        </nav>
      </div>

      <div class="right">
        <button class="btn-gold">加油包</button>
        <button class="btn-gold">会员中心</button>
        <button class="btn-login">登录 / 注册</button>
        <button class="theme-btn" aria-label="切换主题">
          <img :src="assetUrl('ModelBai.png')" alt="主题" />
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  position: relative;
  z-index: 10;
  height: 93px;
  background: #091114;
  border-bottom: 1px solid var(--border-soft);
}

.header-inner {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* 全宽 + 线性缩放左右 padding：1280→40px，1920→108px */
  padding-left: clamp(40px, 10.625vw - 96px, 108px);
  padding-right: clamp(40px, 10.625vw - 96px, 108px);
}

.left {
  display: flex;
  align-items: center;
  gap: 40px;
}

.logo {
  height: 38px;
  width: auto;
}

.nav {
  display: flex;
  gap: 32px;
}

.nav a {
  font-size: 14px;
  color: var(--text-1);
  transition: color 0.2s;
}

.nav a:hover {
  color: var(--cyan);
}

.right {
  display: flex;
  align-items: center;
  gap: 12px;
}

.btn-gold {
  padding: 7px 16px;
  border-radius: 16px;
  font-size: 13px;
  color: var(--gold);
  background: var(--gold-bg);
  border: 1px solid rgba(232, 179, 61, 0.35);
  transition: filter 0.2s;
}

.btn-gold:hover {
  filter: brightness(1.2);
}

.btn-login {
  padding: 7px 16px;
  border-radius: 16px;
  font-size: 13px;
  color: var(--text-1);
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid var(--border-soft);
}

.btn-login:hover {
  background: rgba(255, 255, 255, 0.12);
}

.theme-btn img {
  width: 20px;
  height: 20px;
  opacity: 0.85;
}

@media (max-width: 900px) {
  .nav {
    display: none;
  }
}

@media (max-width: 768px) {
  .site-header {
    height: 72px;
  }
}

@media (max-width: 576px) {
  .site-header {
    height: 64px;
  }

  .btn-gold {
    display: none;
  }

  .logo {
    height: 32px;
  }

  .btn-login {
    padding: 6px 12px;
  }
}
</style>
