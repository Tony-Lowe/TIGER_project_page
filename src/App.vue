<script setup lang="ts">
import { ImgComparisonSlider } from '@img-comparison-slider/vue'
import { onMounted, ref } from 'vue';

// 轮播相关状态
const currentSlide = ref(0);
const imageSlides = [
  {
    first: "/TIGER_project_page/compare/GreenHouse/lq.png",
    second: "/TIGER_project_page/compare/GreenHouse/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Projector/lq.png",
    second: "/TIGER_project_page/compare/Projector/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Multilingual/lq.png",
    second: "/TIGER_project_page/compare/Multilingual/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Shoppingsign/lq.png",
    second: "/TIGER_project_page/compare/Shoppingsign/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Manual1/lq.png",
    second: "/TIGER_project_page/compare/Manual1/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Washing/lq.png",
    second: "/TIGER_project_page/compare/Washing/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Shoppingsign/lq.png",
    second: "/TIGER_project_page/compare/Shoppingsign/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Manual0/lq.png",
    second: "/TIGER_project_page/compare/Manual0/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Traffic/lq.png",
    second: "/TIGER_project_page/compare/Traffic/sr.png"
  },
  {
    first: "/TIGER_project_page/compare/Uniqlo0/lq.png",
    second: "/TIGER_project_page/compare/Uniqlo0/sr.png"
  }
];

// 切换到上一张
const prevSlide = () => {
  currentSlide.value = currentSlide.value > 0 ? currentSlide.value - 1 : imageSlides.length - 1;
};

// 切换到下一张
const nextSlide = () => {
  currentSlide.value = currentSlide.value < imageSlides.length - 1 ? currentSlide.value + 1 : 0;
};

onMounted(() => {
  // 确保MathJax已加载并渲染公式
  if (window.MathJax) {
    window.MathJax.typeset(); // 重新渲染页面中的数学公式
  }
});
</script>

<template>

  <!-- <div class="content-title">
    <div style="display: flex; justify-content: center; align-items: center; height: auto;">
      <img src="/TADSR_files/TADSR.png" alt="" style="width: 170px;">
    </div> -->
    
  <h1 style="text-align: center; font-size: 30px; margin: 15px 0px 5px 0px;"><strong>Restore Text First, Enhance Image Later: Two-Stage Scene Text Image Super-Resolution with Glyph Structure Guidance</strong></h1>

  <p id="authors" style="text-align: center; margin: 10px 0px;">
    <a href="" style="font-size: 20px;" >Minxing Luo<sup>1,2,*</sup></a>, 
    <a href="" style="font-size: 20px;" >Linlong Fan<sup>2,*</sup></a>, 
    <a href="" style="font-size: 20px;" >Wang Qiushi<sup>2,3</sup></a>, 
    <a href="" style="font-size: 20px;" >Ge Wu<sup>1</sup></a>,<br>
    <a href="" style="font-size: 20px;" >Yiyan Luo<sup>2</sup></a>,
    <a href="" style="font-size: 20px;" >Jinwei Chen<sup>2</sup></a>,
    <a href="https://yaxingwang.github.io/" style="font-size: 20px;" >Yaxing Wang<sup>1</sup></a>,
    <a href="https://fqnchina.github.io/" style="font-size: 20px;" >Qingnan Fan<sup>2,&dagger;</sup></a>,
    <a href="" style="font-size: 20px;">Jian Yang<sup>1,&dagger;</sup></a>
    <br>
    <span style="font-size: 18px; font-weight: bold; ;"><sup>1</sup>VCIP, CS, Nankai University. </span> &nbsp;&nbsp;
    <span style="font-size: 18px; font-weight: bold; ;"><sup>2</sup>vivo Mobile Communication Co. Ltd.</span> 
    <span style="font-size: 18px; font-weight: bold; ;"><sup>*;</sup>Corresponding author.</span>
    <br>
    <span style="font-size: 18px; font-weight: bold; ;"><sup>3</sup>SDS, The Chinese University of Hong Kong, Shenzhen.</span> &nbsp;&nbsp;
    <span style="font-size: 18px; font-weight: bold; ;"><sup>&dagger;</sup>Corresponding author.</span> <br>

  </p>

  <div class="button-container">
    <a href="https://arxiv.org/" target="_blank" class="custom-button">
      <svg class="arxiv-icon" viewBox="0 0 448 512" xmlns="http://www.w3.org/2000/svg" style="margin-right: 5px;"> 
        <path
         fill="currentColor"
         d="m 119.65,351.996 c -5.84961,0.13477 -11.1943,-3.29883 -13.502,-8.67578 -2.19629,-5.27051 -0.61914,-8.9668 4.19727,-15.8652 7.05469,-10.3799 78.8242,-96.5625 78.8242,-96.5625 l -15.8828,-14.8633 c -13.3809,-13.3779 -13.9561,-31.333 -1.50977,-43.7754 l 18.4922,-17.6133 -51.5977,-63.377 c -4.00586,-4.26758 -6.48535,-11.7559 -4.24805,-17.1309 2.27832,-5.53613 7.69727,-9.12891 13.6836,-9.07031 3.83398,0.0957 7.43262,1.87402 9.83789,4.86133 l 61.3691,57.0566 94.5762,-90.0703 c 3.19434,-3.08398 7.44336,-4.83984 11.8828,-4.91016 1.60449,0.0039 3.19824,0.245117 4.73242,0.714844 5.7793,1.80566 10.249,6.41797 11.8711,12.252 1.2998,5.47363 -0.27637,11.2334 -4.18164,15.2832 l -83.0859,100.011996 14.8789,13.834 c 11.0957,10.0029 11.1543,27.3906 0.12695,37.4688 l -16.2949,15.6309 56.2559,66.4434 0.0742,0.0859 0.0664,0.0899 c 5.02734,6.53125 7.43164,11.5615 4.83984,17.9395 -3.13379,5.96875 -8.69727,10.29 -15.2559,11.8516 -0.67676,0.0908 -1.35938,0.13574 -2.04297,0.13671 l -0.004,-0.0117 c -4.42871,-0.27051 -8.61035,-2.13086 -11.7754,-5.24023 l -0.13086,-0.10743 -0.12304,-0.11132 -65.207,-59.127 -89.8965,86.2402 c 0,0 -5.33398,6.47754 -10.9707,6.61133 z m 178.104,-33.041 c 0.47852,-0.002 0.95703,-0.0332 1.43164,-0.0957 4.84277,-1.33301 8.95605,-4.54004 11.4316,-8.91016 1.44922,-3.5625 1.00293,-6.45703 -4.19727,-13.2148 l -56.0586,-66.2188 -26.375,25.3027 64.9551,58.9062 c 2.33887,2.41504 5.46484,3.91113 8.8125,4.2168 v 0.0137 z M 192.436,227.402 334.446,57.244 c 2.78711,-3.48926 4.5293,-6.97949 3.3418,-10.9121 -1.16113,-4.30273 -4.43457,-7.71777 -8.68555,-9.05664 -1.08105,-0.333984 -2.20508,-0.503906 -3.33594,-0.505859 -3.20801,0.07617 -6.26953,1.35645 -8.57617,3.58789 l -142.033,135.284999 c -11.1719,11.1719 -9.48242,26.0195 1.39258,36.8945 z"
         id="path2"
         style="stroke-width:0.416233" />
      </svg>
      <span>arXiv</span>
    </a>
    &nbsp;&nbsp;
    <a href="https://github.com/Tony-Lowe/TIGER_project_page" target="_blank" class="custom-button">
      <span class="icon" style="margin-right: 10px;">
        <i class="fab fa-github"></i>
      </span>
      <span>Code (Coming Soon)</span>
    </a>
    &nbsp;&nbsp;
  </div>


  <!-- 轮播图像对比展示 -->
  <div class="carousel-container">
    <button class="carousel-btn prev-btn" @click="prevSlide">‹</button>
    <div class="carousel-slider">
      <ImgComparisonSlider>
        <img
          slot="first"
          style="height: 400px"
          :src="imageSlides[currentSlide].first"
        />
        <img
          slot="second"
          style="height: 400px"
          :src="imageSlides[currentSlide].second"
        />
      </ImgComparisonSlider>
    </div>
    <button class="carousel-btn next-btn" @click="nextSlide">›</button>
  </div>
  <div class="carousel-indicators">
    <span 
      v-for="(_, index) in imageSlides" 
      :key="index"
      :class="['indicator', { active: index === currentSlide }]"
      @click="currentSlide = index"
    ></span>
  </div>


  <div class="content-abstract">
    <h2 style="text-align:center;">Abstract</h2>
    <p>Current generative super-resolution methods show strong performance on natural images but distort text, creating a fundamental trade-off between image quality and textual readability. To address this, we introduce <strong>TIGER</strong> (<strong>T</strong>ext–<strong>I</strong>mage <strong>G</strong>uided sup<strong>E</strong>r-<strong>R</strong>esolution), a novel two-stage framework that breaks this trade-off through a <em>"text-first, image-later"</em> paradigm. TIGER explicitly decouples glyph restoration from image enhancement: it first reconstructs precise text structures and then uses them to guide subsequent full-image super-resolution. This glyph-to-image guidance ensures both high fidelity and visual consistency. To support comprehensive training and evaluation, we also contribute the <strong>UltraZoom-ST</strong> (UltraZoom-Scene Text), the first scene text dataset with extreme zoom (<strong>×14.29</strong>). Extensive experiments show that TIGER achieves <strong>state-of-the-art</strong> performance, enhancing readability while preserving overall image quality. </p>
  </div>
  <!-- <div class="content">
    <h2>Background</h2>
    <p> Given a particular subject such as clock (shown in the real images on the left), it is very challenging to generate it in different contexts with state-of-the-art text-to-image models, while maintaining high fidelity to its key visual features. Even with dozens of iterations over a text prompt that contains a detailed description of the appearance of the clock (<em>"retro style yellow alarm clock with a white clock face and a yellow number three on the right part of the clock face in the jungle"</em>), the Imagen model [Saharia et al., 2022] can't reconstruct its key visual features (third column). Furthermore, even models whose text embedding lies in a shared language-vision space and can create semantic variations of the image, such as DALL-E2 [Ramesh et al., 2022], can neither reconstruct the appearance of the given subject nor modify the context (second column). In contrast, our approach (right) can synthesize the clock with high fidelity and in new contexts (<em>"a [V] clock in the jungle"</em>).</p>
    <br>
    <img class="summary-img" src="/ DreamBooth_files/background.png" style="width:100%;"> <br>
  </div> -->
  <div class="content">
    <h2 style="text-align:center;">Method</h2>
    <p>Current image super-resolution methods focus on enhancing overall image quality but often fail to accurately preserve glyph structures, leading to distorted text in super-resolved images. 
    Conversely, text image super-resolution methods improve text readability but do not retain the global semantic information of the background, causing incoherence between text and non-text regions.
   </p>
    <br>
    <figure>
      <img src="/TIGER_files/overview.png" alt="Overview image" style="width: 100%;">
    </figure>
    <p>
  To leverage the strengths of both approaches, we introduce the TIGER framework.
  As illustrated in the pipeline figure, the TIGER framework is composed of two stages: the <strong>Text Restoration stage</strong> and the <strong>Image Enhancement stage</strong>.
  In the text restoration stage, we extract the text regions from the LR input \(x_{L} \in \mathbb{R}^{H \times W \times C}\) and feed them into the glyph structure restoration model to restore the text structure based on the text region of the LR input and the predicted text.
  We then reassemble the text structures to their original positions to obtain a text mask \(\hat{x}_{m} \in \mathbb{R}^{H \times W \times C}\).
  In the image enhancement stage, the text mask and LR input are then processed by a ControlNet-like network to obtain the enhanced SR output \(\hat{x}_{H} \in \mathbb{R}^{H \times W \times C}\).
    </p>
  </div>

  <div class="content">
    <h2 style="text-align:center;">Dataset and Benchmarks</h2>
    <p>Existing datasets offer only subtle degradation, making them insufficient for evaluating model robustness.
    To address the lack of both challenging and publicly available datasets tailored for scene text image super-resolution, especially for Chinese text, we introduce <strong>UltraZoom-ST</strong>, a challenging real-world benchmark.
   </p>
    <br>
    <figure>
      <img src="/TIGER_files/datapipe.png" alt="Overview of UltraZoom-ST. (a) Real-CE LRs show only mild degradation (red box), while UltraZoom-ST LRs exhibit stronger degradation (red box), enabling a more comprehensive evaluation. (b) Coarse-to-fine alignment: images are sorted by focal length, each warped to the next higher-focal neighbor using an estimated homography matrix, then refined to the 200 mm ground truth." style="width: 100%;">
    </figure>
    <figure>
      <img src="/TIGER_files/datasamples.png" alt="Overview image" style="width: 100%;">
    </figure>
    <p>
    It is collected using ViVO X200 Ultra equipped with four fixed focal lengths (14 mm, 35 mm, 85 mm, 200 mm), enabling image pairs with extreme ×14.29 zoom.
    However, such extreme zoom introduces severe misalignment that breaks registration methods, originally designed for moderate ×2 to ×4 zoom.
    To overcome this, we design a <strong>Cascade Coarse-to-fine Alignment</strong> pipeline: images are first sorted by focal length, and each low-quality image is sequentially aligned to its next higher-focal neighbor using either optimization-based registration or feature-based extractors (e.g., SIFT, SURF, RIPE), then refined against the 200 mm ground truth for precise alignment.
    Through meticulous annotating and aligning, we obtained a total of 5,036 image pairs, with 49,675 lines of text.
    We set images under 200 mm focal length as ground truth, and obtain 1,439, 1,798, and 1,799 pairs for ×14.29, ×5.71, and ×2.35 zooming modes, respectively.
    Among them, we randomly select 470, 589, and 581 pairs for evaluation under each zooming mode.
    Each image pair contains one or more text lines.
    These evaluation sets enable us to evaluate the performance of models under more complex and challenging scenarios.
    </p>
  </div>

  <div class="content">
    <h2 style="text-align:center;">Results</h2>
    <h2>Quantitative Comparisons</h2>
    <figure>
      <img src="/TIGER_files/Quantitative_Comparisons.png" alt="Quantitative_Comparisons" style="width: 100%;">
    </figure>
    <figure>
      <img src="/TIGER_files/Quantitative_Comparisons_1.png" alt="Quantitative_Comparisons on Cropped Images" style="width: 100%;">
    </figure>
    <p>
      TIGER outperforms competing methods on both the Real-CE and UltraZoom-ST benchmarks in terms of image quality and text accuracy, owing to the decoupling strategy.
    </p>
    <h2>Visual Comparisons</h2>
    <figure>
      <img src="/TIGER_files/Visual_Comparison.png" alt="Real-world-result" style="width: 100%;">
    </figure>
    <figure>
      <img src="/TIGER_files/Visual_Comparison_1.png" alt="Additional-Real-world-result" style="width: 100%;">
    </figure>
      Compared to other SD-based Real-ISR methods,TADSR consistently produces clearer, more realistic,and more natural results, demonstrating its stronger image restoration capability while preserving fidelity.
  </div>


<!-- <div class="content">
  <h4>BibTex</h4>
  <pre class="bibtex-code">
    <code>
      @misc{zhang2025timeawarestepdiffusionnetwork,
        title={Time-Aware One Step Diffusion Network for Real-World Image Super-Resolution}, 
        author={Tainyi Zhang and Zheng-Peng Duan and Peng-Tao Jiang and Bo Li and Ming-Ming Cheng and Chun-Le Guo and Chongyi Li},
        year={2025},
        eprint={2508.16557},
        archivePrefix={arXiv},
        primaryClass={eess.IV},
        url={https://arxiv.org/abs/2508.16557}, 
      }
    </code>
  </pre>
</div> -->


  <footer class="footer">
    <div class="container">
      <div class="columns is-centered">
        <!-- <div class="column is-8"> -->
            <p>
              This website's source code is borrowed from the <a
              href="https://github.com/zty557/TADSR_HomePage">TADSR</a> project page.
            </p>
        <!-- </div> -->
      </div>
    </div>
  </footer>

</template>

<style scoped>

.row {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}
.row img-comparison-slider {
  flex: 1;
}

/* 轮播容器样式 */
.carousel-container {
  width: 1000px;
  margin: 25px auto;
  border-radius: 10px;
  padding: 20px 20px 35px 20px;
  background: rgb(244, 244, 244);
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel-slider {
  display: flex; 
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  position: relative;
}

.carousel-btn {
  /* position: absolute; */
  position: relative;
  top: 30px;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 24px;
  cursor: pointer;
  border-radius: 5px;
  z-index: 10;
  transition: background 0.3s ease;
}

.carousel-btn:hover {
  background: rgba(0, 0, 0, 0.8);
}

.prev-btn {
  position: relative;
  left: 120px;
}

.next-btn {
  position: relative;
  right: 120px;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 15px;
  position: relative;
  bottom: 45px;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #ccc;
  cursor: pointer;
  transition: background 0.3s ease;
}

.indicator.active {
  background: #224b8d;
}

.indicator:hover {
  background: #555;
}

a, a:visited {
  color: #224b8d;
  font-weight: 300;
}

.button-container a:visited{
  color: #FFF; 
}

.content img {
  display: inline-block; /* 保持图片为行内块元素 */
}
.content-abstract {
  font-size: 18px;
  width: 750px;
  padding: 25px 50px;
  margin: 25px auto;
  background-color: white;
  /* box-shadow: 0px 0px 10px #999; */
  border-radius: 15px;
  font-family: "Times New Roman", serif;
  color: #333;
}
.content {
  font-size: 18px;
  width: 950px;
  padding: 25px 50px;
  margin: 25px auto;
  background-color: white;
  /* box-shadow: 0px 0px 10px #999; */
  border-radius: 15px;
  font-family: "Times New Roman", serif;
  color: #333;
}
.content-title{
  font-size: 21px;
  width: 1400px;
  padding: 5px 10px;
  margin: 5px 0px;
  background-color: white;
  /* box-shadow: 0px 0px 10px #999; */
  border-radius: 15px;
  font-family: "Times New Roman", serif;
  color: #333;
  justify-content: center;
}
.button-container {
  display: flex;
  justify-content: center;
  font-size: 0.8em;
  margin-top: 15px;
}

.custom-button {
  width: 70px;
  display: inline-flex;
  align-items: center;
  background-color: #2e2e2e;
  color: white;
  border: none;
  border-radius: 999px;
  padding: 8px 16px;
  margin: 0 10px;
  text-decoration: none;
  font-family: sans-serif;
  font-weight: 500;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.custom-button:hover {
      background-color: #444;
}

.custom-button img {
      height: 18px;
      margin-right: 8px;
}

.arxiv-icon {
  width: auto;
  height: 24px;
  color: white;
  margin: 0 0 -7px 0;
}

/* 全局字体设置 */
* {
  font-family: "Times New Roman", serif;
}
</style>