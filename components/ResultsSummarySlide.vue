<template>
  <main class="results-page">
    <section class="header">
      <p class="eyebrow">Experiments · 4.2–4.3</p>
      <h1>Quantitative Results</h1>
      <p class="subtitle">
        FabGPT achieves strong defect detection and Q&amp;A performance on SEM-WaD
      </p>
    </section>

    <section class="tables">
      <section class="table-block">
        <p class="label">Detection average results</p>

        <table>
          <thead>
            <tr>
              <th>Method</th>
              <th>Image-AUC</th>
              <th>Pixel-AUC</th>
              <th>PRO</th>
              <th>AP</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="row in detectionRows"
              :key="row.method"
              :class="{ ours: row.method.includes('FabGPT') }"
              @mouseenter="activeItem = row"
            >
              <td>{{ row.method }}</td>
              <td :class="row.imageClass">{{ row.image }}</td>
              <td :class="row.pixelClass">{{ row.pixel }}</td>
              <td :class="row.proClass">{{ row.pro }}</td>
              <td :class="row.apClass">{{ row.ap }}</td>
            </tr>
          </tbody>
        </table>
      </section>

      <section class="table-block">
        <p class="label">Q&amp;A accuracy results</p>

        <table>
          <thead>
            <tr>
              <th>Question</th>
              <th>Lisa</th>
              <th>AnomalyGPT</th>
              <th>GPT-4</th>
              <th>FabGPT</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="row in qaRows"
              :key="row.question"
              :class="{ ours: row.question === 'All' }"
              @mouseenter="activeItem = row"
            >
              <td>{{ row.question }}</td>
              <td :class="row.lisaClass">{{ row.lisa }}</td>
              <td :class="row.anomalyClass">{{ row.anomaly }}</td>
              <td :class="row.gptClass">{{ row.gpt }}</td>
              <td :class="row.fabClass">{{ row.fab }}</td>
            </tr>
          </tbody>
        </table>
      </section>
    </section>

    <section class="feedback">
      <p class="label">Interactive Feedback</p>
      <strong>{{ activeItem.title }}</strong>
      <span>{{ activeItem.detail }}</span>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const detectionRows = [
  {
    method: 'DevNet',
    image: '52.74',
    pixel: '72.98',
    pro: '–',
    ap: '77.80',
    apClass: 'second',
    title: 'DevNet',
    detail: 'DevNet is a traditional anomaly detection baseline, but its average image-level result is much lower than FabGPT',
  },
  {
    method: 'DRA',
    image: '88.14',
    pixel: '87.15',
    pro: '52.76',
    ap: '–',
    title: 'DRA',
    detail: 'DRA performs reasonably on Image-AUC, but its localization quality is weaker than FabGPT',
  },
  {
    method: 'BGAD',
    image: '63.82',
    pixel: '87.68',
    pro: '81.70',
    ap: '52.66',
    title: 'BGAD',
    detail: 'BGAD has moderate localization performance but is still behind FabGPT in all reported average metrics',
  },
  {
    method: 'PRN',
    image: '78.12',
    pixel: '81.36',
    pro: '78.05',
    ap: '70.89',
    title: 'PRN',
    detail: 'Compared with PRN, FabGPT improves PRO and AP clearly, showing better region-level localization',
  },
  {
    method: 'Lisa',
    image: '87.67',
    pixel: '87.26',
    pro: '76.94',
    ap: '64.20',
    title: 'Lisa',
    detail: 'Lisa is an LMM-based baseline, but its detection metrics remain lower than FabGPT',
  },
  {
    method: 'AnomalyGPT',
    image: '89.96',
    pixel: '92.58',
    pro: '85.20',
    ap: '77.64',
    imageClass: 'second',
    pixelClass: 'second',
    proClass: 'second',
    title: 'AnomalyGPT',
    detail: 'AnomalyGPT is the strongest baseline, but FabGPT still improves Image-AUC, Pixel-AUC, PRO, and AP',
  },
  {
    method: 'FabGPT',
    image: '91.81',
    pixel: '95.61',
    pro: '88.17',
    ap: '85.80',
    imageClass: 'best',
    pixelClass: 'best',
    proClass: 'best',
    apClass: 'best',
    title: 'FabGPT detection result',
    detail: 'FabGPT achieves the best average result across Image-AUC, Pixel-AUC, PRO, and AP',
  },
]

const qaRows = [
  {
    question: 'Presence',
    lisa: '95.00',
    anomaly: '95.00',
    gpt: '100.00',
    fab: '100.00',
    gptClass: 'best',
    fabClass: 'best',
    title: 'Presence question',
    detail: 'FabGPT correctly answers whether a defect exists in the image',
  },
  {
    question: 'Category',
    lisa: '92.50',
    anomaly: '75.00',
    gpt: '37.50',
    fab: '97.50',
    lisaClass: 'second',
    fabClass: 'best',
    title: 'Category question',
    detail: 'FabGPT shows the strongest defect category recognition among compared models',
  },
  {
    question: 'Location',
    lisa: '–',
    anomaly: '72.50',
    gpt: '87.50',
    fab: '95.00',
    gptClass: 'second',
    fabClass: 'best',
    title: 'Location question',
    detail: 'FabGPT can answer where the defect appears, supported by its mask-aware design',
  },
  {
    question: 'Quantity',
    lisa: '–',
    anomaly: '77.50',
    gpt: '80.00',
    fab: '95.00',
    gptClass: 'second',
    fabClass: 'best',
    title: 'Quantity question',
    detail: 'FabGPT performs best when estimating the number of defects in the image',
  },
  {
    question: 'Description',
    lisa: '72.50',
    anomaly: '82.50',
    gpt: '85.00',
    fab: '95.00',
    gptClass: 'second',
    fabClass: 'best',
    title: 'Description question',
    detail: 'FabGPT gives stronger visual descriptions of defect appearance',
  },
  {
    question: 'Analysis',
    lisa: '–',
    anomaly: '–',
    gpt: '90.00',
    fab: '97.50',
    gptClass: 'second',
    fabClass: 'best',
    title: 'Analysis question',
    detail: 'FabGPT improves defect analysis accuracy, which is important for process interpretation',
  },
  {
    question: 'Unrelated',
    lisa: '20.00',
    anomaly: '12.00',
    gpt: '98.00',
    fab: '98.00',
    gptClass: 'best',
    fabClass: 'best',
    title: 'Unrelated question',
    detail: 'FabGPT keeps general answering ability, showing reduced modality bias after fine-tuning',
  },
  {
    question: 'All',
    lisa: '70.00',
    anomaly: '69.08',
    gpt: '82.57',
    fab: '96.86',
    gptClass: 'second',
    fabClass: 'best',
    title: 'Overall Q&A result',
    detail: 'FabGPT achieves the best overall Q&A accuracy across defect-related and general questions',
  },
]

const activeItem = ref(detectionRows[6])
</script>

<style scoped>
.results-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 18px 52px 14px;
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
  font-size: 9.4px;
}

.eyebrow {
  margin: 0 0 5px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 31px;
  line-height: 1.03;
  font-weight: 400;
}

.subtitle {
  margin: 6px 0 0;
  color: #8fa1a8;
  font-size: 11.3px;
}

.tables {
  margin-top: 18px;
  display: grid;
  grid-template-columns: 1.04fr 0.96fr;
  gap: 18px;
}

.table-block {
  padding: 13px 15px 12px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.54);
  border: 1px solid rgba(120, 145, 154, 0.20);
  box-shadow: 0 10px 22px rgba(31, 41, 51, 0.035);
}

.label {
  margin: 0 0 8px;
}

table {
  width: 100%;
  border-collapse: collapse;
  table-layout: fixed;
}

th {
  padding: 6px 5px;
  color: #314f5a;
  font-size: 10.4px;
  font-weight: 600;
  text-align: center;
  border-bottom: 1px solid rgba(95, 127, 137, 0.35);
}

td {
  padding: 5px 5px;
  color: #667983;
  font-size: 10.2px;
  line-height: 1.16;
  text-align: center;
  border-bottom: 1px solid rgba(120, 145, 154, 0.16);
}

td:first-child,
th:first-child {
  text-align: left;
}

tbody tr {
  cursor: pointer;
  transition: 140ms ease;
}

tbody tr:hover {
  background: rgba(255, 255, 255, 0.62);
}

.ours td {
  font-weight: 700;
  color: #1f2933;
}

.best {
  color: #d62728 !important;
  font-weight: 700;
}

.second {
  color: #1f4fbf !important;
  font-weight: 700;
}

.feedback {
  position: absolute;
  left: 52px;
  right: 52px;
  bottom: 14px;
  padding: 9px 13px;
  border-left: 4px solid rgba(95, 127, 137, 0.40);
  border-radius: 0 16px 16px 0;
  background: rgba(255, 255, 255, 0.76);
  box-shadow: 0 10px 22px rgba(31, 41, 51, 0.04);
}

.feedback .label {
  margin: 0 0 3px;
}

.feedback strong {
  display: block;
  color: #1f2933;
  font-size: 12.4px;
  font-weight: 600;
}

.feedback span {
  display: block;
  margin-top: 3px;
  color: #667983;
  font-size: 10.7px;
  line-height: 1.24;
}
</style>