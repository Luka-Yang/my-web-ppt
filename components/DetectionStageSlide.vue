<template>
  <main class="detect-page">
    <section class="header">
      <p class="eyebrow">Proposed Method · 3.3</p>
      <h1>Detection Stage</h1>
      <p class="subtitle">
        The detection head learns pixel-level masks without manually setting segmentation thresholds.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">Core Purpose</p>
        <h2>Learn defect masks automatically.</h2>

        <p>
          Instead of manually tuning thresholds, the detection head learns pixel-level decisions from multimodal tokens.
        </p>

        <div class="keywords">
          <span>Pixel-level mask</span>
          <span>No manual threshold</span>
          <span>Complex background</span>
        </div>
      </section>

      <section class="right">
        <p class="label">Detection Flow</p>

        <div class="step">
          <span>01</span>
          <div>
            <strong>Fuse multimodal tokens</strong>
            <p>T<sub>img</sub> and T<sub>txt</sub> are combined by matrix multiplication.</p>
          </div>
        </div>

        <div class="step">
          <span>02</span>
          <div>
            <strong>Recover spatial details</strong>
            <p>A trainable decoder performs four up-sampling operations.</p>
          </div>
        </div>

        <div class="step">
          <span>03</span>
          <div>
            <strong>Generate mask</strong>
            <p>Softmax normalizes the output into a pixel-level defect mask.</p>
          </div>
        </div>

        <div class="formula">
          <strong>Mask</strong>
          <span>= Softmax((T<sub>img</sub> ⊗ T<sub>txt</sub>) ↑<sup>4</sup><sub>s</sub>)</span>
        </div>
      </section>
    </section>
  </main>
</template>

<script setup>
</script>

<style scoped>
.detect-page {
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
  margin-top: 44px;
  display: grid;
  grid-template-columns: 0.86fr 1.14fr;
  gap: 68px;
  align-items: start;
}

.label {
  margin: 0 0 13px;
}

.left h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 39px;
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
  margin-top: 30px;
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

.step {
  display: grid;
  grid-template-columns: 36px 1fr;
  gap: 15px;
  align-items: start;
  padding: 12px 4px 13px 0;
  border-bottom: 1px solid rgba(120, 145, 154, 0.22);
  transition: 160ms ease;
}

.step:hover,
.keywords span:hover,
.formula:hover {
  transform: translateX(8px);
}

.step span {
  width: 30px;
  height: 30px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.step strong {
  color: #1f2933;
  font-size: 15px;
  font-weight: 500;
}

.step p {
  margin: 4px 0 0;
  color: #6b7d86;
  font-size: 12px;
  line-height: 1.28;
}

.formula {
  margin-top: 10px;
  padding: 13px 16px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  background: rgba(255, 255, 255, 0.52);
  border-radius: 0 18px 18px 0;
  color: #314f5a;
  transition: 160ms ease;
}

.formula strong {
  color: #1f2933;
  font-size: 14px;
  margin-right: 10px;
}

.formula span {
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 20px;
}
</style>