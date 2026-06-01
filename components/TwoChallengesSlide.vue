<template>
  <main class="challenge-page">
    <section class="header">
      <p class="eyebrow">Introduction</p>
      <h1>Two Key Challenges</h1>
      <p class="subtitle">
        FabGPT is motivated by two difficulties in wafer defect understanding:
        complex SEM backgrounds and modality bias.
      </p>
    </section>

    <section class="main">
      <section class="challenge-block">
        <p class="label">Challenge 01 · Visual Evidence</p>
        <h2>Complex SEM Backgrounds</h2>

        <div class="visual-strip">
          <span class="dot d1"></span>
          <span class="dot d2"></span>
          <span class="dot d3"></span>
          <div class="scan-line"></div>
        </div>

        <p>
          Defects can be minute, subtle, and embedded in noisy microscopic textures,
          making reliable localization difficult.
        </p>

        <div class="tags">
          <span>Minute defects</span>
          <span>Noisy texture</span>
        </div>
      </section>

      <section class="bridge">
        <p class="label">Design Need</p>
        <h3>Defect-aware<br />grounding</h3>
        <div class="plus">+</div>
        <h3>Image-based<br />reasoning</h3>
      </section>

      <section class="challenge-block">
        <p class="label">Challenge 02 · Model Reasoning</p>
        <h2>Modality Bias</h2>

        <div class="bias-visual">
          <div>
            <span>Image input</span>
            <div class="bar strong"></div>
          </div>
          <div>
            <span>User query</span>
            <div class="bar weak"></div>
          </div>
        </div>

        <p>
          After fine-tuning, the model may rely too much on image inputs and
          ignore user queries, weakening normal Q&amp;A ability.
        </p>

        <div class="tags">
          <span>Image over-focus</span>
          <span>Query neglect</span>
        </div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.challenge-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 28px 68px 30px;
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
  margin: 0 0 8px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 40px;
  line-height: 1.08;
  font-weight: 400;
}

.subtitle {
  margin: 9px 0 0;
  max-width: 1050px;
  color: #8a9ca3;
  font-size: 14px;
  line-height: 1.35;
}

.main {
  margin-top: 30px;
  display: grid;
  grid-template-columns: 1fr 210px 1fr;
  gap: 34px;
  align-items: start;
}

.challenge-block {
  min-height: 255px;
  transition: transform 180ms ease, filter 180ms ease;
}

.challenge-block:hover,
.bridge:hover {
  transform: translateY(-5px);
  filter: drop-shadow(0 16px 24px rgba(31, 41, 51, 0.09));
}

.label {
  margin: 0 0 13px;
}

.challenge-block h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 32px;
  line-height: 1.05;
  font-weight: 400;
}

.challenge-block p:not(.label) {
  margin: 14px 0 0;
  max-width: 430px;
  color: #6b7d86;
  font-size: 13px;
  line-height: 1.38;
}

.visual-strip,
.bias-visual {
  margin-top: 20px;
  height: 72px;
  border-radius: 22px;
  background:
    linear-gradient(135deg, rgba(255,255,255,0.72), rgba(231,238,240,0.42)),
    repeating-linear-gradient(45deg, rgba(95,127,137,0.055) 0, rgba(95,127,137,0.055) 2px, transparent 2px, transparent 12px);
  border: 1px solid rgba(120, 145, 154, 0.22);
  position: relative;
  overflow: hidden;
}

.visual-strip::before {
  content: "";
  position: absolute;
  inset: 18px 34px;
  border-radius: 999px;
  border: 1px solid rgba(120, 145, 154, 0.22);
  background: rgba(255, 255, 255, 0.28);
}

.scan-line {
  position: absolute;
  left: 0;
  top: 48%;
  width: 100%;
  height: 1px;
  background: rgba(95, 127, 137, 0.24);
}

.dot {
  position: absolute;
  z-index: 2;
  border-radius: 50%;
  background: #5f7f89;
  box-shadow: 0 0 0 8px rgba(95, 127, 137, 0.12);
  animation: pulse 2.5s ease-in-out infinite;
}

.d1 { width: 11px; height: 11px; left: 74px; top: 25px; }
.d2 { width: 8px; height: 8px; left: 170px; top: 44px; animation-delay: 0.5s; }
.d3 { width: 10px; height: 10px; right: 80px; top: 28px; animation-delay: 0.9s; }

@keyframes pulse {
  0%, 100% { opacity: 0.48; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.16); }
}

.tags {
  margin-top: 14px;
  display: flex;
  flex-wrap: nowrap;
  gap: 8px;
}

.tags span {
  padding: 7px 11px;
  border-radius: 999px;
  background: rgba(255,255,255,0.76);
  border: 1px solid rgba(120,145,154,0.22);
  color: #314f5a;
  font-size: 11px;
}

.bridge {
  min-height: 215px;
  padding: 20px 12px;
  box-sizing: border-box;
  text-align: center;
  display: grid;
  align-content: center;
  border-left: 1px solid rgba(120, 145, 154, 0.28);
  border-right: 1px solid rgba(120, 145, 154, 0.28);
  transition: transform 180ms ease, filter 180ms ease;
}

.bridge h3 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 24px;
  line-height: 1.1;
  font-weight: 400;
}

.plus {
  margin: 8px 0;
  color: #5f7f89;
  font-size: 22px;
}

.bias-visual {
  padding: 15px 18px;
  box-sizing: border-box;
  display: grid;
  gap: 10px;
}

.bias-visual span {
  display: block;
  margin-bottom: 5px;
  color: #5f7f89;
  font-size: 9px;
  letter-spacing: 0.13em;
  text-transform: uppercase;
}

.bar {
  height: 8px;
  border-radius: 999px;
  background: rgba(120, 145, 154, 0.18);
  overflow: hidden;
}

.bar::before {
  content: "";
  display: block;
  height: 100%;
  border-radius: inherit;
  background: rgba(95, 127, 137, 0.48);
}

.strong::before { width: 82%; }
.weak::before { width: 32%; }
</style>