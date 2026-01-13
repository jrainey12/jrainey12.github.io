---
layout: page
title: Combating AI 
description: used for Image Manipulation
main_title: <h1> Combating the use of AI in Image Manipulation</h1>
main_description: <h2 align=center>Building Smarter Tools to expose Smarter Fakes.</h2>
img: assets/img/TRAIT/kodim23.png
importance: 3
category: TBC #PostDoc
---

<style>
h2   {
     color: #429435;
     font-size:180%;
     }
</style>

---

Artificial Intelligence has transformed how we create and edit images, for better and for worse.
While tools like DALL-E and Stable Diffusion enable creative expression, they also blur the line between real and fake.

<br>
## Goal
---

This research takes on the challenge of AI manipulated images by developing:

- A large-scale dataset of AI-manipulated images

- A deep learning detection model that identifies and localizes AI-based edits

<br>
## Our Contributions
---

1. The NCL-IMD.v1 Dataset

We built a dataset of 14,000+ AI-manipulated images, each paired with ground truth masks that show exactly where alterations occurred.

Created using Blended Latent Diffusion, a state-of-the-art text-guided inpainting model.

Includes a wide range of image contexts, mask sizes, and manipulation types.

Publicly available: MediaTrust Dataset

2. A New Detection Model

We proposed a CNN-based Autoencoder architecture designed specifically to detect manipulations made by diffusion models — where existing models (like MM-Fusion) fail.

Outperforms MM-Fusion on AI-generated images.

F1 score improved from 0.27 → 0.50, with high accuracy (≈96%).

<br>
## How We Built the Dataset
---

The data generation process was fully automated:

- Mask Generator – creates random, human-like selection areas on images.

- Prompt Generator – uses CLIP + GPT4All (Mistral Instruct) to generate text prompts describing modifications.

- Image Manipulation – applies Blended Latent Diffusion to generate localized edits.

- Balancing & Splitting – ensures diverse, balanced data across train/validation/test sets.

Total output: 13,614 high-resolution manipulated images
Each image has an associated binary mask indicating the edited regions.

<br>
## Model Development
---

Existing detectors (like TruFor and MM-Fusion) perform well on traditional photo edits but struggle with AI-generated content — especially diffusion-based manipulations.

We designed a VGG19-based Autoencoder optimized for anomaly detection in image space.

Removed weaker modalities (e.g., Noiseprint++)

Trained on the NCL-IMD.v1 dataset

Used Mean Squared Error (MSE) loss for stable convergence

The result was a faster, more reliable, and explainable model for identifying AI edits.

<br>
## Results
---

Model	F1	Accuracy	Precision	Recall
MM-Fusion (default)	0.28	0.85	0.33	0.71
MM-Fusion (retrained)	0.23	0.65	0.16	0.56
CNN-Autoencoder (ours)	0.50	0.96	0.53	0.55

Our Autoencoder model more than doubled the detection performance on diffusion-generated images compared to existing approaches.

<br>
## Why It Matters
---
TODO

<br>
## Key Takeaways
---

Diffusion-based image edits are fundamentally harder to detect than GAN-based ones.

Prompt quality affects realism — weak text inputs can cause unrealistic or stylistic artifacts.

A data-centric approach (building large, balanced datasets) is crucial for progress in forensic AI research.

<br>

## Looking Ahead
---

Improve realism of generated manipulations using next-gen diffusion models.

Refine prompt generation for context-aware edits.

Combine visual and semantic features for hybrid detection.

Develop open benchmarks for evaluating AI manipulation detection globally.
