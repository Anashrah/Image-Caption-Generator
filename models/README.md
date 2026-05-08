# Models

This folder documents the two models used in this project — the pretrained base model we started with and our fine-tuned model trained on the COCO dataset.

---

## 1. Pretrained Model (Base)

**Model:** `Salesforce/blip-image-captioning-base`
**Source:** [Hugging Face — Salesforce/blip-image-captioning-base](https://huggingface.co/Salesforce/blip-image-captioning-base)

This is the base BLIP model created by Salesforce. We used it as our starting point and fine-tuned it on the COCO 2017 dataset. It was originally trained on 129 million image-caption pairs from the web.

| Detail | Value |
|---|---|
| Architecture | ViT vision encoder + BERT-style transformer decoder |
| Tokenizer | WordPiece (~30k vocab) |
| Pretrained on | 129 million image-caption pairs |
| Task | Image captioning |
| Framework | PyTorch + Hugging Face Transformers |

**Load the base model:**
```python
from transformers import BlipProcessor, BlipForConditionalGeneration

processor = BlipProcessor.from_pretrained("Salesforce/blip-image-captioning-base")
model     = BlipForConditionalGeneration.from_pretrained("Salesforce/blip-image-captioning-base")
```

---

## 2. Our Fine-Tuned Model

**Model:** `bajughu/group22600-image-caption-generator`
**Source:** [Hugging Face — bajughu/group22600-image-caption-generator](https://huggingface.co/bajughu/group22600-image-caption-generator)

This is our fine-tuned version of BLIP. We adapted the pretrained base model by training it on 25,014 COCO 2017 caption-image pairs. Fine-tuning taught the model to generate more accurate and natural captions aligned with the COCO dataset distribution.

| Detail | Value |
|---|---|
| Base model | Salesforce/blip-image-captioning-base |
| Fine-tuned on | COCO 2017 val2017 |
| Training pairs | 25,014 caption-image pairs |
| Train / Val / Test split | 80% / 10% / 10% |
| Epochs completed | 2 out of 5 planned |
| Best validation loss | 1.9545 |
| Optimizer | AdamW (lr=5e-5, weight decay=0.01) |
| Batch size | 8 |
| Early stopping | Patience = 2 epochs |
| Augmentation | RandomHorizontalFlip, ColorJitter, RandomRotation |

**Final Metrics:**

| Metric | Score |
|---|---|
| CIDEr (primary) | 0.8636 |
| ROUGE-L | 0.4014 |
| METEOR | 0.3216 |
| BLEU-4 | 0.1286 |

**Load our fine-tuned model:**
```python
from transformers import BlipProcessor, BlipForConditionalGeneration

processor = BlipProcessor.from_pretrained("bajughu/group22600-image-caption-generator")
model     = BlipForConditionalGeneration.from_pretrained("bajughu/group22600-image-caption-generator")
```

**Generate a caption:**
```python
from PIL import Image

img     = Image.open("your_image.jpg").convert("RGB")
inputs  = processor(images=img, text="a photo showing", return_tensors="pt")
out_ids = model.generate(**inputs, num_beams=4, max_new_tokens=40)
caption = processor.decode(out_ids[0], skip_special_tokens=True)
print(caption)
```

---

## How They Differ

| | Pretrained (Base) | Our Fine-Tuned |
|---|---|---|
| Trained on | 129M web images | 25,014 COCO pairs |
| Task specific | General captioning | COCO-style captioning |
| CIDEr score | ~0.75 (zero-shot) | 0.8636 |
| Available at | Salesforce/blip-image-captioning-base | bajughu/group22600-image-caption-generator |
