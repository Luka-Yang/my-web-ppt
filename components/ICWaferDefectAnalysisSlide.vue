<template>
  <main class="wafer-page">
    <section class="header">
      <p class="eyebrow">Preliminaries · 2.1</p>
      <h1>SEM-WaD Dataset and Defect Types</h1>
      <p class="subtitle">
        SEM wafer analysis identifies defect type, location, and possible process-related causes.
      </p>
    </section>

    <section class="gallery">
      <button
        v-for="item in defects"
        :key="item.name"
        class="defect-card"
        :class="{ active: active.name === item.name }"
        @mouseenter="active = item"
        @focus="active = item"
      >
        <img :src="item.src" :alt="item.name" />
        <span>{{ item.name }}</span>
      </button>
    </section>

    <section class="selected">
      <span class="number">{{ active.id }}</span>

      <div>
        <p class="label">Selected Defect</p>
        <h2>{{ active.name }}</h2>
        <p class="desc">{{ active.description }}</p>
      </div>

      <div class="task-tags">
        <span>Type</span>
        <span>Location</span>
        <span>Cause</span>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const base = import.meta.env.BASE_URL

const defects = [
  { id: '01', name: 'Good', src: `${base}semwad/good.png`, description: 'Normal wafer surface without obvious defect patterns.' },
  { id: '02', name: 'Hole', src: `${base}semwad/hole.png`, description: 'Hole-like surface abnormality that may indicate local material or process issues.' },
  { id: '03', name: 'Particle', src: `${base}semwad/particle.png`, description: 'Foreign particle or contamination observed on the wafer surface.' },
  { id: '04', name: 'Scratch', src: `${base}semwad/scratch.png`, description: 'Scratch-like pattern that may reflect mechanical damage or surface disturbance.' },
  { id: '05', name: 'Pattern Deformation', src: `${base}semwad/pattern-deformation.png`, description: 'Deformation in repeated wafer surface structures or local pattern morphology.' },
]

const active = ref(defects[0])
</script>

<style scoped>
.wafer-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 24px 60px 24px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.12), transparent 30%),
    radial-gradient(circle at 20% 88%, rgba(95, 127, 137, 0.08), transparent 34%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow,
.label {
  color: #5f7f89;
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.17em;
  text-transform: uppercase;
}

.eyebrow {
  margin: 0 0 7px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 36px;
  line-height: 1.04;
  font-weight: 400;
}

.subtitle {
  margin: 7px 0 0;
  color: #8a9ca3;
  font-size: 12.8px;
}

.gallery {
  margin-top: 26px;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 16px;
}

.defect-card {
  cursor: pointer;
  height: 225px;
  box-sizing: border-box;
  padding: 9px 9px 10px;
  border-radius: 20px;
  border: 1px solid rgba(120, 145, 154, 0.22);
  background: rgba(255, 255, 255, 0.54);
  display: grid;
  grid-template-rows: 1fr auto;
  gap: 8px;
  transition:
    transform 180ms ease,
    background 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.defect-card:hover,
.defect-card.active {
  transform: translateY(-6px);
  background: rgba(255, 255, 255, 0.95);
  border-color: rgba(95, 127, 137, 0.55);
  box-shadow: 0 16px 34px rgba(31, 41, 51, 0.09);
}

.defect-card img {
  width: 100%;
  height: 176px;
  object-fit: cover;
  border-radius: 14px;
  filter: grayscale(100%);
}

.defect-card span {
  color: #314f5a;
  font-size: 11.5px;
  line-height: 1.1;
  text-align: center;
}

.selected {
  margin-top: 22px;
  min-height: 102px;
  box-sizing: border-box;
  padding: 16px 18px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.58);
  border: 1px solid rgba(120, 145, 154, 0.20);
  display: grid;
  grid-template-columns: 40px 1fr auto;
  gap: 18px;
  align-items: center;
  transition:
    transform 180ms ease,
    background 180ms ease,
    box-shadow 180ms ease;
}

.selected:hover {
  transform: translateY(-4px);
  background: rgba(255, 255, 255, 0.88);
  box-shadow: 0 14px 30px rgba(31, 41, 51, 0.07);
}

.number {
  width: 32px;
  height: 32px;
  display: grid;
  place-items: center;
  border-radius: 13px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10.5px;
}

.selected .label {
  margin: 0 0 5px;
}

.selected h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 27px;
  line-height: 1.04;
  font-weight: 400;
}

.desc {
  margin: 6px 0 0;
  color: #6b7d86;
  font-size: 12.2px;
  line-height: 1.28;
}

.task-tags {
  display: flex;
  gap: 8px;
  flex-wrap: nowrap;
}

.task-tags span {
  padding: 7px 11px;
  border-radius: 999px;
  background: rgba(244, 247, 247, 0.78);
  border: 1px solid rgba(120, 145, 154, 0.22);
  color: #314f5a;
  font-size: 11px;
  white-space: nowrap;
}
</style>