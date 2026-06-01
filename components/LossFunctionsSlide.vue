<template>
  <main class="loss-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · 3.5</p>
      <h1>Loss Functions</h1>
      <p class="subtitle">
        FabGPT uses segmentation and classification losses to constrain detection and dialogue learning.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">Training Objective</p>
        <h2>Optimize localization, segmentation, classification, and Q&amp;A.</h2>

        <p>
          Three losses are combined so the model can learn pixel-level masks,
          defect categories, and language responses at the same time.
        </p>

        <div class="total">
          <p class="mini-label">Overall loss</p>
          <div>
            L = αL<sub>focal</sub> + βL<sub>dice</sub> + δL<sub>ce</sub><sup>1</sup> + εL<sub>ce</sub><sup>2</sup>
          </div>
          <span>Default: α = β = δ = ε = 1</span>
        </div>
      </section>

      <section class="right">
        <p class="label">Loss Map</p>

        <button
          v-for="loss in losses"
          :key="loss.id"
          class="loss-row"
          :class="{ active: activeLoss.id === loss.id }"
          @mouseenter="activeLoss = loss"
          @focus="activeLoss = loss"
        >
          <span>{{ loss.id }}</span>
          <div>
            <strong>{{ loss.name }}</strong>
            <p>{{ loss.role }}</p>
          </div>
        </button>

        <div class="feedback">
          <p class="mini-label">Interactive feedback</p>
          <h3>{{ activeLoss.name }}</h3>
          <p>{{ activeLoss.detail }}</p>
          <div class="formula" v-html="activeLoss.formula"></div>
        </div>
      </section>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const losses = [
  {
    id: '01',
    name: 'Focal Loss',
    role: 'Focuses on hard-to-classify pixels.',
    detail:
      'Focal Loss reduces the effect of easy pixels and gives more weight to difficult or misclassified pixels, helping with class imbalance.',
    formula:
      'L<sub>focal</sub> = − 1/(H×W) Σ(1 − p<sub>i</sub>)<sup>γ</sup> log(p<sub>i</sub>)',
  },
  {
    id: '02',
    name: 'Dice Loss',
    role: 'Maximizes mask overlap with ground truth.',
    detail:
      'Dice Loss encourages the predicted mask to overlap with the true defect region, improving segmentation and localization quality.',
    formula:
      'L<sub>dice</sub> = − Σy<sub>i</sub>ŷ<sub>i</sub> / (Σy<sub>i</sub><sup>2</sup> + Σŷ<sub>i</sub><sup>2</sup>)',
  },
  {
    id: '03',
    name: 'Cross-Entropy Loss',
    role: 'Supports classification and Q&A learning.',
    detail:
      'Cross-Entropy Loss measures the difference between predicted and target categories or text tokens.',
    formula:
      'L<sub>ce</sub> = − Σ y<sub>i</sub> log(p<sub>i</sub>)',
  },
]

const activeLoss = ref(losses[0])
</script>

<style scoped>
.loss-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 22px 56px 18px;
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
}

.eyebrow {
  margin: 0 0 6px;
  font-size: 10px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 34px;
  line-height: 1.04;
  font-weight: 400;
}

.subtitle {
  margin: 7px 0 0;
  color: #a0aeb4;
  font-size: 11.8px;
}

.main {
  margin-top: 36px;
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 50px;
  align-items: start;
}

.label {
  margin: 0 0 10px;
  font-size: 10px;
}

.left h2 {
  margin: 0;
  max-width: 560px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 31px;
  line-height: 1.06;
  font-weight: 400;
}

.left > p {
  margin: 18px 0 0;
  max-width: 520px;
  color: #667983;
  font-size: 11.8px;
  line-height: 1.38;
}

.total {
  margin-top: 24px;
  padding: 14px 16px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  background: rgba(255, 255, 255, 0.56);
  border-radius: 0 18px 18px 0;
}

.mini-label {
  margin: 0 0 7px;
  font-size: 9px;
}

.total div {
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 18px;
  line-height: 1.25;
}

.total span {
  display: block;
  margin-top: 8px;
  color: #667983;
  font-size: 11.2px;
}

.right {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.loss-row {
  width: 100%;
  display: grid;
  grid-template-columns: 42px 1fr;
  gap: 14px;
  align-items: start;
  padding: 10px 0 11px;
  background: transparent;
  border: none;
  border-bottom: 1px solid rgba(120, 145, 154, 0.20);
  text-align: left;
  cursor: pointer;
}

.loss-row span {
  width: 33px;
  height: 33px;
  border-radius: 12px;
  display: grid;
  place-items: center;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.loss-row.active span {
  background: #dce8eb;
  color: #314f5a;
}

.loss-row strong {
  display: block;
  color: #1f2933;
  font-size: 13.8px;
  line-height: 1.22;
  font-weight: 600;
}

.loss-row p {
  margin: 3px 0 0;
  color: #6e8089;
  font-size: 11.3px;
  line-height: 1.3;
}

.feedback {
  margin-top: 8px;
  padding: 12px 15px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0 18px 18px 0;
}

.feedback h3 {
  margin: 0 0 5px;
  color: #1f2933;
  font-size: 13.8px;
  line-height: 1.25;
  font-weight: 600;
}

.feedback p:not(.mini-label) {
  margin: 0;
  color: #667983;
  font-size: 11.3px;
  line-height: 1.32;
}

.formula {
  margin-top: 9px;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 15.8px;
  line-height: 1.25;
}
</style>