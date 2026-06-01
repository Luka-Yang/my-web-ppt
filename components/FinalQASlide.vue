<template>
  <main class="final-page">
    <section class="header">
      <p class="eyebrow">Qualitative Results · 4.3</p>
      <h1>FabGPT Q&amp;A Example</h1>
      <p class="subtitle">
        FabGPT can answer defect-related questions and general IC process questions
      </p>
    </section>

    <section class="image-card">
      <img src="/fabgpt-qa-example.png" alt="FabGPT Q&A qualitative example" />
    </section>
  </main>
</template>

<script setup>
</script>

<style scoped>
.final-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 20px 54px 18px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.10), transparent 30%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow {
  margin: 0 0 5px;
  color: #5f7f89;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  font-size: 9.5px;
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

.image-card {
  margin-top: 22px;
  height: 445px;
  padding: 18px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.62);
  border: 1px solid rgba(120, 145, 154, 0.20);
  box-shadow: 0 12px 24px rgba(31, 41, 51, 0.045);
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-card img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}
</style>