<template>
  <main class="fine-page">
    <section class="header">
      <p class="eyebrow">Preliminaries · 2.3</p>
      <h1>Fine-Tuning Methods</h1>
      <p class="subtitle">
        Fine-tuning adapts pre-trained models to new tasks, but may introduce cost, overfitting, and modality-bias risks.
      </p>
    </section>

    <section class="main">
      <section class="left">
        <p class="label">Two Strategies</p>
        <h2>Full tuning versus partial tuning</h2>

        <div class="strategy">
          <span>01</span>
          <div>
            <strong>Full fine-tuning</strong>
            <p>All pre-trained weights are trainable.</p>
            <em>Flexible, but costly and prone to overfitting.</em>
          </div>
        </div>

        <div class="strategy">
          <span>02</span>
          <div>
            <strong>Partial fine-tuning</strong>
            <p>Only selected parameters are updated.</p>
            <em>More efficient, but still needs careful design.</em>
          </div>
        </div>
      </section>

      <section class="right">
        <div class="right-head">
          <p class="label">Popular Partial Methods</p>
          <div class="risk">Risk: modality bias</div>
        </div>

        <div class="method">
          <span>01</span>
          <div>
            <strong>Adapters</strong>
            <p>Add small trainable modules while most weights stay frozen.</p>
          </div>
        </div>

        <div class="method">
          <span>02</span>
          <div>
            <strong>Prompt Learning</strong>
            <p>Use learnable prompts or instructions for task adaptation.</p>
          </div>
        </div>

        <div class="method">
          <span>03</span>
          <div>
            <strong>LoRA</strong>
            <p>Update low-rank parameter components efficiently.</p>
          </div>
        </div>

        <p class="bias-note">
          After fine-tuning, models may over-focus on image inputs and neglect user queries.
        </p>
      </section>
    </section>
  </main>
</template>

<style scoped>
.fine-page {
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
  grid-template-columns: 0.9fr 1.1fr;
  gap: 62px;
  align-items: start;
}

.label {
  margin: 0 0 13px;
}

.left h2 {
  margin: 0 0 26px;
  max-width: 520px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 35px;
  line-height: 1.07;
  font-weight: 400;
}

.strategy,
.method {
  display: grid;
  grid-template-columns: 36px 1fr;
  gap: 14px;
  align-items: start;
  padding: 12px 0 14px;
  border-bottom: 1px solid rgba(120, 145, 154, 0.22);
  transition: 160ms ease;
}

.strategy:hover,
.method:hover,
.risk:hover,
.bias-note:hover {
  transform: translateX(7px);
}

.strategy span,
.method span {
  width: 30px;
  height: 30px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10px;
}

.strategy strong,
.method strong {
  color: #1f2933;
  font-size: 14px;
  font-weight: 500;
}

.strategy p,
.method p {
  margin: 5px 0 0;
  color: #6b7d86;
  font-size: 12px;
  line-height: 1.28;
}

.strategy em {
  display: block;
  margin-top: 6px;
  color: #5f7f89;
  font-size: 11.4px;
  font-style: normal;
}

.right-head {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 13px;
}

.right-head .label {
  margin: 0;
}

.risk {
  padding: 7px 11px;
  border-radius: 999px;
  background: rgba(255,255,255,0.62);
  border: 1px solid rgba(120,145,154,0.22);
  color: #314f5a;
  font-size: 11px;
  transition: 160ms ease;
}

.bias-note {
  margin: 18px 0 0;
  padding-left: 14px;
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  color: #6b7d86;
  font-size: 12.2px;
  line-height: 1.3;
  transition: 160ms ease;
}
</style>