<template>
  <main class="lmm-page">
    <section class="header">
      <p class="eyebrow">Preliminaries · 2.2</p>
      <h1>Large Multimodal Models</h1>
      <p class="subtitle">
        LMMs support image-text reasoning, but adapting them to SEM wafer defects remains difficult.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">General Capability</p>
        <h2>Large-scale multimodal understanding</h2>

        <p class="desc">
          LMMs learn from large-scale datasets to understand visual content and generate descriptions or answers.
        </p>

        <div class="keywords">
          <span>Images</span>
          <span>Text</span>
          <span>Spectra</span>
          <span>Sound</span>
        </div>

        <p class="domain-gap">
          <strong>Domain gap:</strong>
          robustness may drop in specialized SEM wafer defect analysis.
        </p>
      </section>

      <section class="right">
        <p class="label">Representative Ideas</p>

        <button v-for="item in methods" :key="item.id" class="method">
          <span>{{ item.id }}</span>
          <div>
            <strong>{{ item.title }}</strong>
            <p>{{ item.short }}</p>
          </div>
        </button>
      </section>
    </section>
  </main>
</template>

<script setup>
const methods = [
  {
    id: '01',
    title: 'BLIP-2 + Vicuna',
    short: 'Align frozen visual features with an LLM for image-text Q&A.',
  },
  {
    id: '02',
    title: 'Contrastive Learning',
    short: 'Embed image and text semantics into a shared space for zero-shot transfer.',
  },
  {
    id: '03',
    title: 'DALL-E Style Generation',
    short: 'Use text representations to guide visual content generation.',
  },
]
</script>

<style scoped>
.lmm-page {
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
  margin-top: 46px;
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
  max-width: 500px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 35px;
  line-height: 1.07;
  font-weight: 400;
}

.desc {
  margin: 22px 0 0;
  max-width: 500px;
  color: #6b7d86;
  font-size: 13px;
  line-height: 1.36;
}

.keywords {
  margin-top: 26px;
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
  transition: 160ms ease;
}

.domain-gap {
  margin-top: 28px;
  max-width: 520px;
  padding-left: 14px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  color: #6b7d86;
  font-size: 12.4px;
  line-height: 1.32;
}

.domain-gap strong {
  color: #1f2933;
  font-weight: 500;
}

.right {
  display: grid;
  gap: 16px;
}

.method {
  cursor: pointer;
  width: 100%;
  text-align: left;
  display: grid;
  grid-template-columns: 34px 1fr;
  gap: 5px 15px;
  padding: 14px 4px 15px 0;
  border: none;
  border-bottom: 1px solid rgba(120, 145, 154, 0.22);
  background: transparent;
  transition: 160ms ease;
}

.method:hover,
.keywords span:hover {
  transform: translateX(8px);
}

.method span {
  grid-row: span 2;
  width: 30px;
  height: 30px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.method strong {
  color: #1f2933;
  font-size: 15px;
  font-weight: 500;
}

.method p {
  margin: 0;
  color: #6b7d86;
  font-size: 12px;
  line-height: 1.28;
}
</style>