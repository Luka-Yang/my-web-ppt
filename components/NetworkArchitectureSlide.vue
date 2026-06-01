<template>
  <main class="arch-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · 3.1</p>
      <h1>FabGPT Network Architecture</h1>
      <p class="subtitle">
        Hover each stage to highlight its role in the FabGPT pipeline.
      </p>
    </section>

    <section class="stage-strip">
      <button
        v-for="stage in stages"
        :key="stage.id"
        :class="{ active: activeStage.id === stage.id }"
        @mouseenter="activeStage = stage"
        @focus="activeStage = stage"
      >
        {{ stage.id }} {{ stage.title }}
      </button>
    </section>

    <section class="figure-wrap">
      <div class="image-layer">
        <img src="/fabgpt-architecture.png" alt="FabGPT network architecture" />
        <div class="highlight" :style="activeStage.box"></div>
      </div>
    </section>

    <section class="note">
      <span>{{ activeStage.id }}</span>
      <div>
        <strong>{{ activeStage.title }}</strong>
        <p>{{ activeStage.desc }}</p>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const stages = [
  {
    id: '01',
    title: 'Modal Enhancement',
    desc: 'Extracts image, OCR text marks, and label features, then enhances visual and textual tokens.',
    box: { left: '18%', top: '1%', width: '33%', height: '90%' },
  },
  {
    id: '02',
    title: 'Detection',
    desc: 'Uses enhanced image and text tokens to produce supervised defect masks through the detection head.',
    box: { left: '50.5%', top: '1%', width: '15%', height: '90%' },
  },
  {
    id: '03',
    title: 'Q&A',
    desc: 'Combines image tokens, mask tokens, and user question tokens for the final defect-related answer.',
    box: { left: '65%', top: '1%', width: '20%', height: '90%' },
  },
]

const activeStage = ref(stages[0])
</script>

<style scoped>
.arch-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 18px 52px 20px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.12), transparent 30%),
    radial-gradient(circle at 20% 88%, rgba(95, 127, 137, 0.08), transparent 34%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow {
  margin: 0 0 5px;
  color: #5f7f89;
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.17em;
  text-transform: uppercase;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 32px;
  line-height: 1.04;
  font-weight: 400;
}

.subtitle {
  margin: 6px 0 0;
  color: #8a9ca3;
  font-size: 12px;
}

.stage-strip {
  margin-top: 13px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.stage-strip button {
  height: 34px;
  border-radius: 999px;
  border: 1px solid rgba(120, 145, 154, 0.20);
  background: rgba(255, 255, 255, 0.58);
  color: #314f5a;
  font-size: 12px;
  cursor: pointer;
  transition: 160ms ease;
}

.stage-strip button:hover,
.stage-strip button.active {
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.94);
  border-color: rgba(95, 127, 137, 0.55);
  box-shadow: 0 10px 22px rgba(31, 41, 51, 0.08);
}

.figure-wrap {
  position: relative;
  margin-top: 13px;
  flex: 1;
  min-height: 0;
  padding: 10px 12px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid rgba(120, 145, 154, 0.22);
  box-shadow: 0 14px 30px rgba(31, 41, 51, 0.07);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.image-layer {
  position: relative;
  width: 100%;
  max-height: 100%;
  aspect-ratio: 1865 / 768;
}

.image-layer img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: grayscale(100%) contrast(1.04);
  display: block;
}

.highlight {
  position: absolute;
  border-radius: 16px;
  border: 2px solid rgba(70, 120, 140, 0.75);
  background: rgba(95, 160, 180, 0.12);
  box-shadow: 0 0 0 999px rgba(255, 255, 255, 0.18);
  pointer-events: none;
  transition: 220ms ease;
}

.note {
  margin-top: 12px;
  min-height: 54px;
  display: grid;
  grid-template-columns: 34px 1fr;
  gap: 13px;
  align-items: start;
  padding: 11px 14px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.56);
  border-left: 4px solid rgba(95, 127, 137, 0.42);
}

.note span {
  width: 29px;
  height: 29px;
  display: grid;
  place-items: center;
  border-radius: 11px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.note strong {
  color: #1f2933;
  font-size: 13.2px;
  font-weight: 500;
}

.note p {
  margin: 4px 0 0;
  color: #6b7d86;
  font-size: 11.3px;
  line-height: 1.25;
}
</style>