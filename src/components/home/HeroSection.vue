<script setup>
import { assetUrl } from '@/utils/assets'
import CardStack from './CardStack.vue'
</script>

<template>
  <section class="hero">
    <div class="hero-inner">
      <!-- 左侧文案 -->
      <div class="hero-copy">
        <p class="hero-en">LINGXIANG JUCHUANG</p>

        <h1 class="hero-title">
          灵感无界，<br />
          <div class="hero-title-en">剧创未来。</div>
        </h1>

        <p class="hero-sub">
          免费 AI 生成，支持文生图与图生图：输入描述或上传参考图，<br />
          快速生成高质量视觉作品。
        </p>

        <div class="hero-actions">
          <button class="btn-primary">
            开始创作
            <img :src="assetUrl('leftArrow2.png')" alt="" />
          </button>
          <button class="btn-preview">
            <img class="preview-icon" :src="assetUrl('playIcon.png')" alt="" />
            观看预览
          </button>
        </div>

        <div class="hero-tags">
          <span class="tag"><i class="dot-mini"></i>4K 高清</span>
          <span class="tag"><i class="dot-mini"></i>智能运镜</span>
          <span class="tag"><i class="dot-mini"></i>创意特效</span>
        </div>
      </div>

      <!-- 右侧：光晕图 + 三卡层叠 -->
      <div class="hero-visual">
        <!-- <img class="hero-glow" :src="assetUrl('guangyun.png')" alt="" /> -->
        <CardStack />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  width: 100%;
  overflow: hidden;
  background: var(--bg-page);
}

.hero-inner {
  position: relative;
  /* 1920 时整块高 567，左右 padding 108 */
  width: 100%;
  max-width: 1920px;
  height: 567px;
  margin: 0 auto;
  padding-left: clamp(40px, 10.625vw - 96px, 108px);
  padding-right: clamp(40px, 10.625vw - 96px, 108px);
  display: flex;
  align-items: center;
  gap: 24px;
}

.hero-copy {
  flex: 0 0 42%;
  max-width: 560px;
}

.hero-en {
  font-size: 13px;
  letter-spacing: 4px;
  color: var(--cyan);
}

.hero-title {
  margin-top: 16px;
  font-size: clamp(40px, 4.5vw, 56px);
  font-weight: 700;
  line-height: 1.18;
  color: var(--text-1);
}

.dot {
  color: var(--cyan);
}

.hero-sub {
  margin-top: 20px;
  font-size: clamp(14px, 1.1vw, 16px);
  line-height: 1.9;
  color: var(--text-2);
}

.hero-actions {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-top: 30px;
}

.btn-primary {
  display: flex;
  align-items: center;
  gap: 8px;
  height: 48px;
  padding: 0 30px;
  border-radius: 999px;
  background: linear-gradient(90deg, var(--cyan-deep), var(--cyan));
  color: #04252a;
  font-size: 16px;
  font-weight: 600;
  transition: filter 0.2s;
}

.btn-primary:hover {
  filter: brightness(1.1);
}

.btn-primary img {
  width: 16px;
  height: 16px;
}

.btn-preview {
  display: flex;
  align-items: center;
  gap: 10px;
  height: 48px;
  padding: 0 26px;
  border-radius: 999px;
  background: rgba(10, 18, 30, 0.7);
  border: 1px solid var(--border-soft);
  color: var(--text-1);
  font-size: 16px;
}

.preview-icon {
  width: 20px;
  height: 20px;
}

.hero-tags {
  display: flex;
  gap: 22px;
  margin-top: 26px;
}

.tag {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: var(--text-3);
}

.dot-mini {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: var(--text-3);
}

/* ---------- 右侧视觉区 ---------- */
.hero-visual {
  position: relative;
  flex: 1;
  height: 100%;
  background: url('https://dyanyapi.elecottech.com/h5_static_img/LXJC/guangyun.png') no-repeat center;
  background-size: 100% auto;
}

/* 光晕图：作为卡片后方的光晕背景，铺在卡片下层 */
.hero-glow {
  position: absolute;
  right: 0;
  bottom: -60px;
  width: clamp(520px, 60vw, 1150px);
  height: auto;
  z-index: 0;
  pointer-events: none;
}

.hero-visual :deep(.card-stack) {
  position: relative;
  z-index: 1;
}
.hero-title-en{
  position: relative;
  left: 20%;
}

@media (max-width: 1024px) {
  .hero-inner {
    height: auto;
    flex-direction: column;
    align-items: flex-start;
    padding-top: 48px;
    padding-bottom: 48px;
  }

  .hero-copy {
    flex: none;
    width: 100%;
    max-width: none;
  }

  .hero-visual {
    width: 100%;
    height: 340px;
    margin-top: 24px;
  }
}

@media (max-width: 576px) {
  .hero-actions {
    flex-wrap: wrap;
  }

  .hero-tags {
    flex-wrap: wrap;
    gap: 14px;
  }
}
</style>
