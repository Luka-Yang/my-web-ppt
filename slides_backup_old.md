---
theme: seriph
title: FabGPT Paper Presentation
info: |
  Interactive paper presentation for FabGPT: An Efficient Large Multimodal Model for Complex Wafer Defect Knowledge Queries.
class: text-slate-900
transition: slide-left
drawings:
  persist: false
mdc: true
canvasWidth: 1400
fonts:
  sans: Inter
  serif: Georgia
  mono: JetBrains Mono
---

<style>
:root {
  --ink: #0f172a;
  --muted: #64748b;
  --line: #d9e2ee;
  --surface: #f8fafc;
  --card: #ffffff;
  --accent: #2563eb;
  --accent-2: #0f766e;
  --soft: #eff6ff;
  --green-soft: #ecfdf5;
}
.slidev-layout {
  background:
    radial-gradient(circle at 12% 4%, rgba(37, 99, 235, 0.10), transparent 30%),
    radial-gradient(circle at 90% 12%, rgba(15, 118, 110, 0.08), transparent 28%),
    #f8fafc;
  color: var(--ink);
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  padding: 52px 72px;
  overflow: hidden;
}
.slidev-layout h1,
.slidev-layout h2,
.slidev-layout h3 { letter-spacing: -0.04em; }
.slidev-layout h1 { font-weight: 780; line-height: 0.98; }
.slidev-layout h2 { font-weight: 740; }
.kicker { color: var(--accent); font-size: .78rem; letter-spacing: .17em; text-transform: uppercase; font-weight: 850; }
.muted { color: var(--muted); }
.hl { color: var(--accent); font-weight: 850; }
.badge { display: inline-flex; align-items: center; justify-content:center; gap: 6px; border: 1px solid #bfdbfe; background: #eff6ff; color: #1d4ed8; border-radius: 999px; padding: 6px 13px; font-size: .78rem; font-weight: 780; }
.badge-teal { border-color: #99f6e4; background: #f0fdfa; color: #0f766e; }
.card, .hover-card {
  background: rgba(255,255,255,.90);
  border: 1px solid var(--line);
  border-radius: 24px;
  box-shadow: 0 18px 55px rgba(15,23,42,.08);
}
.hover-card {
  position: relative;
  cursor: pointer;
  transition: transform .22s ease, box-shadow .22s ease, border-color .22s ease, background .22s ease;
}
.hover-card:hover {
  transform: translateY(-7px) scale(1.012);
  border-color: rgba(37,99,235,.50);
  box-shadow: 0 28px 75px rgba(37,99,235,.16);
  background: #ffffff;
}
.hover-card .hover-note {
  opacity: 0;
  transform: translateY(6px);
  transition: opacity .22s ease, transform .22s ease;
}
.hover-card:hover .hover-note { opacity: 1; transform: translateY(0); }
.mini-card { background: rgba(255,255,255,.92); border: 1px solid var(--line); border-radius: 18px; padding: 18px 20px; }
.metric { font-size: 2.25rem; font-weight: 820; letter-spacing: -0.055em; color: var(--accent); line-height: 1; }
.metric-sm { font-size: 1.55rem; font-weight: 800; color: var(--accent); letter-spacing: -0.045em; }
.visual-frame { display:flex; align-items:center; justify-content:center; overflow:hidden; background:#fff; border:1px solid var(--line); border-radius:18px; box-shadow:0 14px 42px rgba(15,23,42,.08); }
.visual-frame img { width: 100%; height: 100%; object-fit: contain; }
.visual-frame.cover img { object-fit: cover; }
.divider { height: 1px; background: linear-gradient(90deg, transparent, #cbd5e1, transparent); }
.flow { display:grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
.flow-card { min-height: 205px; }
.flow-card::after { content:""; position:absolute; top:50%; right:-24px; width:32px; height:2px; background:#94a3b8; }
.flow-card:last-child::after { display:none; }
.num { width: 34px; height: 34px; border-radius: 999px; display:inline-flex; align-items:center; justify-content:center; background: var(--soft); color: var(--accent); font-weight: 850; }
.small-table { width:100%; border-collapse:collapse; font-size:.86rem; }
.small-table th { color:#475569; text-align:left; border-bottom:1px solid #cbd5e1; padding:8px 6px; font-weight:800; }
.small-table td { border-bottom:1px solid #e2e8f0; padding:8px 6px; }
.gridline { background-image: linear-gradient(#e2e8f0 1px, transparent 1px), linear-gradient(90deg,#e2e8f0 1px, transparent 1px); background-size: 28px 28px; }
.step-dot { width:12px; height:12px; border-radius:999px; background:var(--accent); box-shadow:0 0 0 6px rgba(37,99,235,.12); }
.safe-img { max-height: 100%; max-width: 100%; object-fit: contain; }
</style>

<div class="h-full grid grid-cols-[1.02fr_.98fr] gap-10 items-center">
  <div>
    <div class="kicker mb-5">ICCAD 2024 Paper Presentation</div>
    <h1 class="text-[4.25rem] mb-5">FabGPT</h1>
    <div class="text-[2.05rem] font-700 leading-tight mb-7 max-w-[780px]">An Efficient Large Multimodal Model for Complex Wafer Defect Knowledge Queries</div>
    <div class="divider mb-6"></div>
    <p class="text-xl muted leading-relaxed max-w-[760px]">
      A domain-customized large multimodal model for SEM wafer defect detection, localization, root-cause analysis, and fabrication Q&A.
    </p>
    <div class="mt-8 flex flex-wrap gap-3">
      <span class="badge">Large Multimodal Model</span>
      <span class="badge badge-teal">Wafer Defect Analysis</span>
      <span class="badge">SEM Images</span>
    </div>
  </div>
  <div class="hover-card p-5">
    <div class="visual-frame h-[405px]"><img src="/figures/fig1_comparison_clean.png" /></div>
    <div class="text-sm muted mt-4 hover-note">Hover feedback: the figure card lifts and highlights.</div>
  </div>
</div>

<!-- The paper frames FabGPT as a wafer defect knowledge-query system, not only an image detector. -->

---
title: Executive Summary
---

<div class="h-full flex flex-col justify-center">
  <div class="kicker mb-4">Executive Summary</div>
  <h1 class="text-[3.35rem] mb-8 max-w-[1160px]">FabGPT turns wafer inspection into an interactive knowledge-query workflow.</h1>
  <div class="grid grid-cols-3 gap-6">
    <div class="hover-card p-7" v-click>
      <div class="num mb-5">1</div>
      <h2 class="text-2xl mb-3">Detect</h2>
      <p class="muted leading-relaxed">Find minute defects in complex SEM wafer backgrounds.</p>
      <p class="text-sm hl mt-4 hover-note">Visual precision</p>
    </div>
    <div class="hover-card p-7" v-click>
      <div class="num mb-5">2</div>
      <h2 class="text-2xl mb-3">Localize</h2>
      <p class="muted leading-relaxed">Generate pixel-level masks instead of relying on manual thresholds.</p>
      <p class="text-sm hl mt-4 hover-note">Mask output</p>
    </div>
    <div class="hover-card p-7" v-click>
      <div class="num mb-5">3</div>
      <h2 class="text-2xl mb-3">Explain</h2>
      <p class="muted leading-relaxed">Answer defect-related and general IC fabrication questions.</p>
      <p class="text-sm hl mt-4 hover-note">Knowledge query</p>
    </div>
  </div>
  <div class="card mt-8 p-6 grid grid-cols-4 gap-4 text-center">
    <div><div class="metric">91.81%</div><div class="muted">Image-AUC</div></div>
    <div><div class="metric">95.61%</div><div class="muted">Pixel-AUC</div></div>
    <div><div class="metric">88.17%</div><div class="muted">PRO</div></div>
    <div><div class="metric">96.86%</div><div class="muted">Q&A accuracy</div></div>
  </div>
</div>

---
title: Talk Roadmap
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Roadmap</div>
    <h1 class="text-[3.2rem] mb-6">A paper-reading flow, not a paragraph-by-paragraph summary.</h1>
    <p class="text-xl muted leading-relaxed">The presentation follows four questions: why, what, how well, and what to question.</p>
  </div>
  <div class="card p-7 grid gap-4">
    <div class="hover-card p-5" v-click><span class="num mr-3">1</span><span class="text-2xl font-750">Why does this matter?</span><p class="muted mt-2 ml-12">Wafer defects affect reliability and process yield.</p></div>
    <div class="hover-card p-5" v-click><span class="num mr-3">2</span><span class="text-2xl font-750">What problem is unsolved?</span><p class="muted mt-2 ml-12">Tiny defects + modality bias.</p></div>
    <div class="hover-card p-5" v-click><span class="num mr-3">3</span><span class="text-2xl font-750">How does FabGPT work?</span><p class="muted mt-2 ml-12">A three-stage multimodal pipeline.</p></div>
    <div class="hover-card p-5" v-click><span class="num mr-3">4</span><span class="text-2xl font-750">How convincing is the evidence?</span><p class="muted mt-2 ml-12">Metrics, qualitative results, ablations, and limitations.</p></div>
  </div>
</div>

---
title: Why Wafer Defect Query Matters
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Motivation</div>
    <h1 class="text-[3rem] mb-6">Wafer defects are small, costly, and knowledge-intensive.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Manufacturing complexity</b><br/><span class="muted">Many fabrication steps may introduce random surface defects.</span></div>
      <div class="hover-card p-5" v-click><b>Engineering decision-making</b><br/><span class="muted">Engineers need type, location, cause, and process knowledge, not only a defect label.</span></div>
      <div class="hover-card p-5" v-click><b>SEM image challenge</b><br/><span class="muted">Minute defects can be hidden inside complex wafer patterns.</span></div>
    </div>
  </div>
  <div class="hover-card p-6">
    <div class="visual-frame h-[410px]"><img src="/figures/fig2_dataset_clean.png" /></div>
    <div class="mt-5 grid grid-cols-5 gap-2 text-center text-xs">
      <div class="badge">Good</div><div class="badge">Hole</div><div class="badge">Particle</div><div class="badge">Scratch</div><div class="badge">Pattern Def.</div>
    </div>
  </div>
</div>

---
title: Problem 1 Minute Defects
---

<div class="h-full grid grid-cols-[.9fr_1.1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Problem 1</div>
    <h1 class="text-[3.05rem] mb-6">Minute defects are difficult to detect under complex SEM backgrounds.</h1>
    <p class="text-xl muted leading-relaxed mb-6">The paper argues that existing LMMs may fail to identify the correct number, position, or type of small defects.</p>
    <div class="hover-card p-5 bg-blue-50" v-click><b>Presentation focus:</b> explain why the task is more than simple image classification.</div>
  </div>
  <div class="hover-card p-5">
    <div class="visual-frame h-[460px]"><img src="/figures/fig1_comparison_clean.png" /></div>
  </div>
</div>

---
title: Problem 2 Modality Bias
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Problem 2</div>
    <h1 class="text-[3.05rem] mb-6">Fine-tuned LMMs may over-focus on images and lose general Q&A ability.</h1>
    <p class="text-xl muted leading-relaxed">The paper calls this issue <span class="hl">modality bias</span>: the model becomes too visually biased even when the question is not image-related.</p>
  </div>
  <div class="card p-7 grid gap-4">
    <div class="hover-card p-5" v-click>
      <div class="badge mb-3">Image-related</div>
      <div class="text-xl font-750">“Where is the defect located?”</div>
      <p class="muted mt-2">The model should use visual prompts strongly.</p>
    </div>
    <div class="hover-card p-5" v-click>
      <div class="badge badge-teal mb-3">General IC knowledge</div>
      <div class="text-xl font-750">“What are the core process steps in IC manufacturing?”</div>
      <p class="muted mt-2">The model should not be dominated by the image.</p>
    </div>
  </div>
</div>

---
title: SEM-WaD Dataset
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Dataset</div>
    <h1 class="text-[3rem] mb-6">SEM-WaD combines defect images, masks, and textual knowledge.</h1>
    <table class="small-table card overflow-hidden">
      <thead><tr><th>Item</th><th>Value</th></tr></thead>
      <tbody>
        <tr><td>Image type</td><td>SEM wafer images</td></tr>
        <tr><td>Resolution</td><td>480 × 480</td></tr>
        <tr><td>Good images</td><td>1,226</td></tr>
        <tr><td>Defective images</td><td>1,182</td></tr>
        <tr><td>Defect classes</td><td>Hole, Particle, Scratch, Pattern Deformation</td></tr>
        <tr><td>Split</td><td>Training / test = 7 : 3</td></tr>
      </tbody>
    </table>
  </div>
  <div class="hover-card p-6">
    <div class="visual-frame h-[380px]"><img src="/figures/fig2_dataset_clean.png" /></div>
    <div class="grid grid-cols-2 gap-4 mt-6">
      <div class="mini-card text-center"><div class="metric">2,408</div><div class="muted">total images</div></div>
      <div class="mini-card text-center"><div class="metric">4</div><div class="muted">defect types</div></div>
    </div>
  </div>
</div>

---
title: Prior Methods Gap
---

<div class="h-full grid grid-cols-[1fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Preliminaries</div>
    <h1 class="text-[3rem] mb-6">Prior methods solve parts of the workflow, but not the full knowledge-query task.</h1>
    <p class="text-xl muted leading-relaxed">This slide positions FabGPT between visual defect inspection and domain-aware dialogue.</p>
  </div>
  <div class="card p-7 grid grid-cols-3 gap-5 text-center">
    <div class="hover-card p-5" v-click><div class="metric-sm mb-2">CNN</div><b>Detection</b><p class="text-sm muted mt-2">strong visual features, weak Q&A</p></div>
    <div class="hover-card p-5" v-click><div class="metric-sm mb-2">LMM</div><b>Reasoning</b><p class="text-sm muted mt-2">general image-text ability, weak fab knowledge</p></div>
    <div class="hover-card p-5" v-click><div class="metric-sm mb-2">FT</div><b>Adaptation</b><p class="text-sm muted mt-2">domain knowledge, possible modality bias</p></div>
    <div class="col-span-3 divider my-1"></div>
    <div class="col-span-3 text-2xl font-750">FabGPT aims to integrate detection + localization + analysis + Q&A.</div>
  </div>
</div>

---
title: FabGPT Main Idea
---

<div class="h-full flex flex-col justify-center">
  <div class="kicker mb-4">Main Idea</div>
  <h1 class="text-[3.08rem] mb-8">FabGPT uses three stages to bridge wafer images, defect semantics, and dialogue.</h1>
  <div class="flow">
    <div class="hover-card flow-card p-6" v-click>
      <div class="badge mb-4">Stage 1</div>
      <h2 class="text-2xl">Modal Enhancement</h2>
      <p class="muted mt-3">Improve multimodal prompt features from image, OCR text marks, and labels.</p>
      <p class="text-sm hl mt-5 hover-note">Better input representation</p>
    </div>
    <div class="hover-card flow-card p-6" v-click>
      <div class="badge mb-4">Stage 2</div>
      <h2 class="text-2xl">Detection</h2>
      <p class="muted mt-3">Generate pixel-level defect masks through a learned detection head.</p>
      <p class="text-sm hl mt-5 hover-note">Automatic mask output</p>
    </div>
    <div class="hover-card flow-card p-6" v-click>
      <div class="badge mb-4">Stage 3</div>
      <h2 class="text-2xl">Q&A</h2>
      <p class="muted mt-3">Use modulation and corpus training to reduce modality bias.</p>
      <p class="text-sm hl mt-5 hover-note">Balanced knowledge response</p>
    </div>
  </div>
  <div class="hover-card mt-7 p-4">
    <div class="visual-frame h-[245px]"><img src="/figures/fig3_architecture_clean.png" /></div>
  </div>
</div>

---
title: Overall Architecture
---

<div class="h-full grid grid-rows-[auto_1fr] gap-5">
  <div>
    <div class="kicker mb-3">Architecture</div>
    <h1 class="text-[2.8rem]">Overall FabGPT pipeline</h1>
  </div>
  <div class="grid grid-cols-[1.2fr_.8fr] gap-8 items-center">
    <div class="hover-card p-4">
      <div class="visual-frame h-[525px]"><img src="/figures/fig3_architecture_clean.png" /></div>
    </div>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Input</b><br/><span class="muted">Query image + OCR text marks + label set</span></div>
      <div class="hover-card p-5" v-click><b>Enhancement</b><br/><span class="muted">Prediction Module + prompt-learning adapters</span></div>
      <div class="hover-card p-5" v-click><b>Detection output</b><br/><span class="muted">Pixel-level mask for defect localization</span></div>
      <div class="hover-card p-5 bg-blue-50" v-click><b>Q&A output</b><br/><span class="muted">A natural-language answer conditioned on relevance.</span></div>
    </div>
  </div>
</div>

---
title: Stage 1 Modal Enhancement
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Stage 1</div>
    <h1 class="text-[3rem] mb-6">Modal Enhancement makes defect features more informative before detection and Q&A.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Prediction Module</b><br/><span class="muted">Predicts defect category and injects semantic information.</span></div>
      <div class="hover-card p-5" v-click><b>Visual/Textual Adapters</b><br/><span class="muted">Use pre-trained experts for feature optimization.</span></div>
      <div class="hover-card p-5" v-click><b>Output tokens</b><br/><span class="muted">Generate information-rich image and text tokens.</span></div>
    </div>
  </div>
  <div class="hover-card p-6">
    <div class="visual-frame h-[250px]"><img src="/figures/fig4_modules_clean.png" /></div>
    <div class="mt-6 card p-5 bg-blue-50"><b>Speaker note:</b> do not explain every formula; emphasize that this stage improves prompt quality.</div>
  </div>
</div>

---
title: Prediction Module
---

<div class="h-full grid grid-cols-[1.05fr_.95fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Prediction Module</div>
    <h1 class="text-[3rem] mb-6">PM adds defect-category semantics before downstream tasks.</h1>
    <div class="card p-6 grid grid-cols-4 gap-4 text-center">
      <div class="hover-card p-4"><b>Image</b><p class="muted text-sm mt-1">CLIP visual vector</p></div>
      <div class="hover-card p-4"><b>Label Set</b><p class="muted text-sm mt-1">defect categories</p></div>
      <div class="hover-card p-4"><b>Cosine Similarity</b><p class="muted text-sm mt-1">category matching</p></div>
      <div class="hover-card p-4"><b>Enhanced Token</b><p class="muted text-sm mt-1">semantic feature</p></div>
    </div>
    <div class="mt-6 hover-card p-5 bg-blue-50" v-click>
      <b>Why it matters:</b> pixel-level details alone may not preserve high-level defect meaning after repeated down-sampling.
    </div>
  </div>
  <div class="hover-card p-5">
    <div class="visual-frame h-[440px]"><img src="/figures/fig4_modules_clean.png" /></div>
  </div>
</div>

---
title: Stage 2 Detection Head
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Stage 2</div>
    <h1 class="text-[3rem] mb-6">The detection head learns pixel-level masks automatically.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Input:</b> image token + text token</div>
      <div class="hover-card p-5" v-click><b>Fusion:</b> multimodal feature interaction</div>
      <div class="hover-card p-5" v-click><b>Decoder:</b> four up-sampling operations</div>
      <div class="hover-card p-5" v-click><b>Output:</b> supervised pixel-level mask</div>
    </div>
  </div>
  <div class="hover-card p-6 gridline">
    <div class="grid grid-cols-4 gap-3 items-center text-center mb-6">
      <div class="mini-card"><b>Image Token</b></div><div class="text-3xl">×</div><div class="mini-card"><b>Text Token</b></div><div class="mini-card"><b>Mask</b></div>
    </div>
    <div class="visual-frame h-[320px]"><img src="/figures/fig6_lmm_clean.png" /></div>
  </div>
</div>

---
title: Stage 3 Q&A Modulation
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Stage 3</div>
    <h1 class="text-[3rem] mb-6">The Q&A stage controls how much visual information should influence the answer.</h1>
    <p class="text-xl muted leading-relaxed mb-6">The modulation module aligns visual, textual, mask, and question tokens, then applies an updating factor <span class="hl">a</span>.</p>
    <div class="hover-card p-5 bg-blue-50" v-click>
      <b>Key intuition:</b> if the user question is unrelated to the image, the model should rely less on visual prompts.
    </div>
  </div>
  <div class="card p-7 grid gap-5">
    <div class="hover-card p-5" v-click><b>Q-Former-like alignment</b><br/><span class="muted">Align visual, mask, and textual tokens.</span></div>
    <div class="hover-card p-5" v-click><b>Learnable corrector</b><br/><span class="muted">Estimate relevance between query and visual instructions.</span></div>
    <div class="hover-card p-5" v-click><b>Updated visual instruction</b><br/><span class="muted">Use <span class="hl">aT<sub>vis</sub></span> to mitigate modality bias.</span></div>
  </div>
</div>

---
title: Training Strategy and Loss
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Training Strategy</div>
    <h1 class="text-[3rem] mb-6">Interactive corpus training balances new defect knowledge and original general knowledge.</h1>
    <div class="grid gap-5">
      <div class="hover-card p-5" v-click><b>Corpus-A</b><br/><span class="muted">Defect-related Q&A: type, quantity, location, description, and analysis.</span></div>
      <div class="hover-card p-5" v-click><b>Corpus-B</b><br/><span class="muted">General Q&A unrelated to defect knowledge.</span></div>
      <div class="hover-card p-5" v-click><b>Training ratio</b><br/><span class="muted">Corpus-A : Corpus-B = <span class="hl">2 : 1</span></span></div>
    </div>
  </div>
  <div class="card p-8">
    <div class="text-2xl font-750 mb-5">Loss design</div>
    <table class="small-table">
      <thead><tr><th>Loss</th><th>Purpose</th></tr></thead>
      <tbody>
        <tr><td>Focal Loss</td><td>Hard pixels and class imbalance</td></tr>
        <tr><td>Dice Loss</td><td>Segmentation overlap</td></tr>
        <tr><td>Cross-Entropy</td><td>Classification and Q&A token prediction</td></tr>
      </tbody>
    </table>
    <div class="mt-6 p-4 rounded-xl bg-slate-100 font-mono text-sm">L = αL<sub>focal</sub> + βL<sub>dice</sub> + δL<sub>ce1</sub> + εL<sub>ce2</sub></div>
  </div>
</div>

---
title: Experimental Setup
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Experiments</div>
    <h1 class="text-[3rem] mb-6">The experiments evaluate both visual detection and language Q&A.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Backbone:</b> PandaGPT with Vicuna-7B and ImageBind-Huge</div>
      <div class="hover-card p-5" v-click><b>Training:</b> AdamW, cosine annealing, 50 epochs, three 4090Ti GPUs</div>
      <div class="hover-card p-5" v-click><b>Baselines:</b> DevNet, DRA, BGAD, PRN, Lisa, AnomalyGPT, GPT-4</div>
    </div>
  </div>
  <div class="card p-8">
    <div class="text-2xl font-750 mb-6">Evaluation metrics</div>
    <div class="grid grid-cols-2 gap-4">
      <div class="hover-card p-5"><b>Image-AUC</b><p class="muted text-sm">image-level defect judgment</p></div>
      <div class="hover-card p-5"><b>Pixel-AUC</b><p class="muted text-sm">pixel-level defect judgment</p></div>
      <div class="hover-card p-5"><b>PRO</b><p class="muted text-sm">region overlap quality</p></div>
      <div class="hover-card p-5"><b>AP</b><p class="muted text-sm">localization precision</p></div>
      <div class="hover-card p-5 col-span-2"><b>Q&A Accuracy</b><p class="muted text-sm">correctness on defect-related and unrelated questions</p></div>
    </div>
  </div>
</div>

---
title: Detection Results
---

<div class="h-full grid grid-rows-[auto_1fr] gap-5">
  <div>
    <div class="kicker mb-3">Quantitative Result 1</div>
    <h1 class="text-[2.8rem]">FabGPT achieves the best average detection performance.</h1>
  </div>
  <div class="grid grid-cols-[1.18fr_.82fr] gap-8 items-center">
    <div class="hover-card p-5">
      <div class="visual-frame h-[470px]"><img src="/figures/table1_detection_clean.png" /></div>
    </div>
    <div class="grid gap-5">
      <div class="hover-card p-5" v-click><div class="metric">91.81%</div><div class="muted">Average Image-AUC</div></div>
      <div class="hover-card p-5" v-click><div class="metric">95.61%</div><div class="muted">Average Pixel-AUC</div></div>
      <div class="hover-card p-5" v-click><div class="metric">85.80%</div><div class="muted">Average AP</div></div>
      <div class="hover-card p-5 bg-blue-50" v-click><b>Interpretation:</b> feature enhancement + detection head improve visual precision.</div>
    </div>
  </div>
</div>

---
title: Q&A Results
---

<div class="h-full grid grid-cols-[.95fr_1.05fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Quantitative Result 2</div>
    <h1 class="text-[3rem] mb-6">FabGPT maintains strong Q&A ability across defect and general questions.</h1>
    <div class="card p-6 grid grid-cols-2 gap-5">
      <div class="hover-card p-5"><div class="metric">97.50%</div><div class="muted">Defect analysis</div></div>
      <div class="hover-card p-5"><div class="metric">98.00%</div><div class="muted">Unrelated Q&A</div></div>
      <div class="hover-card p-5"><div class="metric">96.86%</div><div class="muted">Overall accuracy</div></div>
      <div class="hover-card p-5"><div class="metric">+78%</div><div class="muted">vs. Lisa on unrelated Q&A</div></div>
    </div>
  </div>
  <div class="hover-card p-5">
    <div class="visual-frame h-[510px]"><img src="/figures/table2_qa_clean.png" /></div>
  </div>
</div>

---
title: Qualitative Visual Results
---

<div class="h-full grid grid-rows-[auto_1fr] gap-5">
  <div>
    <div class="kicker mb-3">Qualitative Results</div>
    <h1 class="text-[2.8rem]">The visual results show more focused defect localization.</h1>
  </div>
  <div class="grid grid-cols-2 gap-8">
    <div class="hover-card p-5">
      <h2 class="text-2xl mb-3">Non-LMM baselines</h2>
      <div class="visual-frame h-[420px]"><img src="/figures/fig5_non_lmm_clean.png" /></div>
    </div>
    <div class="hover-card p-5">
      <h2 class="text-2xl mb-3">LMM-based baselines</h2>
      <div class="visual-frame h-[420px]"><img src="/figures/fig6_lmm_clean.png" /></div>
    </div>
  </div>
</div>

---
title: Dialogue Example
---

<div class="h-full grid grid-cols-[1.02fr_.98fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Dialogue Example</div>
    <h1 class="text-[3rem] mb-6">FabGPT can answer both image-grounded and general IC questions.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>Image-grounded:</b> Are there any defects? Where are they?</div>
      <div class="hover-card p-5" v-click><b>Root cause:</b> What caused this defect?</div>
      <div class="hover-card p-5" v-click><b>General IC knowledge:</b> What are the core IC manufacturing steps?</div>
    </div>
  </div>
  <div class="hover-card p-5">
    <div class="visual-frame h-[510px]"><img src="/figures/fig7_dialogue_clean.png" /></div>
  </div>
</div>

---
title: Ablation Study
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Ablation Study</div>
    <h1 class="text-[3rem] mb-6">Each component contributes to detection, Q&A, or bias mitigation.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b>PM</b> improves Pixel-AUC and defect-related Q&A.</div>
      <div class="hover-card p-5" v-click><b>Pre-trained experts</b> provide a large gain in the enhancement stage.</div>
      <div class="hover-card p-5" v-click><b>Corrector</b> is critical for alleviating modality bias.</div>
    </div>
  </div>
  <div class="grid gap-5">
    <div class="hover-card p-4"><div class="visual-frame h-[230px]"><img src="/figures/table3_ablation_clean.png" /></div></div>
    <div class="hover-card p-4"><div class="visual-frame h-[300px]"><img src="/figures/table4_5_ablation_clean.png" /></div></div>
  </div>
</div>

---
title: Strengths and Limitations
---

<div class="h-full grid grid-cols-[1fr_1fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Critical Evaluation</div>
    <h1 class="text-[3rem] mb-6">The contribution is strong, but deployment evidence is still limited.</h1>
    <div class="grid gap-4">
      <div class="hover-card p-5" v-click><b class="text-blue-700">Strength:</b> integrates detection, localization, root-cause analysis, and Q&A.</div>
      <div class="hover-card p-5" v-click><b class="text-blue-700">Strength:</b> explicitly tackles modality bias, not just segmentation accuracy.</div>
      <div class="hover-card p-5" v-click><b class="text-slate-700">Question:</b> SEM-WaD is in-house, so external generalization is not fully verified.</div>
      <div class="hover-card p-5" v-click><b class="text-slate-700">Question:</b> real fab deployment needs latency, reliability, and human validation analysis.</div>
    </div>
  </div>
  <div class="card p-8 grid grid-cols-2 gap-5 text-center">
    <div class="hover-card p-7"><div class="metric-sm mb-3">Novel</div><b>End-to-end query interface</b></div>
    <div class="hover-card p-7"><div class="metric-sm mb-3">Strong</div><b>Detection and Q&A metrics</b></div>
    <div class="hover-card p-7"><div class="metric-sm mb-3">Risk</div><b>Private dataset</b></div>
    <div class="hover-card p-7"><div class="metric-sm mb-3">Gap</div><b>Real fab validation</b></div>
  </div>
</div>

---
title: Final Takeaways
---

<div class="h-full flex flex-col justify-center">
  <div class="kicker mb-4">Final Takeaways</div>
  <h1 class="text-[3.35rem] mb-8">FabGPT is best understood as a wafer-defect knowledge interface, not only a detector.</h1>
  <div class="grid grid-cols-3 gap-6">
    <div class="hover-card p-7" v-click><div class="num mb-5">1</div><h2 class="text-2xl">Problem</h2><p class="muted mt-3">Wafer defect analysis requires both visual precision and domain reasoning.</p></div>
    <div class="hover-card p-7" v-click><div class="num mb-5">2</div><h2 class="text-2xl">Method</h2><p class="muted mt-3">FabGPT uses modal enhancement, detection, and Q&A stages.</p></div>
    <div class="hover-card p-7" v-click><div class="num mb-5">3</div><h2 class="text-2xl">Evidence</h2><p class="muted mt-3">Experiments show strong detection metrics and reduced modality bias.</p></div>
  </div>
  <div class="mt-9 hover-card p-6 text-center text-2xl font-750">
    Discussion question: How should a fab engineer validate FabGPT before using it in production?
  </div>
</div>

---
title: Thank You
---

<div class="h-full grid grid-cols-[.88fr_1.12fr] gap-10 items-center">
  <div>
    <div class="kicker mb-4">Backup / Q&A</div>
    <h1 class="text-[3.2rem] mb-6">Thank you</h1>
    <p class="text-xl muted leading-relaxed">Suggested discussion topics: dataset generalization, modality bias, and human-in-the-loop fab decision support.</p>
  </div>
  <div class="hover-card p-6">
    <div class="visual-frame h-[520px]"><img src="/figures/paper_title_clean.png" /></div>
  </div>
</div>
