<template>
  <main class="goal-page">
    <section class="header">
      <p class="eyebrow">Abstract</p>
      <h1>What FabGPT Tries to Solve</h1>
      <p class="subtitle">
        FabGPT moves wafer defect analysis from visual detection to knowledge-based understanding.
      </p>
    </section>

    <section class="main">
      <section class="statement">
        <p class="label">Core Goal</p>
        <h2>
          From defect images<br />
          to expert-style answers
        </h2>
        <p>
          FabGPT takes SEM wafer images and user questions, then produces detection,
          localization, analysis, and defect-related answers.
        </p>
      </section>

      <section class="pipeline">
        <div class="step">
          <span>01</span>
          <strong>Detect</strong>
          <p>Find defect regions.</p>
        </div>

        <div class="line"></div>

        <div class="step">
          <span>02</span>
          <strong>Analyze</strong>
          <p>Link visual patterns to defect knowledge.</p>
        </div>

        <div class="line"></div>

        <div class="step">
          <span>03</span>
          <strong>Answer</strong>
          <p>Respond with domain reasoning.</p>
        </div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.goal-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 30px 68px 34px;
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
  max-width: 900px;
  color: #8a9ca3;
  font-size: 14px;
  line-height: 1.35;
}

.main {
  margin-top: 42px;
  display: grid;
  grid-template-columns: 0.92fr 1.08fr;
  gap: 54px;
  align-items: center;
}

.statement {
  transition: transform 180ms ease;
}

.statement:hover {
  transform: translateY(-5px);
}

.label {
  margin: 0 0 16px;
}

.statement h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 35px;
  line-height: 1.08;
  font-weight: 400;
}

.statement p:not(.label) {
  margin: 20px 0 0;
  color: #6b7d86;
  font-size: 14px;
  line-height: 1.42;
}

.pipeline {
  display: grid;
  grid-template-columns: 1fr 42px 1fr 42px 1fr;
  align-items: center;
}

.step {
  min-height: 176px;
  box-sizing: border-box;
  padding: 20px;
  border-radius: 26px;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid rgba(120, 145, 154, 0.24);
  transition:
    transform 180ms ease,
    background 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.step:hover {
  transform: translateY(-7px);
  background: rgba(255, 255, 255, 0.96);
  border-color: rgba(95, 127, 137, 0.55);
  box-shadow: 0 20px 46px rgba(31, 41, 51, 0.10);
}

.step span {
  width: 31px;
  height: 31px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 11px;
}

.step strong {
  display: block;
  margin-top: 20px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 27px;
  font-weight: 400;
}

.step p {
  margin: 11px 0 0;
  color: #6b7d86;
  font-size: 12.4px;
  line-height: 1.34;
}

.line {
  height: 2px;
  background: linear-gradient(
    90deg,
    rgba(95, 127, 137, 0.15),
    rgba(95, 127, 137, 0.42),
    rgba(95, 127, 137, 0.15)
  );
}
</style>