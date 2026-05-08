# Image-Caption-Generator

![Demo Screenshot](results/images/live%20demo%20screen%20shot%20(2).jpg)

An AI system that automatically generates natural-language captions for any image.

### Team Members

Anashrah Adil — Organized GitHub repository and project structure, worked on data exploration and documentation, updated README and uploaded project results

Blessing Ajughu — Trained the BLIP image caption model, created model training and demo notebooks, managed dataset setup and model integration

Wayne Lu — Worked on evaluation notebook and model metrics, tested and evaluated model performance

Jaqueline Lomas Vazquez — Created the final presentation slides, assisted with project organization

Emaan Gohar — Recorded the demo video, created the inference report, assisted with final submission preparation


### The Problem
Images contain rich visual information but computers cannot naturally describe them in human language. This creates a real gap in accessibility, content moderation, and image search. With billions of images uploaded every day, manually writing captions is simply not possible at scale.

#### Our Solution
We fine-tuned BLIP (Bootstrapped Language Image Pretraining) on the COCO 2017 dataset to automatically generate natural-language descriptions for any image. The system processes an image through a ViT vision encoder, passes the embeddings through a BERT-style transformer decoder via cross-attention, and outputs a caption using beam search generation.

### Impact
- Visually impaired users can access image content without manual descriptions
- Social media platforms can automatically detect unsafe or restricted content
- Search engines can index images using generated text descriptions
- Organizations can organize large visual datasets without human labeling


### Technical Approach
Task: Image Captioning (Vision Language Modeling)
Model: Salesforce/blip-image-captioning-base (fine-tuned)
Framework: PyTorch + Hugging Face Transformers
Key Libraries: transformers, torchvision, nltk, pycocoevalcap, rouge-score, matplotlib

### System Architecture

[Image Input] → [Preprocessing 384x384] → [ViT Vision Encoder] → [Cross-Attention] → [Transformer Decoder] → [Beam Search] → [Caption Output]



### Dataset Plan
* Source: Kaggle COCO caption dataset
* Split: Split: Train: (80%) Val: (10%) Test: (10%)
* Size: 600 images with captions
* Classes: Captions (primary), optional object tags if included
* Preprocessing: resizing, augmentation

Link: (https://www.kaggle.com/datasets/nikhil7280/coco-image-caption)

### Results: 
???


### Week By Week Plan
<img width="645" height="268" alt="image" src="https://github.com/user-attachments/assets/8b35c464-b66b-48cf-aa9e-6dad4f6a1655" />

### Resources Used
* Compute: Google Colab, Kaggle
* Cost: $0
* APIs: Hugging Face Transformers (free)
* Storage: ~5–10 GB for dataset + model checkpoints

### Risks & Mitigations

<img width="822" height="391" alt="image" src="https://github.com/user-attachments/assets/42d89dd2-ba24-497d-b0fd-5f24a8607097" />

