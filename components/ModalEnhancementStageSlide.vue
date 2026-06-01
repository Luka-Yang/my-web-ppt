<template>
  <main class="modal-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · 3.2</p>
      <h1>Modal Enhancement Stage</h1>
      <p class="subtitle">
        This stage enhances semantic and detailed defect features before detection and Q&amp;A.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">Core Purpose</p>
        <h2>Enhance subtle defect cues in complex SEM backgrounds</h2>

        <p>
          The Prediction Module first estimates the defect category, then the visual and textual adapters enrich the feature flow.
        </p>

        <div class="keywords">
          <span>PM</span>
          <span>Visual Adapter</span>
          <span>Textual Adapter</span>
        </div>
      </section>

      <section class="right">
        <p class="label">Key Formulas</p>

        <div class="formula">
          <strong>01 · Feature reshaping</strong>
          <p>f<sub>img</sub> = σ(W<sub>i</sub><sup>T</sup>V<sub>img</sub><sup>clip</sup> + b<sub>i</sub>)</p>
          <p>f<sub>lab</sub> = σ(W<sub>i</sub><sup>T</sup>V<sub>lab</sub><sup>clip</sup> + b<sub>i</sub>)</p>
        </div>

        <div class="formula">
          <strong>02 · Category prediction</strong>
          <p>p<sub>i</sub> = Cosine(f<sub>img</sub>, f<sub>lab</sub>)</p>
          <p>P<sub>n</sub> = max(Softmax(p<sub>i</sub>))</p>
        </div>

        <div class="formula">
          <strong>03 · Adapter output</strong>
          <p>∇f<sub>e</sub> = (V<sub>img</sub><sup>clip</sup>)<sub>i</sub> → z<sub>i</sub></p>
          <p>T<sub>img</sub> = Concat(∇f<sub>e</sub>, V<sub>img</sub>)</p>
        </div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.modal-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 24px 64px;
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
  margin: 0 0 6px;
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
  font-size: 12.6px;
}

.main {
  margin-top: 42px;
  display: grid;
  grid-template-columns: 0.85fr 1.15fr;
  gap: 68px;
  align-items: start;
}

.label {
  margin: 0 0 13px;
}

.left h2 {
  margin: 0;
  max-width: 560px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 30px;
  line-height: 1.06;
  font-weight: 400;
}

.left p {
  margin: 24px 0 0;
  max-width: 540px;
  color: #6b7d86;
  font-size: 13px;
  line-height: 1.38;
}

.keywords {
  margin-top: 28px;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.keywords span {
  padding: 8px 14px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.64);
  border: 1px solid rgba(120, 145, 154, 0.22);
  color: #314f5a;
  font-size: 12px;
}

.right {
  display: grid;
  gap: 13px;
}

.formula {
  padding: 13px 16px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  background: rgba(255, 255, 255, 0.52);
  border-radius: 0 18px 18px 0;
  transition: 160ms ease;
}

.formula:hover,
.keywords span:hover {
  transform: translateX(7px);
  background: rgba(255, 255, 255, 0.86);
  box-shadow: 0 12px 26px rgba(31, 41, 51, 0.06);
}

.formula strong {
  display: block;
  color: #1f2933;
  font-size: 13.5px;
  font-weight: 500;
  margin-bottom: 7px;
}

.formula p {
  margin: 4px 0;
  color: #314f5a;
  font-size: 13.2px;
  line-height: 1.35;
}
</style>