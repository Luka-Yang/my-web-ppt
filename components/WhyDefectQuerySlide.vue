<template>
  <main class="why-page">
    <section class="header">
      <p class="eyebrow">Introduction</p>
      <h1>Why Wafer Defect Knowledge Query Matters</h1>
      <p class="subtitle">
        Wafer defects are not only visual anomalies; they can indicate fabrication problems and reliability risks.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">Core Idea</p>
        <h2>Defects are manufacturing signals</h2>
        <p>
          A defect observed in a SEM image may reflect process instability,
          yield loss, or potential device reliability issues.
        </p>
      </section>

      <section class="right">
        <div class="item">
          <span>01</span>
          <div>
            <strong>Quality Control</strong>
            <p>Detect abnormal wafer surface conditions during inspection.</p>
          </div>
        </div>

        <div class="item">
          <span>02</span>
          <div>
            <strong>Yield Impact</strong>
            <p>Understand how defect patterns may affect production yield.</p>
          </div>
        </div>

        <div class="item">
          <span>03</span>
          <div>
            <strong>Process Diagnosis</strong>
            <p>Connect visual defect evidence with possible fabrication causes.</p>
          </div>
        </div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.why-page {
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
  max-width: 980px;
  color: #8a9ca3;
  font-size: 14px;
  line-height: 1.35;
}

.main {
  margin-top: 28px;
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 60px;
  align-items: start;
}

.left {
  padding-top: 12px;
  transition: transform 180ms ease, filter 180ms ease;
}

.left:hover {
  transform: translateY(-6px);
  filter: drop-shadow(0 16px 24px rgba(31, 41, 51, 0.08));
}

.label {
  margin: 0 0 16px;
}

.left h2 {
  margin: 0;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 35px;
  line-height: 1.05;
  font-weight: 400;
}

.left p {
  margin: 24px 0 0;
  max-width: 470px;
  color: #6b7d86;
  font-size: 15px;
  line-height: 1.48;
}

.right {
  display: grid;
  gap: 16px;
}

.item {
  display: grid;
  grid-template-columns: 46px 1fr;
  gap: 18px;
  align-items: start;
  padding: 16px 0 18px;
  border-bottom: 1px solid rgba(120, 145, 154, 0.22);
  transition:
    transform 160ms ease,
    background 160ms ease,
    padding 160ms ease,
    border-radius 160ms ease,
    box-shadow 160ms ease;
}

.item:hover {
  transform: translateX(8px);
  padding-left: 14px;
  background: rgba(255, 255, 255, 0.48);
  border-radius: 18px;
  box-shadow: 0 12px 28px rgba(31, 41, 51, 0.055);
}

.item span {
  width: 36px;
  height: 36px;
  display: grid;
  place-items: center;
  border-radius: 14px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 12px;
  transition: transform 160ms ease, background 160ms ease;
}

.item:hover span {
  transform: scale(1.08);
  background: #ffffff;
}

.item strong {
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 25px;
  font-weight: 400;
}

.item p {
  margin: 7px 0 0;
  color: #6b7d86;
  font-size: 13.2px;
  line-height: 1.38;
}
</style>