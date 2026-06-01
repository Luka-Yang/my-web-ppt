<template>
  <main class="journey-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · Case Flow</p>
      <h1>Wafer Example Through FabGPT</h1>
      <p class="subtitle">
        Real case: SEM-WaD particle image processed through enhancement, detection, Q&amp;A, and loss feedback
      </p>
    </section>

    <section class="tabs">
      <button
        v-for="item in steps"
        :key="item.id"
        :class="{ active: active.id === item.id }"
        @mouseenter="active = item"
        @focus="active = item"
        @click="active = item"
      >
        {{ item.id }} {{ item.shortTitle }}
      </button>
    </section>

    <section class="main">
      <section class="image-card">
        <p class="label">Real input case</p>

        <div class="image-wrap">
          <img src="/semwad/particle.png" alt="Particle defect SEM example" />
          <div v-if="active.showFocus" class="focus-ring"></div>
          <div v-if="active.showMask" class="mask-layer"></div>
        </div>

        <div class="case-row">
          <strong>Case</strong>
          <span>Particle defect candidate</span>
        </div>
      </section>

      <section class="flow-card" :key="active.id">
        <p class="label">Current stage</p>
        <h2>{{ active.headline }}</h2>

        <div class="mini-flow">
          <span>{{ active.before }}</span>
          <b>→</b>
          <span>{{ active.after }}</span>
        </div>

        <div class="calc-box">
          <p class="mini-label">Calculation path</p>
          <div v-for="line in active.calculation" :key="line" class="calc-line">
            {{ line }}
          </div>
        </div>

        <div class="result-box">
          <strong>{{ active.resultTitle }}</strong>
          <p>{{ active.result }}</p>
        </div>
      </section>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const steps = [
  {
    id: '01',
    shortTitle: 'Feature enhancement',
    headline: 'Estimate particle category and strengthen related features',
    before: 'Raw SEM image',
    after: 'Particle-aware tokens',
    calculation: [
      'Image-label similarity: Good 0.06, Hole 0.09, Particle 0.74, Scratch 0.07, Pattern 0.04',
      'Highest score = Particle 0.74 → predicted category Pn = Particle',
      'Pn guides image/text features → Vimg and Vtxt become particle-aware',
      'Adapters add expert prompt features → Timg and Ttxt',
    ],
    resultTitle: 'Stage output',
    result:
      'The model receives tokens that emphasize particle-related cues rather than background texture',
    showFocus: true,
    showMask: false,
  },
  {
    id: '02',
    shortTitle: 'Defect localization',
    headline: 'Convert enhanced tokens into a pixel-level defect mask',
    before: 'Timg + Ttxt',
    after: 'Defect mask',
    calculation: [
      'Image token and text token are fused to combine visual evidence with defect meaning',
      'Decoder upsamples the feature map 4 times to recover spatial resolution',
      'Predicted defect pixels = 42, total pixels = 4096',
      'Mask ratio = 42 / 4096 = 1.03%',
    ],
    resultTitle: 'Stage output',
    result:
      'The model identifies a small particle candidate region instead of only producing an image-level class',
    showFocus: false,
    showMask: true,
  },
  {
    id: '03',
    shortTitle: 'Knowledge answer',
    headline: 'Use image evidence, mask location, and user query together',
    before: 'Image + mask + query',
    after: 'Answer instruction',
    calculation: [
      'Query example: What may cause this defect',
      'Visual instruction is generated from image and mask tokens',
      'Similarity between visual instruction and query = 0.82',
      'Scaling factor a = 0.82 → visual evidence is strongly used',
    ],
    resultTitle: 'Stage output',
    result:
      'The model answers that the particle-like abnormality may be related to surface contamination, residue, or local process disturbance',
    showFocus: false,
    showMask: true,
  },
  {
    id: '04',
    shortTitle: 'Loss feedback',
    headline: 'Update the model with detection and dialogue losses',
    before: 'Model prediction',
    after: 'Training correction',
    calculation: [
      'Focal Loss = 0.32 for hard pixels',
      'Dice Loss = 0.18 for mask overlap',
      'CE classification = 0.24, CE Q&A = 0.16',
      'Total loss = 0.32 + 0.18 + 0.24 + 0.16 = 0.90',
    ],
    resultTitle: 'Training output',
    result:
      'The model is updated to improve localization, classification, and defect-related answer generation',
    showFocus: false,
    showMask: true,
  },
]

const active = ref(steps[0])
</script>

<style scoped>
.journey-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 16px 50px 12px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.10), transparent 30%),
    radial-gradient(circle at 18% 88%, rgba(95, 127, 137, 0.07), transparent 34%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow,
.label,
.mini-label {
  color: #5f7f89;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  font-weight: 500;
  font-size: 9.5px;
}

.eyebrow {
  margin: 0 0 4px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 29px;
  line-height: 1.03;
  font-weight: 400;
}

.subtitle {
  margin: 5px 0 0;
  color: #8fa1a8;
  font-size: 11px;
}

.tabs {
  margin-top: 14px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.tabs button {
  height: 30px;
  border-radius: 999px;
  border: 1px solid rgba(120, 145, 154, 0.20);
  background: rgba(255, 255, 255, 0.58);
  color: #314f5a;
  font-size: 11px;
  cursor: pointer;
  transition:
    transform 180ms ease,
    background 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.tabs button.active,
.tabs button:hover {
  transform: translateY(-2px);
  background: rgba(255, 255, 255, 0.94);
  border-color: rgba(95, 127, 137, 0.55);
  box-shadow: 0 8px 18px rgba(31, 41, 51, 0.07);
}

.main {
  margin-top: 16px;
  display: grid;
  grid-template-columns: 0.76fr 1.24fr;
  gap: 30px;
  align-items: start;
}

.label {
  margin: 0 0 7px;
}

.image-card,
.flow-card {
  animation: fadeUp 240ms ease both;
}

.image-wrap {
  position: relative;
  height: 210px;
  border-radius: 21px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid rgba(120, 145, 154, 0.22);
  box-shadow: 0 12px 26px rgba(31, 41, 51, 0.06);
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-wrap img {
  width: 88%;
  height: 88%;
  object-fit: contain;
  filter: grayscale(100%) contrast(1.04);
}

.focus-ring {
  position: absolute;
  left: 49%;
  top: 27%;
  width: 66px;
  height: 66px;
  border-radius: 50%;
  border: 3px solid rgba(70, 120, 140, 0.78);
  background: rgba(95, 160, 180, 0.12);
  transform: translate(-50%, -50%);
  animation: pulse 1.5s ease-out infinite;
}

.mask-layer {
  position: absolute;
  left: 49%;
  top: 27%;
  width: 70px;
  height: 70px;
  border-radius: 50%;
  background: rgba(70, 120, 140, 0.22);
  border: 3px solid rgba(70, 120, 140, 0.78);
  transform: translate(-50%, -50%);
  box-shadow: 0 0 0 999px rgba(255, 255, 255, 0.18);
  animation: maskIn 240ms ease both;
}

.case-row {
  margin-top: 8px;
  display: flex;
  gap: 8px;
  color: #667983;
  font-size: 11.5px;
}

.case-row strong {
  color: #1f2933;
}

.flow-card h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 23px;
  line-height: 1.04;
  font-weight: 400;
}

.mini-flow {
  margin-top: 9px;
  display: grid;
  grid-template-columns: 1fr 28px 1fr;
  gap: 8px;
  align-items: center;
}

.mini-flow span {
  padding: 8px 10px;
  border-radius: 15px;
  background: rgba(255, 255, 255, 0.58);
  border: 1px solid rgba(120, 145, 154, 0.18);
  color: #314f5a;
  font-size: 11.5px;
  text-align: center;
}

.mini-flow b {
  color: #5f7f89;
  font-size: 17px;
  text-align: center;
}

.calc-box {
  margin-top: 9px;
  padding: 9px 12px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0 17px 17px 0;
}

.calc-line {
  margin-top: 4px;
  color: #667983;
  font-size: 10.7px;
  line-height: 1.24;
}

.result-box {
  margin-top: 8px;
  padding: 8px 12px;
  border-radius: 17px;
  background: rgba(255, 255, 255, 0.58);
  border: 1px solid rgba(120, 145, 154, 0.18);
}

.result-box strong {
  color: #1f2933;
  font-size: 12.6px;
  font-weight: 600;
}

.result-box p {
  margin: 4px 0 0;
  color: #667983;
  font-size: 10.7px;
  line-height: 1.24;
}

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(7px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pulse {
  from {
    opacity: 0.85;
    transform: translate(-50%, -50%) scale(0.9);
  }
  to {
    opacity: 0;
    transform: translate(-50%, -50%) scale(1.28);
  }
}

@keyframes maskIn {
  from {
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.82);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
  }
}
</style>