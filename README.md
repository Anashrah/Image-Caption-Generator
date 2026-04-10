# Image-Caption-Generator
Repository for the computer vision project, Image Caption Generator.

### Team Members
Anashrah Adil

Blessings Ajughu

Wayne Lu

Jaqueline Lomas Vazquez

Emaan Gohar


### Tier Selection - Tier 2
This project fits Tier 2 because it fine‑tunes a pretrained vision–language model on an existing caption dataset. It requires meaningful engineering, training, evaluation, and a working demo, but does not require building a model from scratch.

### Problem Statement
Images contain rich visual information, but computers cannot naturally describe them in human language. This project addresses the real‑world need for automatically describing images, enabling accessibility, better search, content moderation, and efficient organization of large visual datasets. It aims to help platforms that need to understand what an image is to detect unsafe content, violence, or restricted material, and it also enhances text-based searches for images, which is extremely important in the age of the internet and social media. The goal is to build a system that understands an image and produces a natural‑language description.

### Solution Overview
We fine‑tune a pretrained image‑captioning model using a Kaggle dataset that already includes images and caption annotations. The system processes an input image, extracts visual features using a vision encoder, and generates a caption using a transformer‑based decoder. A simple inference script will allow users to upload an image and receive a caption.

### Technical Approach
* Technique: Encoder–decoder vision–language modeling
* Model: Pretrained vision + BLIP or CNN + RNN
* Frameworks: PyTorch + Pytorch Transformers

### Dataset Plan
* Source: Kaggle COCO caption dataset
* Split: The dataset includes separate train/val/test annotation files, so we use the provided splits
* Size: Thousands of images with multiple human‑written captions
* Labels: Captions (primary), optional object tags if included

Link: (https://www.kaggle.com/datasets/nikhil7280/coco-image-caption)

### Week By Week Plan
<img width="645" height="268" alt="image" src="https://github.com/user-attachments/assets/8b35c464-b66b-48cf-aa9e-6dad4f6a1655" />

### Resources Needed
* Compute: Google Colab, Kaggle
* Cost: $0
* APIs: Hugging Face Transformers (free)
* Storage: ~5–10 GB for dataset + model checkpoints

### Risks & Mitigations

<img width="822" height="391" alt="image" src="https://github.com/user-attachments/assets/42d89dd2-ba24-497d-b0fd-5f24a8607097" />

