## Pixel-level and Semantic-level Adjustable Super-resolution: A Dual-LoRA Approach


<a href='https://arxiv.org/pdf/2412.03017'><img src='https://img.shields.io/badge/Paper-Arxiv-red'></a>

[Lingchen Sun](https://scholar.google.com/citations?hl=zh-CN&tzom=-480&user=ZCDjTn8AAAAJ)<sup>1,2</sup>
| [Rongyuan Wu](https://scholar.google.com/citations?user=A-U8zE8AAAAJ&hl=zh-CN)<sup>1,2</sup> | 
[Zhiyuan Ma](https://scholar.google.com/citations?user=F15mLDYAAAAJ&hl=en)<sup>1</sup> | 
[Shuaizheng Liu](https://scholar.google.com/citations?user=wzdCc-QAAAAJ&hl=en)<sup>1,2</sup> | 
[Qiaosi Yi](https://dblp.org/pid/249/8335.html)<sup>1,2</sup> |
[Lei Zhang](https://www4.comp.polyu.edu.hk/~cslzhang)<sup>1,2</sup>

<sup>1</sup>The Hong Kong Polytechnic University, <sup>2</sup>OPPO Research Institute

**ABSTRACT** 
Diffusion prior-based methods have shown impressive results in real-world image super-resolution (SR). However, most existing methods entangle pixel-level and semanticlevel SR objectives in the training process, struggling to balance pixel-wise fidelity and perceptual quality. Meanwhile, users have varying preferences on SR results, thus it is demanded to develop an adjustable SR model that can be tailored to different fidelity-perception preferences during inference without re-training. We present Pixel-level and Semantic-level Adjustable SR (PiSA-SR), which learns two LoRA modules upon the pre-trained stable-diffusion (SD) model to achieve improved and adjustable SR results. We first formulate the SD-based SR problem as learning the residual between the low-quality input and the high-quality output, then show that the learning objective can be decoupled into two distinct LoRA weight spaces: one is characterized by the ℓ2-loss for pixel-level regression, and another is characterized by the LPIPS and classifier score distillation losses to extract semantic information from pretrained classification and SD models. In its default setting, PiSA-SR can be performed in a single diffusion step, achieving leading real-world SR results in both quality and efficiency. By introducing two adjustable guidance scales on the two LoRA modules to control the strengths of pixel-wise fidelity and semantic-level details during inference, PiSASR can offer flexible SR results according to user preference without re-training.
---


## ⏰ Update
The code and model will be ready soon.
- **2024.12.4**: This repo and paper are released.

:star: If PiSA-SR is helpful to your images or projects, please help star this repo. Thanks! :hugs:

## 🌟 Overview Framework
![PiSA-SR](figs/framework.png)
(a) Training procedure of PiSA-SR. During the training process, two LoRA modules are respectively optimized for pixel-level and semantic-level enhancement.

(b) Inference procedure of PiSA-SR. During the inference stage, users can use the default setting to reconstruct the high-quality image in one-step diffusion or adjust λ<sub>pix</sub> and λ<sub>sem</sub> to control the strengths of pixel-level and semantic-level enhancement.
## 😍 Visual Results
### Adjustable SR
![PiSA-SR](figs/adjustable.png)

By increasing the guidance scale λ<sub>pix</sub> on the pixel-level LoRA module, the image degradations such as noise and compression artifacts can be gradually removed; however, a too-strong λ<sub>pix</sub> will make the SR image over-smoothed. By increasing the guidance scale λ<sub>sem</sub> on the semantic-level LoRA module, the SR images will have more semantic details; nonetheless, a too-high λ<sub>sem</sub> will generate visual artifacts.

### Comparisons with Other DM-Based SR Methods
![ccsr](figs/comparison.png)