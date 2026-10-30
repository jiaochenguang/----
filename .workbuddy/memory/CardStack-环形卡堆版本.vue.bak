<script setup>
import { ref, computed } from 'vue'
import { assetUrl } from '@/utils/assets'

/* 轮播数据：每张卡一个标题 */
const slides = [
  { title: '霓虹之后', img: 'lunbo1.png' },
  { title: '山海入梦', img: 'lunbo2.png' },
  { title: '2049号街区', img: 'lunbo3.png' },
]

const len = slides.length

/* 当前激活索引（最上层卡片） */
const current = ref(0)

/* 拖拽状态 */
const dragging = ref(false)
let startX = 0
let dragX = 0
const SWIPE_THRESHOLD = 60

/* 环形差值：把下标差折叠到 [-half, half]，实现首尾循环 */
function ringDiff(index) {
  let diff = index - current.value
  const half = Math.floor(len / 2)
  if (diff > half) diff -= len
  if (diff < -half) diff += len
  return diff
}

/* 每张卡的样式：环形卡堆位形 + 拖动位移 */
function getCardStyle(index) {
  const diff = ringDiff(index)
  const abs = Math.abs(diff)
  const sign = diff === 0 ? 0 : diff < 0 ? -1 : 1

  /* 位形：0 中间（满大），1 左右（缩小，被压 1/6，露出 5/6） */
  let x = 0
  let scale = 1
  let z = 100

  if (abs === 0) {
    x = 0
    scale = 1
    z = 100
  } else if (abs === 1) {
    /* 左右卡：向两侧移，内侧插入中间卡下方（露出 5/6） */
    x = 260 * sign
    scale = 0.73
    z = 50
  }

  /* 拖拽时位移：当前卡全跟手，侧卡阻尼 0.6 */
  const damp = abs === 0 ? 1 : 0.6
  const finalX = x + dragX * damp
  const transition = dragging.value ? 'none' : 'transform 0.4s cubic-bezier(0.22, 0.61, 0.36, 1)'

  return {
    transform: `translateX(${finalX}px) scale(${scale})`,
    zIndex: z,
    transition,
  }
}

/* 中间卡（diff===0）显示文字 */
function isActive(index) {
  return ringDiff(index) === 0
}

function next() {
  current.value = (current.value + 1) % len
}

function prev() {
  current.value = (current.value - 1 + len) % len
}

function onPointerDown(e) {
  if (e.pointerType === 'mouse' && e.button !== 0) return
  dragging.value = true
  startX = e.clientX
  dragX = 0
}

function onWindowMove(e) {
  if (!dragging.value) return
  dragX = e.clientX - startX
}

function onWindowUp() {
  if (!dragging.value) return
  const dx = dragX
  dragging.value = false
  dragX = 0
  window.removeEventListener('pointermove', onWindowMove)
  window.removeEventListener('pointerup', onWindowUp)
  if (Math.abs(dx) > SWIPE_THRESHOLD) {
    dx < 0 ? next() : prev()
  }
}

function onPointerDownHandler(e) {
  onPointerDown(e)
  window.addEventListener('pointermove', onWindowMove)
  window.addEventListener('pointerup', onWindowUp)
}
</script>

<template>
  <div
    class="card-stack"
    :class="{ dragging }"
    @pointerdown="onPointerDownHandler"
    @dragstart.prevent
  >
    <div
      v-for="(card, i) in slides"
      :key="i"
      class="card"
      :class="{ active: isActive(i) }"
      :style="getCardStyle(i)"
    >
      <div class="card-img">
        <img :src="assetUrl(card.img)" :alt="card.title" draggable="false" />
      </div>

      <!-- 仅中间卡显示文字 -->
      <div v-if="isActive(i)" class="card-body">
        <div class="card-info">
          <p class="card-label">FEATURED STORY</p>
          <h3 class="card-title">{{ card.title }}</h3>
        </div>
        <img class="card-play" :src="assetUrl('paly2Icon.png')" alt="播放" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-stack {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: grab;
  touch-action: pan-y;
  user-select: none;
}

.card-stack.dragging {
  cursor: grabbing;
}

.card-stack img {
  -webkit-user-drag: none;
  pointer-events: none;
}

/* 所有卡绝对定位在中心，靠 transform 向两侧展开 */
.card {
  position: absolute;
  left: 50%;
  top: 50%;
  width: clamp(280px, 23.6vw, 453px);
  height: clamp(264px, 22.2vw, 427px);
  margin-left: calc(clamp(280px, 23.6vw, 453px) / -2);
  margin-top: calc(clamp(264px, 22.2vw, 427px) / -2);
  display: flex;
  flex-direction: column;
  border-radius: 27px;
  background: #09141a;
  padding: clamp(10px, 0.83vw, 16px);
  box-sizing: border-box;
  will-change: transform;
}

.card-img {
  flex: 1;
  border-radius: 18px;
  overflow: hidden;
  border: 1px solid var(--border-soft);
  background: #08141a;
}

.card-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* 中间卡：满大 + 描边阴影 + 文字 */
.card.active {
  opacity: 1;
  filter: none;
}

.card.active .card-img {
  border-color: rgba(255, 255, 255, 0.2);
  box-shadow: 0 18px 50px rgba(0, 0, 0, 0.65);
}

/* 左右卡：缩小变暗，被中间卡压住一部分 */
.card:not(.active) {
  opacity: 0.55;
  filter: brightness(0.7);
}

.card:not(.active) .card-img {
  border-radius: 16px;
}

/* 中间卡底部文字区 */
.card-body {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding: clamp(6px, 0.63vw, 12px) 0 0;
  background: transparent;
}

.card-label {
  margin-top: clamp(8px, 0.73vw, 14px);
  font-size: 10px;
  letter-spacing: 2px;
  color: var(--cyan);
}

.card-title {
  margin-top: 2px;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-1);
}

.card-play {
  width: clamp(16px, 1.25vw, 24px);
  height: clamp(16px, 1.25vw, 24px);
  flex-shrink: 0;
  align-self: flex-end;
}
</style>
