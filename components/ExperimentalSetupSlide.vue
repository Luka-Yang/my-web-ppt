<template>
  <main class="exp-page">
    <section class="header">
      <p class="eyebrow">Experiments · 4.1</p>
      <h1>Experimental Setups</h1>
      <p class="subtitle">
        Evaluation setting for SEM wafer defect detection and Q&amp;A capability
      </p>
    </section>

    <section class="summary">
      <div
        v-for="item in summaryItems"
        :key="item.id"
        class="summary-card"
        @mouseenter="activeItem = item"
      >
        <p class="label">{{ item.group }}</p>
        <h2>{{ item.title }}</h2>
        <span>{{ item.short }}</span>
      </div>
    </section>

    <section class="details">
      <section class="info-block">
        <p class="label">Training Details</p>

        <div class="grid-table">
          <div
            v-for="item in trainingItems"
            :key="item.id"
            @mouseenter="activeItem = item"
          >
            <strong>{{ item.title }}</strong>
            <span>{{ item.short }}</span>
          </div>
        </div>
      </section>

      <section class="info-block">
        <p class="label">Evaluation Design</p>

        <div class="grid-table">
          <div
            v-for="item in evaluationItems"
            :key="item.id"
            @mouseenter="activeItem = item"
          >
            <strong>{{ item.title }}</strong>
            <span>{{ item.short }}</span>
          </div>
        </div>
      </section>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const summaryItems = [
  {
    id: 'dataset',
    group: 'Dataset',
    title: 'SEM-WaD',
    short: '480 × 480 · Train/Test = 7:3',
    detail:
      'The in-house SEM-WaD dataset is used to evaluate both wafer defect detection and Q&A capability',
  },
  {
    id: 'implementation',
    group: 'Implementation',
    title: 'PandaGPT',
    short: 'Vicuna-7B + ImageBind Huge',
    detail:
      'FabGPT uses PandaGPT as the foundation, with Vicuna-7B as the language model and ImageBind Huge as the frozen encoder',
  },
  {
    id: 'evaluation',
    group: 'Evaluation',
    title: 'Detection + Q&A',
    short: 'AUC / PRO / AP + answer accuracy',
    detail:
      'The evaluation covers both defect localization performance and answer correctness in Q&A tasks',
  },
]

const trainingItems = [
  {
    id: 'encoder',
    title: 'Encoder',
    short: 'ImageBind Huge, frozen',
    detail:
      'The encoder is frozen, so adaptation mainly depends on the proposed modules and fine-tuning strategy',
  },
  {
    id: 'optimizer',
    title: 'Optimizer',
    short: 'AdamW',
    detail:
      'AdamW is used to optimize trainable parameters during model training',
  },
  {
    id: 'learning-rate',
    title: 'Learning rate',
    short: '1e-4 → 1e-6, cosine annealing',
    detail:
      'The learning rate gradually decreases from 1e-4 to 1e-6 using cosine annealing',
  },
  {
    id: 'training',
    title: 'Training',
    short: '3 × 4090Ti, batch 24, 50 epochs',
    detail:
      'The model is trained on three 4090Ti GPUs with batch size 24 for 50 epochs',
  },
  {
    id: 'annotation',
    title: 'Annotation',
    short: 'Mask, text description, analysis',
    detail:
      'Each image is paired with mask annotations, textual descriptions, and defect analysis',
  },
  {
    id: 'samples',
    title: 'Samples',
    short: 'Good and defective images',
    detail:
      'Both good and defective wafer images are included in the training and test sets',
  },
]

const evaluationItems = [
  {
    id: 'detection-metrics',
    title: 'Detection metrics',
    short: 'Image-AUC, Pixel-AUC, PRO, AP',
    detail:
      'Image-AUC and Pixel-AUC evaluate defect judgment, while PRO and AP measure localization quality',
  },
  {
    id: 'qa-questions',
    title: 'Q&A questions',
    short: '15 per defect type + 50 general questions',
    detail:
      'The Q&A set includes defect-related questions and general questions for testing modality bias',
  },
  {
    id: 'qa-metric',
    title: 'Q&A metric',
    short: 'Percentage of correct answers',
    detail:
      'Q&A performance is measured by the percentage of correctly answered questions',
  },
  {
    id: 'baselines',
    title: 'Baselines',
    short: 'DevNet, DRA, BGAD, PRN, Lisa, AnomalyGPT',
    detail:
      'FabGPT is compared with both traditional anomaly detection methods and LMM-based baselines',
  },
]

const activeItem = ref(summaryItems[0])
</script>

<style scoped>
.exp-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 20px 54px 18px;
  overflow: hidden;
  position: relative;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.10), transparent 30%),
    radial-gradient(circle at 18% 88%, rgba(95, 127, 137, 0.07), transparent 34%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow,
.label {
  color: #5f7f89;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  font-weight: 500;
  font-size: 9.5px;
}

.eyebrow {
  margin: 0 0 5px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 32px;
  line-height: 1.03;
  font-weight: 400;
}

.subtitle {
  margin: 6px 0 0;
  color: #8fa1a8;
  font-size: 11.5px;
}

.summary {
  margin-top: 34px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 22px;
}

.summary-card {
  padding: 18px 22px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.56);
  border: 1px solid rgba(120, 145, 154, 0.20);
  box-shadow: 0 12px 24px rgba(31, 41, 51, 0.04);
  cursor: pointer;
  transition: 160ms ease;
}

.summary-card:hover {
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.86);
  border-color: rgba(95, 127, 137, 0.42);
}

.label {
  margin: 0 0 10px;
}

.summary-card h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 27px;
  line-height: 1.05;
  font-weight: 400;
}

.summary-card span {
  display: block;
  margin-top: 12px;
  color: #667983;
  font-size: 12px;
  line-height: 1.3;
}

.details {
  margin-top: 24px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 22px;
}

.info-block {
  padding: 18px 22px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.52);
  border: 1px solid rgba(120, 145, 154, 0.20);
  box-shadow: 0 12px 24px rgba(31, 41, 51, 0.035);
}

.grid-table {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0 22px;
}

.grid-table div {
  min-height: 48px;
  padding: 9px 0;
  border-bottom: 1px solid rgba(120, 145, 154, 0.18);
  cursor: pointer;
  transition: 160ms ease;
}

.grid-table div:hover {
  background: rgba(255, 255, 255, 0.42);
  border-radius: 10px;
  padding-left: 8px;
}

.grid-table div:hover strong {
  color: #314f5a;
}

.grid-table strong {
  display: block;
  color: #1f2933;
  font-size: 11.8px;
  font-weight: 600;
  line-height: 1.25;
}

.grid-table span {
  display: block;
  margin-top: 4px;
  color: #667983;
  font-size: 11.2px;
  line-height: 1.28;
}

.feedback {
  position: absolute;
  left: 54px;
  right: 54px;
  bottom: 14px;
  padding: 10px 14px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  border-radius: 0 16px 16px 0;
  background: rgba(255, 255, 255, 0.78);
  box-shadow: 0 10px 22px rgba(31, 41, 51, 0.04);
}

.feedback .label {
  margin: 0 0 4px;
}

.feedback strong {
  display: block;
  color: #1f2933;
  font-size: 12.5px;
  font-weight: 600;
}

.feedback span {
  display: block;
  margin-top: 3px;
  color: #667983;
  font-size: 10.8px;
  line-height: 1.25;
}
</style>