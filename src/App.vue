<script setup lang="ts">
import '@fontsource/caveat/700.css'
import '@fontsource/playfair-display/600.css'
import '@fontsource/playfair-display/700.css'
import { ImgComparisonSlider } from '@img-comparison-slider/vue'
import { ref } from 'vue'

const currentSlide = ref(0)
const imageSlides = [
  { label: 'Greenhouse', first: '/TIGER_project_page/compare/GreenHouse/lq.png', second: '/TIGER_project_page/compare/GreenHouse/sr.png' },
  { label: 'Projector', first: '/TIGER_project_page/compare/Projector/lq.png', second: '/TIGER_project_page/compare/Projector/sr.png' },
  { label: 'Multilingual', first: '/TIGER_project_page/compare/Multilingual/lq.png', second: '/TIGER_project_page/compare/Multilingual/sr.png' },
  { label: 'Shop sign', first: '/TIGER_project_page/compare/Shoppingsign/lq.png', second: '/TIGER_project_page/compare/Shoppingsign/sr.png' },
  { label: 'Manual', first: '/TIGER_project_page/compare/Manual1/lq.png', second: '/TIGER_project_page/compare/Manual1/sr.png' },
  { label: 'Washing', first: '/TIGER_project_page/compare/Washing/lq.png', second: '/TIGER_project_page/compare/Washing/sr.png' },
  { label: 'Traffic', first: '/TIGER_project_page/compare/Traffic/lq.png', second: '/TIGER_project_page/compare/Traffic/sr.png' },
  { label: 'Uniqlo', first: '/TIGER_project_page/compare/Uniqlo0/lq.png', second: '/TIGER_project_page/compare/Uniqlo0/sr.png' },
]

function moveSlide(direction: number) {
  currentSlide.value = (currentSlide.value + direction + imageSlides.length) % imageSlides.length
}
</script>

<template>
  <main>
    <section class="hero">
      <div class="hero-mark"><img src="/tiger-mascot.png" alt="TIGER mascot" /> TIGER</div>
      <p class="eyebrow">CVPR 2026 · Scene Text Image Super-Resolution</p>
      <h1>Restore Text First,<br><em>Enhance Image Later.</em></h1>
      <p class="subtitle">Two-stage scene text image super-resolution with glyph structure guidance.</p>

      <p class="authors">
        Minxing Luo<sup>1,2,*</sup> · Linlong Fan<sup>2,*</sup> · Qiushi Wang<sup>2,3</sup> · Ge Wu<sup>1</sup> ·
        Yiyan Luo<sup>2</sup> · Yuhang Yu<sup>2</sup> · Jinwei Chen<sup>2</sup> · Yaxing Wang<sup>1,4</sup> ·
        Qingnan Fan<sup>2,†</sup> · Jian Yang<sup>1,5,†</sup>
      </p>
      <p class="affiliations"><sup>1</sup>PCA Lab, VCIP, College of Computer Science, Nankai University &nbsp; <sup>2</sup>vivo BlueImage Lab, vivo Mobile Communication Co., Ltd. &nbsp; <sup>3</sup>SDS, CUHK, Shenzhen &nbsp; <sup>4</sup>NKIARI, Shenzhen Futian &nbsp; <sup>5</sup>PCA Lab, School of Intelligence Science and Technology, Nanjing University</p>

      <nav class="actions" aria-label="Project resources">
        <a href="https://openaccess.thecvf.com/content/CVPR2026/html/Luo_Restore_Text_First_Enhance_Image_Later_Two-Stage_Scene_Text_Image_CVPR_2026_paper.html" target="_blank" rel="noreferrer">Paper ↗</a>
        <a href="https://arxiv.org/abs/2510.21590" target="_blank" rel="noreferrer">arXiv ↗</a>
        <a href="https://github.com/OpenVeraTeam/TiGeSR" target="_blank" rel="noreferrer">Code ↗</a>
        <a href="https://huggingface.co/mxluocv/TiGeSR" target="_blank" rel="noreferrer">Models ↗</a>
        <a href="https://huggingface.co/datasets/mxluocv/UZ-ST" target="_blank" rel="noreferrer">UZ-ST ↗</a>
      </nav>
    </section>

    <section class="comparison-band" aria-label="Interactive visual comparisons">
      <div class="section-kicker">Drag the divider</div>
      <div class="comparison-head">
        <h2>Read the text. Keep the scene.</h2>
        <span>{{ imageSlides[currentSlide].label }}</span>
      </div>
      <div class="comparison-shell">
        <button class="arrow left" type="button" aria-label="Previous comparison" @click="moveSlide(-1)">←</button>
        <ImgComparisonSlider class="comparison-slider">
          <img slot="first" :src="imageSlides[currentSlide].first" alt="Low-quality input" />
          <img slot="second" :src="imageSlides[currentSlide].second" alt="TiGeSR restoration" />
        </ImgComparisonSlider>
        <button class="arrow right" type="button" aria-label="Next comparison" @click="moveSlide(1)">→</button>
      </div>
      <div class="comparison-caption"><span>Low-quality input</span><strong>TiGeSR</strong></div>
      <div class="dots" role="tablist" aria-label="Comparison samples">
        <button v-for="(slide, index) in imageSlides" :key="slide.label" type="button" :class="{ active: index === currentSlide }" :aria-label="`Show ${slide.label}`" @click="currentSlide = index" />
      </div>
    </section>

    <section class="statement section-wrap">
      <p class="section-kicker">Why TIGER</p>
      <h2>Text is not a texture.</h2>
      <p>Generative image SR can sharpen a scene while corrupting the characters that matter most. Text SR improves readability, but often loses the image context. TIGER resolves this conflict by treating glyph restoration as a first-class task, then using its restored structure to guide image enhancement.</p>
    </section>

    <section class="method section-wrap">
      <div class="method-copy">
        <p class="section-kicker">The two-stage framework</p>
        <h2>Recover glyphs before pixels.</h2>
        <div class="steps">
          <article>
            <span>01</span>
            <h3>Text restoration</h3>
            <p>OCR and a glyph-structure restoration model reconstruct legible text regions and assemble them into a full-resolution text mask.</p>
          </article>
          <article>
            <span>02</span>
            <h3>Image enhancement</h3>
            <p>A ControlNet-like image enhancer conditions on the low-resolution image and restored glyph mask to preserve both scene realism and readable text.</p>
          </article>
        </div>
      </div>
      <figure class="paper-figure">
        <img src="/TIGER_files/overview.png" alt="Overview of the two-stage TIGER framework" />
      </figure>
    </section>

    <section class="dataset section-wrap">
      <div>
        <p class="section-kicker">UZ-ST benchmark</p>
        <h2>Extreme zoom, real-world text.</h2>
        <p>UZ-ST (UltraZoom Scene Text) is captured with four fixed focal lengths—14 mm, 35 mm, 85 mm, and 200 mm—enabling challenging real-world scene-text pairs at up to ×14.29 zoom.</p>
      </div>
      <div class="stats">
        <div><strong>5,036</strong><span>aligned image pairs</span></div>
        <div><strong>49,675</strong><span>text lines</span></div>
        <div><strong>×14.29</strong><span>maximum zoom</span></div>
      </div>
      <figure class="wide-figure"><img src="/TIGER_files/datapipe.png" alt="UZ-ST data collection and alignment pipeline" /></figure>
      <figure class="wide-figure"><img src="/TIGER_files/datasamples.png" alt="Examples from the UZ-ST dataset" /></figure>
    </section>

    <section class="results section-wrap">
      <p class="section-kicker">Results</p>
      <h2>Better image quality. Better text accuracy.</h2>
      <p>TIGER consistently improves reconstruction quality and text recognition accuracy on Real-CE and UZ-ST, especially in challenging long-range, multilingual, and severely degraded scenes.</p>
      <div class="results-grid">
        <figure><img src="/TIGER_files/Quantitative_Comparisons.png" alt="Quantitative results" /></figure>
        <figure><img src="/TIGER_files/Quantitative_Comparisons_1.png" alt="Quantitative results on cropped images" /></figure>
      </div>
      <figure class="wide-figure"><img src="/TIGER_files/Visual_Comparison.png" alt="Visual comparisons with previous methods" /></figure>
      <figure class="wide-figure"><img src="/TIGER_files/Visual_Comparison_1.png" alt="Additional visual comparisons" /></figure>
    </section>

    <section class="citation section-wrap">
      <p class="section-kicker">Citation</p>
      <h2>Reference</h2>
      <pre><code>@inproceedings{luo2026restore,
  title={Restore text first, enhance image later: Two-stage scene text image super-resolution with glyph structure guidance},
  author={Luo, Minxing and Fan, Linlong and Wang, Qiushi and Wu, Ge and Luo, Yiyan and Yu, Yuhang and Chen, Jinwei and Wang, Yaxing and Fan, Qingnan and Yang, Jian},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={30553--30563},
  year={2026}
}</code></pre>
    </section>

    <footer>Built for <strong>TIGER</strong> · Restore text first, enhance image later.</footer>
  </main>
</template>

<style scoped>
:global(*) { box-sizing: border-box; }
:global(body) { margin: 0; background: #f5f0e6; color: #1c1a17; }
main { overflow: hidden; font-family: Georgia, 'Times New Roman', serif; }
.hero { position: relative; padding: 5.5rem 1.5rem 4.5rem; text-align: center; background: radial-gradient(circle at 50% -10%, #fff8dc 0, #f5f0e6 55%, #e6dccb 100%); border-bottom: 1px solid #c8b89e; }
.hero::before { content: ''; position: absolute; inset: 0; pointer-events: none; opacity: .25; background-image: linear-gradient(30deg, transparent 47%, #cf6f2e 48%, #cf6f2e 50%, transparent 51%), linear-gradient(150deg, transparent 47%, #cf6f2e 48%, #cf6f2e 50%, transparent 51%); background-size: 54px 94px; mask-image: linear-gradient(to bottom, black, transparent 65%); }
.hero > * { position: relative; }
.hero-mark { display: inline-flex; align-items: center; gap: .35rem; padding: .18rem .8rem .18rem .25rem; border: 1px solid #bd642a; color: #bd642a; font-family: 'Caveat', cursive; font-size: 1.65rem; letter-spacing: .06em; background: #fff8e7cc; transform: rotate(-2deg); }
.hero-mark img { width: 38px; height: 38px; border-radius: 50%; object-fit: cover; }
.eyebrow, .section-kicker { margin: 1.5rem 0 .65rem; color: #a84f1d; font-size: .72rem; font-family: 'Caveat', cursive; font-weight: 700; letter-spacing: .17em; text-transform: uppercase; }
h1, h2, h3, p { margin-top: 0; }
h1 { max-width: 980px; margin: 0 auto; font-family: 'Playfair Display', Georgia, serif; font-size: clamp(2.7rem, 7vw, 5.8rem); line-height: .96; letter-spacing: -.055em; }
h1 em { color: #b95620; font-weight: 600; }
.subtitle { max-width: 640px; margin: 1.3rem auto 1.1rem; font-size: clamp(1rem, 2vw, 1.28rem); line-height: 1.55; }
.authors { max-width: 1000px; margin: 1rem auto .35rem; font-size: .94rem; line-height: 1.85; }
.authors sup, .affiliations sup { color: #ae531e; font-weight: 700; }
.affiliations { margin: 0 auto; font-size: .85rem; color: #5f564c; }
.actions { display: flex; flex-wrap: wrap; justify-content: center; gap: .65rem; margin-top: 1.75rem; }
.actions a { padding: .65rem .9rem; color: #fffaf0; background: #26221d; border: 1px solid #26221d; text-decoration: none; font-family: 'Caveat', cursive; font-size: 1.08rem; letter-spacing: .03em; transition: transform .2s ease, background .2s ease; }
.actions a:hover { transform: translateY(-3px) rotate(-1deg); background: #bd642a; border-color: #bd642a; }
.comparison-band { padding: 3.2rem 1.25rem 2.3rem; background: #20221e; color: #f8f0e2; }
.comparison-band .section-kicker { margin-top: 0; color: #f4a453; text-align: center; }
.comparison-head { display: flex; max-width: 1040px; margin: 0 auto 1.2rem; align-items: baseline; justify-content: space-between; gap: 1rem; }
.comparison-head h2 { margin: 0; font-family: 'Playfair Display', Georgia, serif; font-size: clamp(1.8rem, 4vw, 3rem); letter-spacing: -.04em; }
.comparison-head span { color: #f4a453; font-family: 'Caveat', cursive; font-size: 1.5rem; }
.comparison-shell { display: flex; align-items: center; justify-content: center; max-width: 1160px; margin: 0 auto; }
.comparison-slider { width: min(900px, 78vw); border: 2px solid #f4a453; background: #111; }
.comparison-slider img { display: block; width: 100%; max-width: 100%; height: min(50vw, 430px); object-fit: contain; object-position: center; }
.arrow { width: 50px; height: 50px; margin: 0 -9px; border: 1px solid #f4a453; color: #f4a453; background: #20221e; font-size: 1.5rem; cursor: pointer; z-index: 1; transition: all .2s ease; }
.arrow:hover { color: #20221e; background: #f4a453; }
.comparison-caption { display: flex; justify-content: space-between; width: min(900px, 78vw); margin: .75rem auto 0; color: #cfc7b9; font-size: .88rem; }
.comparison-caption strong { color: #f4a453; }
.dots { display: flex; justify-content: center; gap: .45rem; margin-top: 1rem; }
.dots button { width: 8px; height: 8px; padding: 0; border: 0; border-radius: 999px; background: #69645b; cursor: pointer; transition: all .2s ease; }
.dots button.active { width: 28px; background: #f4a453; }
.section-wrap { width: min(1120px, calc(100% - 2.5rem)); margin: 0 auto; padding: 5.5rem 0; }
.statement { max-width: 830px; text-align: center; }
.statement h2, .method h2, .dataset h2, .results h2, .citation h2 { margin-bottom: 1rem; font-family: 'Playfair Display', Georgia, serif; font-size: clamp(2.2rem, 5vw, 4rem); line-height: 1; letter-spacing: -.05em; }
.statement p:last-child, .dataset p, .results > p { font-size: 1.12rem; line-height: 1.7; color: #51483f; }
.method { display: grid; grid-template-columns: .9fr 1.1fr; gap: 3.5rem; align-items: center; border-top: 1px solid #d7cbb9; }
.steps { margin-top: 2rem; border-left: 1px solid #cbbba5; }
.steps article { padding: .1rem 0 1.25rem 1.4rem; position: relative; }
.steps article::before { content: ''; position: absolute; width: 9px; height: 9px; left: -5px; top: .43rem; border-radius: 50%; background: #c45d24; }
.steps span { color: #bd642a; font-family: 'Caveat', cursive; font-size: 1.4rem; }
.steps h3 { margin: .1rem 0 .25rem; font-family: 'Playfair Display', Georgia, serif; font-size: 1.45rem; }
.steps p { margin: 0; color: #5a5046; line-height: 1.6; }
.paper-figure, .wide-figure { margin: 0; }
.paper-figure img, .wide-figure img, .results-grid img { display: block; width: 100%; border: 1px solid #d6c7b1; background: #fff; }
.dataset { border-top: 1px solid #d7cbb9; }
.stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px; margin: 2.3rem 0; background: #c9b99f; border: 1px solid #c9b99f; }
.stats div { display: grid; gap: .25rem; padding: 1.3rem; background: #fffaf0; }
.stats strong { color: #b85620; font-family: 'Playfair Display', Georgia, serif; font-size: clamp(1.7rem, 4vw, 3rem); letter-spacing: -.04em; }
.stats span { color: #695e53; font-size: .83rem; text-transform: uppercase; letter-spacing: .07em; }
.dataset .wide-figure + .wide-figure { margin-top: 1.5rem; }
.results { border-top: 1px solid #d7cbb9; text-align: center; }
.results > p { max-width: 730px; margin: 0 auto 2rem; }
.results-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.25rem; margin-bottom: 1.25rem; text-align: left; }
.results .wide-figure + .wide-figure { margin-top: 1.4rem; }
.citation { border-top: 1px solid #d7cbb9; }
.citation pre { overflow-x: auto; margin: 1.5rem 0 0; padding: 1.35rem; background: #26221d; color: #f6e7cb; border-left: 5px solid #c45d24; font-family: 'Courier New', monospace; font-size: .82rem; line-height: 1.55; }
footer { padding: 2rem 1rem; text-align: center; color: #f2dfbf; background: #26221d; font-size: .9rem; }
footer strong { color: #f49c46; font-family: 'Caveat', cursive; font-size: 1.35rem; }
@media (max-width: 760px) { .hero { padding-top: 3.6rem; } .method { grid-template-columns: 1fr; gap: 2rem; } .comparison-shell { width: 100%; } .comparison-slider { width: calc(100vw - 88px); } .comparison-caption { width: calc(100vw - 88px); } .arrow { width: 42px; height: 42px; } .stats, .results-grid { grid-template-columns: 1fr; } .section-wrap { padding: 3.8rem 0; } .authors { font-size: .83rem; } }
</style>
