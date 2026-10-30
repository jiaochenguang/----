<script setup>
import { assetUrl } from "@/utils/assets";
</script>

<template>
  <section class="canvas-banner">
    <div class="canvas-inner">
      <div class="panel">
        <img class="deco left" :src="assetUrl('HBLeftImg.png')" alt="" />
        <div class="center">
          <p class="label">YOUR STORY STARTS HERE</p>
          <h2>创作，只需要一张画布</h2>
          <button class="btn-start">
            开始创作
            <img :src="assetUrl('leftArrow.png')" alt="" />
          </button>
        </div>
        <img class="deco right" :src="assetUrl('HBRightImg.png')" alt="" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.canvas-banner {
  margin-top: 24px;
  width: 100%;
  max-width: 1920px;
  /* 全宽 + 线性缩放左右 padding：1280→40px，1920→108px */
  padding-left: clamp(40px, 10.625vw - 96px, 108px);
  padding-right: clamp(40px, 10.625vw - 96px, 108px);
}

.canvas-inner {
  /* 全宽 + 动态左右 padding：1920 时 108px */
  width: 100%;
  margin: 0 auto;
  background: #0a1318;
  border-radius: 16px 16px 16px 16px;
}

.panel {
  position: relative;
  border-radius: 18px;
  /* background: var(--bg-panel); */
  /* border: 1px solid var(--border-soft); */
  padding: 36px 0 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  overflow: hidden;
  /* 内部内容按 max-width: 1200px 约束居中 */
  max-width: 1200px;
  margin: 0 auto;
}

.deco {
  width: 84px;
  height: 56px;
  object-fit: cover;
  border-radius: 8px;
}

.deco.left {
  left: 12%;
}

.deco.right {
  right: 12%;
}

.center {
  text-align: center;
}

.label {
  font-size: 11px;
  letter-spacing: 2px;
  color: var(--text-3);
}

h2 {
  margin-top: 6px;
  font-size: 24px;
  font-weight: 600;
}

.btn-start {
  margin-top: 16px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  width: 190px;
  height: 40px;
  border-radius: 18px;
  background: #0a1f26;
  font-family: PingFang SC, PingFang SC;
  font-weight: 600;
  font-size: 14px;
  color: #E8F5FA;
  justify-content: center;
}

.btn-start img {
  width: 14px;
  height: 14px;
}

@media (max-width: 1366px) {
  .panel {
    padding-left: 30px;
    padding-right: 30px;
  }
}

@media (max-width: 768px) {
  .deco {
    display: none;
  }

  .panel {
    padding: 26px 16px 24px;
  }

  h2 {
    font-size: 18px;
  }
}
</style>
