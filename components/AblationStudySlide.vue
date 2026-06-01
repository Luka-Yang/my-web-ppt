<template>
  <main class="ablation-page">
    <section class="header">
      <p class="eyebrow">Experiments · 4.4</p>
      <h1>Ablation Studies</h1>
      <p class="subtitle">
        Ablation results validate the PM operation and visual prompt instruction design
      </p>
    </section>

    <section class="tables">
      <section class="table-block">
        <p class="label">PM Operation Design</p>

        <table>
          <thead>
            <tr>
              <th>Feature Mapping</th>
              <th>Similarity Strategy</th>
              <th>Image-AUC</th>
              <th>Pixel-AUC</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="row in pmRows"
              :key="row.id"
              :class="{ best: row.best, active: activeItem.id === row.id }"
              @mouseenter="activeItem = row"
            >
              <td>{{ row.mapping }}</td>
              <td>{{ row.strategy }}</td>
              <td>{{ row.image }}</td>
              <td>{{ row.pixel }}</td>
            </tr>
          </tbody>
        </table>
      </section>

      <section class="table-block">
        <p class="label">Prompt Embedding Scheme</p>

        <table>
          <thead>
            <tr>
              <th>Visual Instruction</th>
              <th>Defect-Related</th>
              <th>Unrelated</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="row in promptRows"
              :key="row.id"
              :class="{ best: row.best, active: activeItem.id === row.id }"
              @mouseenter="activeItem = row"
            >
              <td>{{ row.instruction }}</td>
              <td>{{ row.defect }}</td>
              <td>{{ row.unrelated }}</td>
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

const pmRows = [
  {
    id: 'pm-1',
    mapping: '–',
    strategy: 'BiLinear Similarity',
    image: '85.77',
    pixel: '89.33',
    title: 'BiLinear Similarity',
    detail:
      'BiLinear similarity provides the weakest PM result, showing that the category-matching operation is not sufficient for this task',
  },
  {
    id: 'pm-2',
    mapping: '–',
    strategy: 'Matrix Multiplication',
    image: '88.25',
    pixel: '92.59',
    title: 'Matrix Multiplication',
    detail:
      'Matrix multiplication improves the result, but it is still weaker than cosine similarity for comparing image and label features',
  },
  {
    id: 'pm-3',
    mapping: '–',
    strategy: 'Cosine Similarity',
    image: '91.03',
    pixel: '94.61',
    title: 'Cosine Similarity',
    detail:
      'Cosine similarity gives better category matching because it measures feature direction rather than only raw magnitude',
  },
  {
    id: 'pm-4',
    mapping: 'Linear + ReLU',
    strategy: 'Cosine Similarity',
    image: '91.81',
    pixel: '95.61',
    best: true,
    title: 'Linear + ReLU + Cosine Similarity',
    detail:
      'Adding Linear and ReLU before cosine similarity gives the best PM result, meaning feature reshaping improves defect-category prediction',
  },
]

const promptRows = [
  {
    id: 'p-1',
    instruction: 'Timg',
    defect: '82.50',
    unrelated: '10.00',
    title: 'Only image token',
    detail:
      'Using only Timg gives limited defect-related Q&A performance and almost fails on unrelated questions',
  },
  {
    id: 'p-2',
    instruction: 'Timg + Ttxt',
    defect: '85.00',
    unrelated: '10.00',
    title: 'Image token + text token',
    detail:
      'Adding Ttxt slightly improves defect-related questions, but unrelated-question accuracy remains very low',
  },
  {
    id: 'p-3',
    instruction: 'Timg + Ttxt + Tmas',
    defect: '95.00',
    unrelated: '10.00',
    title: 'Image, text, and mask tokens',
    detail:
      'Adding the mask token strongly improves defect-related Q&A, but the model is still dominated by visual information',
  },
  {
    id: 'p-4',
    instruction: 'Tvis + Tmas',
    defect: '96.67',
    unrelated: '12.00',
    title: 'Unified visual token + mask token',
    detail:
      'Tvis improves defect-related answering, but without the scaling factor, the model still struggles with unrelated questions',
  },
  {
    id: 'p-5',
    instruction: 'aTvis + Tmas',
    defect: '96.67',
    unrelated: '98.00',
    best: true,
    title: 'Scaled visual token + mask token',
    detail:
      'The scaling factor a keeps high defect-related accuracy while recovering unrelated-question accuracy, showing reduced modality bias',
  },
]

const activeItem = ref(pmRows[3])
</script>

<style scoped>
.ablation-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 20px 54px 16px;
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

.tables {
  margin-top: 26px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 22px;
}

.table-block {
  padding: 16px 18px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.56);
  border: 1px solid rgba(120, 145, 154, 0.20);
  box-shadow: 0 12px 24px rgba(31, 41, 51, 0.04);
}

.label {
  margin: 0 0 12px;
}

table {
  width: 100%;
  border-collapse: collapse;
  table-layout: fixed;
}

th {
  padding: 8px 6px;
  color: #314f5a;
  font-size: 11px;
  font-weight: 600;
  text-align: center;
  border-bottom: 1px solid rgba(95, 127, 137, 0.36);
}

td {
  padding: 8px 6px;
  color: #667983;
  font-size: 11px;
  line-height: 1.18;
  text-align: center;
  border-bottom: 1px solid rgba(120, 145, 154, 0.16);
}

td:first-child,
th:first-child {
  text-align: left;
}

tbody tr {
  cursor: pointer;
  transition: 150ms ease;
}

tbody tr:hover,
tbody tr.active {
  background: rgba(255, 255, 255, 0.72);
}

.best td {
  color: #1f2933;
  font-weight: 700;
}

.best td:nth-last-child(-n + 2) {
  color: #d62728;
}

.feedback {
  position: absolute;
  left: 54px;
  right: 54px;
  bottom: 16px;
  padding: 11px 15px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  border-radius: 0 17px 17px 0;
  background: rgba(255, 255, 255, 0.78);
  box-shadow: 0 10px 22px rgba(31, 41, 51, 0.04);
}

.feedback .label {
  margin: 0 0 4px;
}

.feedback strong {
  display: block;
  color: #1f2933;
  font-size: 12.8px;
  font-weight: 600;
}

.feedback span {
  display: block;
  margin-top: 4px;
  color: #667983;
  font-size: 11px;
  line-height: 1.28;
}
</style>