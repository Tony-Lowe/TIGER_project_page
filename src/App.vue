<script setup lang="ts">
import { ImgComparisonSlider } from '@img-comparison-slider/vue'
import { onMounted, ref } from 'vue';

// 轮播相关状态
const currentSlide = ref(0);
const imageSlides = [
  {
    first: "/TADSR_HomePage/compare/147/lq.png",
    second: "/TADSR_HomePage/compare/147/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0166x4d/lq.png",
    second: "/TADSR_HomePage/compare/0166x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0263x4d/lq.png",
    second: "/TADSR_HomePage/compare/0263x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0338x4d/lq.png",
    second: "/TADSR_HomePage/compare/0338x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0035x4d/lq.png",
    second: "/TADSR_HomePage/compare/0035x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0007x4d/lq.png",
    second: "/TADSR_HomePage/compare/0007x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/0279x4d/lq.png",
    second: "/TADSR_HomePage/compare/0279x4d/sr.png"
  },
  {
    first: "/TADSR_HomePage/compare/151/lq.png",
    second: "/TADSR_HomePage/compare/151/sr.png"
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

  <div class="content-title">
    <div style="display: flex; justify-content: center; align-items: center; height: auto;">
      <img src="/TADSR_files/TADSR.png" alt="" style="width: 170px;">
    </div>
    
  <h1 style="text-align: center; font-size: 30px; margin: 15px 0px 5px 0px;"><strong>Time-Aware One Step Diffusion Network for Real-World Image Super-Resolution</strong></h1>

  <p id="authors" style="text-align: center; margin: 10px 0px;">
    <a href="" style="font-size: 20px;" >Tainyi Zhang<sup>1</sup></a>, 
    <a href="https://adam-duan.github.io/" style="font-size: 20px;" >Zheng-Peng Duan<sup>1</sup></a>, 
    <a href="" style="font-size: 20px;" >Peng-Tao Jiang<sup>2</sup></a>, 
    <a href="" style="font-size: 20px;" >Bo Li<sup>2</sup></a>,<br>
    <a href="" style="font-size: 20px;" >MingMing Cheng<sup>1</sup></a>,
    <a href="https://scholar.google.com/citations?user=RZLYwR0AAAAJ&hl=zh-CN&oi=ao" style="font-size: 20px;" >Chun-Le Guo<sup>1,3,&dagger;</sup></a>,
    <a href="https://li-chongyi.github.io/" style="font-size: 20px;">Chongyi Li<sup>1,3</sup></a>
    <br>
    <span style="font-size: 18px; font-weight: bold; ;"><sup>1</sup>VCIP, CS, Nankai University. </span> &nbsp;&nbsp;
    <span style="font-size: 18px; font-weight: bold; ;"><sup>2</sup>vivo Mobile Communication Co. Ltd.</span> <br>
    <span style="font-size: 18px; font-weight: bold; ;"><sup>3</sup>NKIARI, Shenzhen Futian.</span> &nbsp;&nbsp;
    <span style="font-size: 18px; font-weight: bold; ;"><sup>&dagger;</sup>Corresponding author.</span> <br>

  </p>

  <div class="button-container">
    <a href="https://arxiv.org/abs/2508.16557" target="_blank" class="custom-button">
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
    <a href="https://github.com/zty557/TADSR" target="_blank" class="custom-button">
      <span class="icon" style="margin-right: 10px;">
        <i class="fab fa-github"></i>
      </span>
      <span>Code</span>
    </a>
    &nbsp;&nbsp;
    <a href="" target="_blank" class="custom-button">
      <svg fill="currentColor" fill-rule="evenodd" height="1em" style="flex:none;line-height:1;margin-right: 3px;" viewBox="0 0 24 24" width="1em" xmlns="http://www.w3.org/2000/svg">
        <title>HuggingFace</title>
        <path d="M16.781 3.277c2.997 1.704 4.844 4.851 4.844 8.258 0 .995-.155 1.955-.443 2.857a1.332 1.332 0 011.125.4 1.41 1.41 0 01.2 1.723c.204.165.352.385.428.632l.017.062c.06.222.12.69-.2 1.166.244.37.279.836.093 1.236-.255.57-.893 1.018-2.128 1.5l-.202.078-.131.048c-.478.173-.89.295-1.061.345l-.086.024c-.89.243-1.808.375-2.732.394-1.32 0-2.3-.36-2.923-1.067a9.852 9.852 0 01-3.18.018C9.778 21.647 8.802 22 7.494 22a11.249 11.249 0 01-2.541-.343l-.221-.06-.273-.08a16.574 16.574 0 01-1.175-.405c-1.237-.483-1.875-.93-2.13-1.501-.186-.4-.151-.867.093-1.236a1.42 1.42 0 01-.2-1.166c.069-.273.226-.516.447-.694a1.41 1.41 0 01.2-1.722c.233-.248.557-.391.917-.407l.078-.001a9.385 9.385 0 01-.44-2.85c0-3.407 1.847-6.554 4.844-8.258a9.822 9.822 0 019.687 0zM4.188 14.758c.125.687 2.357 2.35 2.14 2.707-.19.315-.796-.239-.948-.386l-.041-.04-.168-.147c-.561-.479-2.304-1.9-2.74-1.432-.43.46.119.859 1.055 1.42l.784.467.136.083c1.045.643 1.12.84.95 1.113-.188.295-3.07-2.1-3.34-1.083-.27 1.011 2.942 1.304 2.744 2.006-.2.7-2.265-1.324-2.685-.537-.425.79 2.913 1.718 2.94 1.725l.16.04.175.042c1.227.284 3.565.65 4.435-.604.673-.973.64-1.709-.248-2.61l-.057-.057c-.945-.928-1.495-2.288-1.495-2.288l-.017-.058-.025-.072c-.082-.22-.284-.639-.63-.584-.46.073-.798 1.21.12 1.933l.05.038c.977.721-.195 1.21-.573.534l-.058-.104-.143-.25c-.463-.799-1.282-2.111-1.739-2.397-.532-.332-.907-.148-.782.541zm14.842-.541c-.533.335-1.563 2.074-1.94 2.751a.613.613 0 01-.687.302.436.436 0 01-.176-.098.303.303 0 01-.049-.06l-.014-.028-.008-.02-.007-.019-.003-.013-.003-.017a.289.289 0 01-.004-.048c0-.12.071-.266.25-.427.026-.024.054-.047.084-.07l.047-.036c.022-.016.043-.032.063-.049.883-.71.573-1.81.131-1.917l-.031-.006-.056-.004a.368.368 0 00-.062.006l-.028.005-.042.014-.039.017-.028.015-.028.019-.036.027-.023.02c-.173.158-.273.428-.31.542l-.016.054s-.53 1.309-1.439 2.234l-.054.054c-.365.358-.596.69-.702 1.018-.143.437-.066.868.21 1.353.055.097.117.195.187.296.882 1.275 3.282.876 4.494.59l.286-.07.25-.074c.276-.084.736-.233 1.2-.42l.188-.077.065-.028.064-.028.124-.056.081-.038c.529-.252.964-.543.994-.827l.001-.036a.299.299 0 00-.037-.139c-.094-.176-.271-.212-.491-.168l-.045.01c-.044.01-.09.024-.136.04l-.097.035-.054.022c-.559.23-1.238.705-1.607.745h.006a.452.452 0 01-.05.003h-.024l-.024-.003-.023-.005c-.068-.016-.116-.06-.14-.142a.22.22 0 01-.005-.1c.062-.345.958-.595 1.713-.91l.066-.028c.528-.224.97-.483.985-.832v-.04a.47.47 0 00-.016-.098c-.048-.18-.175-.251-.36-.251-.785 0-2.55 1.36-2.92 1.36-.025 0-.048-.007-.058-.024a.6.6 0 01-.046-.088c-.1-.238.068-.462 1.06-1.066l.209-.126c.538-.32 1.01-.588 1.341-.831.29-.212.475-.406.503-.6l.003-.028c.008-.113-.038-.227-.147-.344a.266.266 0 00-.07-.054l-.034-.015-.013-.005a.403.403 0 00-.13-.02c-.162 0-.369.07-.595.18-.637.313-1.431.952-1.826 1.285l-.249.215-.033.033c-.08.078-.288.27-.493.386l-.071.037-.041.019a.535.535 0 01-.122.036h.005a.346.346 0 01-.031.003l.01-.001-.013.001c-.079.005-.145-.021-.19-.095a.113.113 0 01-.014-.065c.027-.465 2.034-1.991 2.152-2.642l.009-.048c.1-.65-.271-.817-.791-.493zM11.938 2.984c-4.798 0-8.688 3.829-8.688 8.55 0 .692.083 1.364.24 2.008l.008-.009c.252-.298.612-.46 1.017-.46.355.008.699.117.993.312.22.14.465.384.715.694.261-.372.69-.598 1.15-.605.852 0 1.367.728 1.562 1.383l.047.105.06.127c.192.396.595 1.139 1.143 1.68 1.06 1.04 1.324 2.115.8 3.266a8.865 8.865 0 002.024-.014c-.505-1.12-.26-2.17.74-3.186l.066-.066c.695-.684 1.157-1.69 1.252-1.912.195-.655.708-1.383 1.56-1.383.46.007.889.233 1.15.605.25-.31.495-.553.718-.694a1.87 1.87 0 01.99-.312c.357 0 .682.126.925.36.14-.61.215-1.245.215-1.898 0-4.722-3.89-8.55-8.687-8.55zm1.857 8.926l.439-.212c.553-.264.89-.383.89.152 0 1.093-.771 3.208-3.155 3.262h-.184c-2.325-.052-3.116-2.06-3.156-3.175l-.001-.087c0-1.107 1.452.586 3.25.586.716 0 1.379-.272 1.917-.526zm4.017-3.143c.45 0 .813.358.813.8 0 .441-.364.8-.813.8a.806.806 0 01-.812-.8c0-.442.364-.8.812-.8zm-11.624 0c.448 0 .812.358.812.8 0 .441-.364.8-.812.8a.806.806 0 01-.813-.8c0-.442.364-.8.813-.8zm7.79-.841c.32-.384.846-.54 1.33-.394.483.146.83.564.878 1.06.048.495-.212.97-.659 1.203-.322.168-.447-.477-.767-.585l.002-.003c-.287-.098-.772.362-.925.079a1.215 1.215 0 01.14-1.36zm-4.323 0c.322.384.377.92.14 1.36-.152.283-.64-.177-.925-.079l.003.003c-.108.036-.194.134-.273.24l-.118.165c-.11.15-.22.262-.377.18a1.226 1.226 0 01-.658-1.204c.048-.495.395-.913.878-1.059a1.262 1.262 0 011.33.394z"></path>
      </svg>
      &nbsp;&nbsp;
      <span>Model</span>
    </a>
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

  </div>

  <div class="content-abstract">
    <h2 style="text-align:center;">Abstract</h2>
    <p>Diffusion-based real-world image super-resolution (Real-ISR) methods have demonstrated impressive performance. 
      To achieve efficient Real-ISR, many works employ Variational Score Distillation (VSD) to distill pre-trained stable-diffusion (SD) model for one-step SR with a fixed timestep. 
      However, due to the different noise injection timesteps, the SD will perform different generative priors. 
      Therefore, a fixed timestep is difficult for these methods to fully leverage the generative priors in SD, leading to suboptimal performance. 
      To address this, we propose a Time-Aware one-step Diffusion Network for Real-ISR (<strong>TADSR</strong>). 
      We first introduce a Time-Aware VAE Encoder, which projects the same image into different latent features based on timesteps. 
      Through joint dynamic variation of timesteps and latent features, the student model can better align with the input pattern distribution of the pre-trained SD, thereby enabling more effective utilization of SD's generative capabilities. 
      To better activate the generative prior of SD at different timesteps, we propose a Time-Aware VSD loss that bridges the timesteps of the student model and those of the teacher model, thereby producing more consistent generative prior guidance conditioned on timesteps. 
      Additionally, though utilizing the generative prior in SD at different timesteps, our method can naturally achieve controllable trade-offs between fidelity and realism by changing the timestep condition. Experimental results demonstrate that our method achieves both state-of-the-art performance and controllable SR results with only a single step. </p>
  </div>
  <!-- <div class="content">
    <h2>Background</h2>
    <p> Given a particular subject such as clock (shown in the real images on the left), it is very challenging to generate it in different contexts with state-of-the-art text-to-image models, while maintaining high fidelity to its key visual features. Even with dozens of iterations over a text prompt that contains a detailed description of the appearance of the clock (<em>"retro style yellow alarm clock with a white clock face and a yellow number three on the right part of the clock face in the jungle"</em>), the Imagen model [Saharia et al., 2022] can't reconstruct its key visual features (third column). Furthermore, even models whose text embedding lies in a shared language-vision space and can create semantic variations of the image, such as DALL-E2 [Ramesh et al., 2022], can neither reconstruct the appearance of the given subject nor modify the context (second column). In contrast, our approach (right) can synthesize the clock with high fidelity and in new contexts (<em>"a [V] clock in the jungle"</em>).</p>
    <br>
    <img class="summary-img" src="/ DreamBooth_files/background.png" style="width:100%;"> <br>
  </div> -->
  <div class="content">
    <h2 style="text-align:center;">Method</h2>
    <p>TADSR is a single step real-word image super-resolution method based on diffusion model. 
      Gigen a low-quality inputs, TADSR is capable of reconstructing high-quality images at various generation levels, conditioned on the input timestep \(t_{s}\). </p>
    <br>
    <figure>
      <img src="/TADSR_files/overview.png" alt="Overview image" style="width: 100%;">
    </figure>
    <p>
      TADSR consists of two components: Time-Aware VAE Encoder (TAE) and Time-Aware Variational Score Distillation (TAVSD).
      TAE projects the low-quality input images into different latent distributions conditioned on timestep \(t_{s}\), in order to better leverage the generative priors of the pre-trained Stable Diffusion (SD) model.
      TAVSD associates the timestep of the student model and the teacher model, enabling the teacher to provide more consistent gradient supervision conditioned on the timestep \(t_{s}\).
      By fully exploiting the diverse generative priors of SD across different time steps, TADSR naturally achieves a controllable trade-off between fidelity and generation.  
    </p>
  </div>

  <div class="content">
    <h2 style="text-align:center;">Results</h2>
    <h2>Quantitative Comparisons</h2>
    <figure>
      <img src="/TADSR_files/Quantitative_Comparisons.png" alt="Quantitative_Comparisons" style="width: 100%;">
    </figure>
    <p>
      TADSR achieves the best performance in almost all the no-reference metircs like MAINIQA, CLIPIQA, TOPIQ, and QALIGN, while also exhibiting competitive reference metrics like PSNR. 
      This demonstrates that TADSR leverages the generative priors of the pre-trained SD more effectively, resulting in superior image reconstruction quality.
    </p>
    <h2>Visual Comparisons</h2>
    <figure>
      <img src="/TADSR_files/Vision_Compare_1.png" alt="synth_result" style="width: 100%;">
    </figure>
    <figure>
      <img src="/TADSR_files/Vision_Compare_2.png" alt="synth_result" style="width: 100%;">
    </figure>
      Compared to other SD-based Real-ISR methods,TADSR consistently produces clearer, more realistic,and more natural results, demonstrating its stronger image restoration capability while preserving fidelity.
    <h2>Adjustable SR Results</h2>
    <figure>
      <img src="/TADSR_files/Vision_Compare_ts.png" alt="synth_result" style="width: 100%;">
    </figure>
    With increasing timestep condition \(t_{s}\), TADSR progressively leverages the generative priors of SD for image restoration, leading to more generation-driven results. 
    This allows users to flexibly balance fidelity and generation by tuning the timestep condition \(t_{s}\).
  </div>


<div class="content">
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
</div>


  <footer class="footer">
    <div class="container">
      <div class="columns is-centered">
        <!-- <div class="column is-8"> -->
            <p>
              This website's source code is borrowed from the <a
              href="GitHub - google/dreambooth">DreamBooth</a> project page.
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