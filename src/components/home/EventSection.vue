<script setup>
import { assetUrl } from "@/utils/assets";

/* 列表图片暂用 itemImg 占位 */
const events = [
  {
    title: "梦境短片征集活动",
    source: "©学习强国 · 梦境短片征集活动",
    duration: "00:24",
  },
  {
    title: "山海入梦",
    source: "©新华网 · 国风动效征集活动",
    duration: "00:44",
  },
  {
    title: "2049号街区",
    source: "©学习强国 · 科幻概念短片征集活动",
    duration: "00:56",
  },
  { title: "夏日来信", source: "©新华网 · 治愈微征集活动", duration: "00:38" },
];
</script>

<template>
  <section class="event-section container">
    <div class="section-head">
      <div>
        <p class="label">CURATED BY LINGGAN</p>
        <h2>Event</h2>
      </div>
      <div class="search">
        <svg
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
        >
          <circle cx="11" cy="11" r="7" />
          <line x1="21" y1="21" x2="16.5" y2="16.5" />
        </svg>
        <input type="text" placeholder="搜索相关赛事及评选" />
      </div>
    </div>

    <div class="grid">
      <div v-for="event in events" :key="event.title" class="card">
        <div class="cover-wrap">
          <img
            class="cover"
            :src="assetUrl('itemImg.png')"
            :alt="event.title"
          />
          <img class="play" :src="assetUrl('paly2Icon.png')" alt="播放" />
          <span class="duration">{{ event.duration }}</span>
        </div>
        <h3>{{ event.title }}</h3>
        <p class="source">{{ event.source }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.event-section {
  margin-top: 72px;
}

.section-head {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
}

.label {
  font-size: 12px;
  letter-spacing: 2px;
  color: var(--cyan);
}

h2 {
  margin-top: 6px;
  font-size: 28px;
  font-weight: 600;
}

.search {
  display: flex;
  align-items: center;
  gap: 8px;
  width: 226px;
  height: 42px;
  background: #111316;
  border-radius: 12px 12px 12px 12px;
  padding: 0 14px;
}

.search svg {
  width: 15px;
  height: 15px;
  color: var(--text-3);
  flex-shrink: 0;
}

.search input {
  width: 100%;
  border: none;
  outline: none;
  background: none;
  color: var(--text-1);
  font-size: 13px;
}

.search input::placeholder {
  color: #94A3B0;
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-top: 26px;
}

.cover-wrap {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
}

.cover {
  width: 100%;
  aspect-ratio: 16 / 10;
  object-fit: cover;
}

.play {
  position: absolute;
  left: 10px;
  bottom: 10px;
  width: 16px;
  height: 16px;
}

.duration {
  position: absolute;
  right: 8px;
  bottom: 8px;
  padding: 1px 6px;
  border-radius: 4px;
  background: rgba(0, 0, 0, 0.6);
  font-size: 11px;
  color: var(--text-1);
}

.card h3 {
  margin-top: 10px;
  font-size: 15px;
  font-weight: 600;
}

.source {
  margin-top: 4px;
  font-size: 12px;
  color: var(--text-3);
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }

  h2 {
    font-size: 24px;
  }
}

@media (max-width: 480px) {
  .section-head {
    flex-wrap: wrap;
    gap: 12px;
  }

  .search {
    width: 100%;
    max-width: 260px;
  }
}
</style>
