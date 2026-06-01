<template>
  <main class="limit-page">
    <section class="header">
      <p class="eyebrow">Introduction</p>
      <h1>Limitations of Existing Defect Methods</h1>
      <p class="subtitle">
        Existing defect models can support visual inspection, but they are limited in knowledge-level wafer defect analysis.
      </p>
    </section>

    <section class="main">
      <p class="section-label">Three main limitations</p>

      <section class="limit-row">
        <article class="limit-item">
          <span class="number">01</span>
          <h2>Detection-focused output</h2>
          <p>
            Most methods provide class labels, defect locations, or masks, but not expert-style explanations.
          </p>
        </article>

        <article class="limit-item">
          <span class="number">02</span>
          <h2>High annotation demand</h2>
          <p>
            Supervised defect models usually require carefully labeled SEM wafer datasets.
          </p>
        </article>

        <article class="limit-item">
          <span class="number">03</span>
          <h2>Weak knowledge querying</h2>
          <p>
            They usually cannot answer questions about defect meaning, possible cause, or process implication.
          </p>
        </article>
      </section>
    </section>
  </main>
</template>

<style scoped>
.limit-page {
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
  font-family:
    Inter,
    ui-sans-serif,
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    sans-serif;
}

.eyebrow,
.section-label,
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
  max-width: 1000px;
  color: #8a9ca3;
  font-size: 14px;
  line-height: 1.35;
}

.main {
  margin-top: 38px;
}

.section-label {
  margin: 0 0 18px;
}

.limit-row {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 26px;
}

.limit-row::before {
  content: "";
  position: absolute;
  left: 70px;
  right: 70px;
  top: 37px;
  height: 1px;
  background: linear-gradient(
    90deg,
    rgba(95, 127, 137, 0.08),
    rgba(95, 127, 137, 0.34),
    rgba(95, 127, 137, 0.08)
  );
}

.limit-item {
  position: relative;
  min-height: 220px;
  box-sizing: border-box;
  padding: 20px 20px 18px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.52);
  border: 1px solid rgba(120, 145, 154, 0.20);
  transition:
    transform 180ms ease,
    background 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.limit-item:hover {
  transform: translateY(-6px);
  background: rgba(255, 255, 255, 0.88);
  border-color: rgba(95, 127, 137, 0.48);
  box-shadow: 0 18px 40px rgba(31, 41, 51, 0.08);
}

.number {
  width: 34px;
  height: 34px;
  display: grid;
  place-items: center;
  border-radius: 13px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 11px;
  transition:
    transform 160ms ease,
    background 160ms ease;
}

.limit-item:hover .number {
  transform: scale(1.08);
  background: #ffffff;
}

.limit-item h2 {
  margin: 22px 0 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 27px;
  line-height: 1.12;
  font-weight: 400;
}

.limit-item p {
  margin: 14px 0 0;
  color: #6b7d86;
  font-size: 13px;
  line-height: 1.42;
}

.bottom-message {
  margin-top: 28px;
  padding: 16px 18px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  background: rgba(255, 255, 255, 0.48);
  border-radius: 0 20px 20px 0;
  transition:
    transform 180ms ease,
    background 180ms ease,
    box-shadow 180ms ease;
}

.bottom-message:hover {
  transform: translateX(6px);
  background: rgba(255, 255, 255, 0.78);
  box-shadow: 0 14px 34px rgba(31, 41, 51, 0.07);
}

.bottom-message .label {
  margin: 0 0 8px;
}

.bottom-message h3 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 21px;
  line-height: 1.18;
  font-weight: 400;
}
</style>