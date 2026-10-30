<script setup>
import { ref } from "vue";
import { assetUrl } from "@/utils/assets";

const chips = ["全部 Skill", "人物动态", "智能运镜", "氛围特效", "故事短片"];
const activeChip = ref(0);

/* 列表图片暂用 itemImg 占位 */
const skills = [
  { title: "人物微表情", desc: "让剧中动起来，真实更有感" },
  { title: "电影感推进", desc: "创建电影长片镜头" },
  { title: "粒子觉醒", desc: "无痕替换入未来能量" },
  { title: "奇幻预演片", desc: "AI生成民间主题故事短片" },
];
</script>

<template>
  <section class="skill-section container">
    <div class="section-head">
      <div>
        <p class="label">AI VIDEO SKILLS</p>
        <h2>热门创作玩法</h2>
      </div>
      <a class="more" href="#">
        浏览全部
        <img :src="assetUrl('leftArrow.png')" alt="" />
      </a>
    </div>

    <div class="chips">
      <button
        v-for="(chip, i) in chips"
        :key="chip"
        class="chip"
        :class="{ active: i === activeChip }"
        @click="activeChip = i"
      >
        {{ chip }}
      </button>
    </div>

    <div class="grid">
      <div v-for="skill in skills" :key="skill.title" class="card">
        <img class="cover" :src="assetUrl('itemImg.png')" :alt="skill.title" />
        <div class="cardBottom"> 
          <h3>{{ skill.title }}</h3>
        <p class="desc">{{ skill.desc }}</p>
        <a class="try" href="#">
          立即体验
          <img :src="assetUrl('leftArrow2.png')" alt="" />
        </a>
        </div>
        
      </div>
    </div>
  </section>
</template>

<style scoped>
.skill-section {
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

.more {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: var(--text-2);
}

.more:hover {
  color: var(--text-1);
}

.more img {
  width: 14px;
  height: 14px;
}

.chips {
  display: flex;
  gap: 10px;
  margin-top: 22px;
}

.chip {
  padding: 6px 14px;
  border-radius: 15px;
  font-size: 12px;
  color: var(--text-2);
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid var(--border-soft);
  transition: all 0.2s;
}

.chip.active {
  color: #04252a;
  background: var(--cyan);
  border-color: var(--cyan);
  font-weight: 600;
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-top: 26px;
}
.card {
  background: #091216;
  border-radius: 12px 12px 12px 12px;
}
.cardBottom{
  padding: 0px 16px 12px;
  box-sizing: border-box;
}
.card .cover {
  width: 100%;
  aspect-ratio: 4 / 3;
  object-fit: cover;
  border-radius: 12px;
}

.card h3 {
  margin-top: 12px;
  font-size: 16px;
  font-weight: 600;
}

.desc {
  margin-top: 4px;
  font-size: 12px;
  color: var(--text-2);
}

.try {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  margin-top: 10px;
  font-size: 13px;
  color: var(--text-1);
}

.try:hover {
  color: var(--cyan);
}

.try img {
  width: 14px;
  height: 14px;
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
  .chips {
    flex-wrap: wrap;
  }
}
</style>
