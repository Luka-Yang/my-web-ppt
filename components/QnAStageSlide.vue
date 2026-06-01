<template>
  <main class="qa-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · 3.4</p>
      <h1>Q&amp;A Stage</h1>
      <p class="subtitle">
        Reduces modality bias by aligning visual, mask, text, and user-query instructions.
      </p>
    </section>

    <section class="content">
      <section class="left">
        <p class="section-label">Problem</p>
        <h2>Fine-tuning may over-focus the model on image inputs.</h2>

        <div class="formula-box">
          <p class="mini-label">Instruction formats</p>
          <div class="formula">INS = Concat(x, T<sub>img</sub>, T<sub>que</sub>)</div>
          <div class="formula small">INS<sub>g</sub> = Concat(aT<sub>vis</sub>, T<sub>mas</sub>, T<sub>que</sub>)</div>
        </div>

        <p class="body-text">
          The common format may cause modality bias: the model can answer defect-related questions,
          but may neglect queries requiring broader process knowledge.
        </p>

        <div class="chips">
          <span>Image over-focus</span>
          <span>Query neglect</span>
          <span>Knowledge imbalance</span>
        </div>
      </section>

      <section class="right">
        <p class="section-label">FabGPT Solution</p>

        <button
          v-for="item in steps"
          :key="item.id"
          class="step-row"
          :class="{ active: activeStep.id === item.id }"
          @mouseenter="activeStep = item"
          @focus="activeStep = item"
        >
          <span class="num">{{ item.id }}</span>
          <div>
            <strong>{{ item.title }}</strong>
            <p>{{ item.short }}</p>
          </div>
        </button>

        <div class="feedback-box">
          <p class="mini-label">Interactive feedback</p>
          <h3>{{ activeStep.title }}</h3>
          <p>{{ activeStep.detail }}</p>
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
    title: 'Align visual and mask information',
    short: 'Image tokens interact with mask tokens.',
    detail:
      'The modulation module lets image features absorb localized mask information, making visual prompts more defect-aware.',
  },
  {
    id: '02',
    title: 'Align visual and textual tokens',
    short: 'Cross-attention shares multimodal knowledge.',
    detail:
      'Visual features and text tokens are aligned so image evidence and semantic information can support each other.',
  },
  {
    id: '03',
    title: 'Control query relevance with a',
    short: 'a measures the relation between instruction and query.',
    detail:
      'The scaling factor a controls how strongly visual information should affect the answer, reducing image-dominated responses.',
  },
]

const activeStep = ref(steps[0])
</script>

<style scoped>
.qa-page {
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
.section-label,
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

.content {
  margin-top: 32px;
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 48px;
  align-items: start;
}

.section-label {
  margin: 0 0 10px;
  font-size: 10px;
}

.left h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 30px;
  line-height: 1.06;
  font-weight: 400;
  max-width: 500px;
}

.formula-box {
  margin-top: 16px;
  padding: 11px 15px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0 18px 18px 0;
}

.mini-label {
  margin: 0 0 6px;
  font-size: 9px;
}

.formula {
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 17px;
  line-height: 1.25;
  white-space: nowrap;
}

.formula.small {
  margin-top: 5px;
  font-size: 15.5px;
}

.body-text {
  margin: 15px 0 0;
  color: #667983;
  font-size: 11.6px;
  line-height: 1.38;
  max-width: 500px;
}

.chips {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
  margin-top: 16px;
}

.chips span {
  padding: 7px 13px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.62);
  border: 1px solid rgba(120, 145, 154, 0.20);
  color: #314f5a;
  font-size: 11.5px;
}

.right {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.step-row {
  width: 100%;
  display: grid;
  grid-template-columns: 42px 1fr;
  gap: 14px;
  align-items: start;
  padding: 9px 0 10px;
  background: transparent;
  border: none;
  border-bottom: 1px solid rgba(120, 145, 154, 0.20);
  text-align: left;
  cursor: pointer;
}

.num {
  width: 33px;
  height: 33px;
  border-radius: 12px;
  display: grid;
  place-items: center;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.step-row.active .num {
  background: #dce8eb;
  color: #314f5a;
}

.step-row strong {
  display: block;
  color: #1f2933;
  font-size: 13.5px;
  line-height: 1.22;
  font-weight: 600;
}

.step-row p {
  margin: 3px 0 0;
  color: #6e8089;
  font-size: 11.3px;
  line-height: 1.3;
}

.feedback-box {
  margin-top: 7px;
  padding: 11px 15px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0 18px 18px 0;
}

.feedback-box h3 {
  margin: 0 0 5px;
  color: #1f2933;
  font-size: 13.5px;
  line-height: 1.25;
  font-weight: 600;
}

.feedback-box p:last-child {
  margin: 0;
  color: #667983;
  font-size: 11.3px;
  line-height: 1.32;
}
</style>