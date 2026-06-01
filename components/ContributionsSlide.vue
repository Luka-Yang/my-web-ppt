<template>
  <main class="contrib-page">
    <section class="header">
      <p class="eyebrow">Introduction</p>
      <h1>Main Contributions of FabGPT</h1>
      <p class="subtitle">
        FabGPT proposes an efficient knowledge-query LMM with modal enhancement, detection, and Q&amp;A stages.
      </p>
    </section>

    <section class="stage-flow">
      <p class="flow-label">Three-stage strategy</p>

      <div class="flow-row">
        <div class="stage"><span>01</span><strong>Modal Enhancement</strong></div>
        <div class="arrow">→</div>
        <div class="stage"><span>02</span><strong>Detection</strong></div>
        <div class="arrow">→</div>
        <div class="stage"><span>03</span><strong>Q&amp;A Stage</strong></div>
      </div>
    </section>

    <section class="main">
      <section class="summary">
        <p class="label">Contribution Summary</p>

        <div class="row"><span>01</span><p><strong>Prompt-learning-based FabGPT</strong> detects minute wafer defects and supports defect-related Q&amp;A.</p></div>
        <div class="row"><span>02</span><p><strong>Modal enhancement stage</strong> improves semantic information in multimodal prompt features.</p></div>
        <div class="row"><span>03</span><p><strong>Pixel-level detection head</strong> detects wafer defects without subjective threshold selection.</p></div>
        <div class="row"><span>04</span><p><strong>Q&amp;A and corpus training</strong> update instruction coefficients and alleviate modality bias.</p></div>
      </section>

      <section class="validation">
        <p class="label">SEM-WaD Validation</p>
        <div class="metric"><strong>91.81%</strong><span>Image-level accuracy</span></div>
        <div class="metric"><strong>95.61%</strong><span>Pixel-level accuracy</span></div>
        <div class="metric"><strong>96.86%</strong><span>Q&amp;A accuracy</span></div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.contrib-page {
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
.label,
.flow-label {
  color: #5f7f89;
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.17em;
  text-transform: uppercase;
}

.eyebrow { margin: 0 0 7px; }

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 37px;
  line-height: 1.05;
  font-weight: 400;
}

.subtitle {
  margin: 8px 0 0;
  color: #8a9ca3;
  font-size: 13px;
  line-height: 1.3;
}

.stage-flow {
  margin-top: 22px;
}

.flow-label {
  margin: 0 0 9px;
}

.flow-row {
  display: grid;
  grid-template-columns: 1fr 34px 1fr 34px 1fr;
  gap: 9px;
  align-items: center;
}

.stage {
  height: 50px;
  padding: 9px 13px;
  border-radius: 18px;
  display: grid;
  grid-template-columns: 28px 1fr;
  gap: 11px;
  align-items: center;
  background: rgba(255, 255, 255, 0.66);
  border: 1px solid rgba(120, 145, 154, 0.22);
  box-sizing: border-box;
  transition: 160ms ease;
}

.stage:hover,
.row:hover,
.metric:hover {
  transform: translateY(-4px);
  background: rgba(255, 255, 255, 0.94);
  border-color: rgba(95, 127, 137, 0.48);
  box-shadow: 0 14px 30px rgba(31, 41, 51, 0.07);
}

.stage span,
.row span {
  width: 27px;
  height: 27px;
  display: grid;
  place-items: center;
  border-radius: 11px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.stage strong {
  color: #314f5a;
  font-size: 12.7px;
  font-weight: 500;
}

.arrow {
  color: #8a9ca3;
  font-size: 21px;
  text-align: center;
}

.main {
  margin-top: 24px;
  display: grid;
  grid-template-columns: 1.45fr 0.55fr;
  gap: 36px;
  align-items: start;
}

.label {
  margin: 0 0 10px;
}

.row {
  display: grid;
  grid-template-columns: 35px 1fr;
  gap: 12px;
  align-items: start;
  padding: 10px 12px;
  border-bottom: 1px solid rgba(120, 145, 154, 0.20);
  border-radius: 15px;
  transition: 160ms ease;
}

.row p {
  margin: 0;
  color: #6b7d86;
  font-size: 12.4px;
  line-height: 1.3;
}

.row strong {
  color: #1f2933;
  font-weight: 500;
}

.validation {
  padding-top: 0;
}

.metric {
  margin-bottom: 12px;
  padding: 12px 14px;
  border-radius: 18px;
  background: rgba(255,255,255,0.58);
  border: 1px solid rgba(120,145,154,0.20);
  transition: 160ms ease;
}

.metric strong {
  display: block;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 26px;
  line-height: 1;
  font-weight: 400;
}

.metric span {
  display: block;
  margin-top: 5px;
  color: #6b7d86;
  font-size: 11px;
}
</style>