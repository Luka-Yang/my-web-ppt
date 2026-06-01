<template>
  <main class="cover-page">
    <section class="left">
      <p class="eyebrow">Paper Presentation · ICCAD 2024</p>

      <h1>FabGPT</h1>

      <h2>
        Wafer Defect<br />
        Knowledge Queries
      </h2>

      <p class="subtitle">
        An Efficient Large Multimodal Model for Complex Wafer Defect Knowledge Queries
      </p>

      <div class="topic-row">
        <span>SEM wafer image</span>
        <span>Large multimodal model</span>
        <span>Defect Q&amp;A</span>
      </div>

      <p class="presenter">Presenter: CHIH YU YANG</p>
    </section>

    <section class="right">
      <div class="wafer">
        <div class="ring r1"></div>
        <div class="ring r2"></div>
        <div class="ring r3"></div>

        <span class="defect d1"></span>
        <span class="defect d2"></span>
        <span class="defect d3"></span>

        <p>SEM</p>
      </div>

      <div class="flow">
        <div class="step">
          <span>01</span>
          <strong>Input</strong>
          <p>SEM Image</p>
        </div>

        <div class="arrow">→</div>

        <div class="step">
          <span>02</span>
          <strong>Model</strong>
          <p>FabGPT</p>
        </div>

        <div class="arrow">→</div>

        <div class="step output-step">
          <span>03</span>
          <strong>Output</strong>
          <p>Mask + Q&amp;A</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.cover-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 44px 68px 38px;
  overflow: hidden;
  display: grid;
  grid-template-columns: 0.95fr 1.05fr;
  gap: 38px;
  align-items: center;
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

/* Left title area */

.left {
  position: relative;
  z-index: 2;
}

.eyebrow {
  margin: 0 0 22px;
  color: #2f6fd6;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
}

h1 {
  margin: 0;
  color: #07111f;
  font-family:
    Georgia,
    Cambria,
    "Times New Roman",
    serif;
  font-size: 76px;
  line-height: 0.95;
  font-weight: 400;
  letter-spacing: -0.035em;
}

h2 {
  margin: 16px 0 0;
  color: #314f5a;
  font-family:
    Georgia,
    Cambria,
    "Times New Roman",
    serif;
  font-size: 39px;
  line-height: 1.08;
  font-weight: 400;
}

.subtitle {
  margin: 22px 0 0;
  max-width: 520px;
  color: #7d8e96;
  font-size: 15.5px;
  line-height: 1.38;
}

.topic-row {
  margin-top: 28px;
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
}

.topic-row span {
  padding: 8px 13px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.76);
  border: 1px solid rgba(120, 145, 154, 0.24);
  color: #314f5a;
  font-size: 11.8px;
  transition:
    transform 160ms ease,
    background 160ms ease,
    border-color 160ms ease,
    box-shadow 160ms ease;
}

.topic-row span:hover {
  transform: translateY(-4px);
  background: #ffffff;
  border-color: rgba(47, 111, 214, 0.45);
  box-shadow: 0 14px 28px rgba(31, 41, 51, 0.08);
}

.presenter {
  margin: 34px 0 0;
  color: #5f6f78;
  font-size: 13px;
  font-weight: 500;
}

/* Right visual area */

.right {
  position: relative;
  height: 390px;
}

.wafer {
  position: absolute;
  right: 92px;
  top: 0;
  width: 250px;
  height: 250px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  background:
    radial-gradient(circle, rgba(255, 255, 255, 0.96), rgba(231, 238, 240, 0.82));
  border: 1px solid rgba(95, 127, 137, 0.28);
  box-shadow:
    inset 0 0 0 16px rgba(95, 127, 137, 0.035),
    0 22px 52px rgba(31, 41, 51, 0.10);
  transition:
    transform 220ms ease,
    box-shadow 220ms ease,
    border-color 220ms ease;
}

.wafer:hover {
  transform: translateY(-7px) scale(1.02);
  border-color: rgba(47, 111, 214, 0.34);
  box-shadow:
    inset 0 0 0 16px rgba(95, 127, 137, 0.035),
    0 30px 64px rgba(31, 41, 51, 0.15);
}

.wafer p {
  position: relative;
  z-index: 3;
  margin: 0;
  color: #314f5a;
  font-family:
    Georgia,
    Cambria,
    "Times New Roman",
    serif;
  font-size: 31px;
}

.ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(95, 127, 137, 0.15);
}

.r1 {
  inset: 45px;
}

.r2 {
  inset: 75px;
}

.r3 {
  inset: 104px;
}

.defect {
  position: absolute;
  border-radius: 50%;
  background: #5f7f89;
  box-shadow: 0 0 0 8px rgba(95, 127, 137, 0.13);
  animation: pulse 2.4s ease-in-out infinite;
}

.d1 {
  width: 12px;
  height: 12px;
  left: 80px;
  top: 78px;
}

.d2 {
  width: 9px;
  height: 9px;
  right: 62px;
  top: 116px;
  animation-delay: 0.5s;
}

.d3 {
  width: 11px;
  height: 11px;
  left: 108px;
  bottom: 63px;
  animation-delay: 0.9s;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 0.55;
    transform: scale(1);
  }

  50% {
    opacity: 1;
    transform: scale(1.15);
  }
}

/* Flow strip */

.flow {
  position: absolute;
  left: 6px;
  right: 0;
  bottom: 18px;
  height: 96px;
  display: grid;
  grid-template-columns: 1.08fr 28px 1fr 28px 1.28fr;
  gap: 8px;
  align-items: center;
}

.step {
  height: 90px;
  box-sizing: border-box;
  padding: 12px 13px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.78);
  border: 1px solid rgba(120, 145, 154, 0.24);
  box-shadow: 0 14px 32px rgba(31, 41, 51, 0.055);
  transition:
    transform 180ms ease,
    background 180ms ease,
    border-color 180ms ease,
    box-shadow 180ms ease;
}

.step:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.98);
  border-color: rgba(47, 111, 214, 0.38);
  box-shadow: 0 20px 44px rgba(31, 41, 51, 0.11);
}

.step span {
  width: 27px;
  height: 27px;
  display: grid;
  place-items: center;
  border-radius: 11px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.step strong {
  display: block;
  margin-top: 9px;
  color: #2f6fd6;
  font-size: 9px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

.step p {
  margin: 4px 0 0;
  color: #1f2933;
  font-size: 13px;
  font-weight: 500;
  white-space: nowrap;
}

.output-step p {
  font-size: 12.5px;
}

.arrow {
  color: #8a9ca3;
  font-size: 25px;
  text-align: center;
}
</style>