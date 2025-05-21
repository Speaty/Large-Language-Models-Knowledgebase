Visual Language Model - A model that can process both images (vision) and natural language text (language).

### Example use cases
- Image retrieval from natural language text
- Phrase grounding, i.e., performing object detection from an input image and natural language phrase (e.g. A **young person** swings a **bat**)
- Visual question answering, i.e., finding answers from an input image and a question in natural language.
- Generate a caption for a given image. This can also take the form of conditional text generation, where you'd start with a natural language prompt and an image. 
- Detection of hate speech from social media content involving both images and text modalities. 

## Learning Strategies
VLMs typically consist of an image encoder, a text encoder, and a strategy to fuse information from the two. They've changed a lot over time but latest research predominantly adopts image and text encoders with transformer architectures to separately or jointly learn features. 

### Contrastive Learning

![[contrastive_learning.png| Contrastive pre-training and zero-shot image classification.]]

Learns a text encoder and image encoder jointly with a contrastive loss using large datasets consisting of {image, caption} pairs. Aims to map feature space such that the distance between the embeddings of image0text pairs is minimised if they match or maximised if they don't.

CLIP uses cosine distance whereas ALIGN and DeCLIP design their own distance metrics to account for noisy datasets. LiT uses the CLIP pre-training objective on the text encoder while keeping the image encoder frozen to 'teach the text encoder to better read image embeddings from the image encoder'. FLAVA uses a combination of contrastive learning and other pretraining strategies to align vision and language embeddings. 

contrastive learning?


- [CLIP](https://arxiv.org/abs/2103.00020)
- [GLOOB](https://arxiv.org/abs/2110.11316)
- [ALIGN](https://arxiv.org/abs/2102.05918)
- [DeCLIP](https://arxiv.org/abs/2110.05208)
- [LiT](https://arxiv.org/abs/2111.07991)
- [FLAVA](https://arxiv.org/abs/2112.04482)

### PrefixLM
![[prefixlm.png]]
Similar to autoregressive language models, applying the concept of the prefix to images by dividing each image into a number of patches and sequentially feeding these patches to the model as input. 

Mainly limited in terms of application to image captioning and visual question-answering, weak in object detection and image segmentation tasks.

- [SimLVM](https://arxiv.org/abs/2108.10904)
- [VirTex](https://arxiv.org/abs/2006.06666v3)

### Frozen PrefixLM

![[frozen_prefixlm.png]]

Frozen PrefixLMs only update the parameters of the vision encoder during training to generate image embeddings that can be used as a prefix to the pre-trained, frozen language model similarly to PrefixLM

?

### Multi-modal Fusing with Cross Attention

![[cross_attention_fusing.png]]

Directly fuses visual information into the layers of a language model decoder using a cross-attention mechanism instead of using images as additional prefixes to the language model. The main goal of such models is to balance the mixture of text generation capacity and visual information efficiently, which is highly important in the absence of large multi-modal datasets. 

- VisualGPT
- VC-GPT
- Flamingo
- FIBER


### Masked-Language Modeling / Image-Text Matching

![[mlm_itm.png]]

Given a partially masked caption, the MLM objective is to predict the masked words based on the corresponding image. Requires either using a richly annotated multi-modal dataset with bounding boxes, or using an object detection model to generate object region proposals for parts of the input text. 

- VisualBERT
- FLAVA
- ViLBERT
- LXMERT
- BridgeTower

### No Training

![[asif.png]]
Using pre-trained image and text models or adapt pre-trained multi-modal models to new downstream tasks without additional training.

- MaGiC - iterative optimisation through a pre-trained autoregressive language model to generate a caption for the input image by computing a CLIP-based 'Magic Score' using CLIP embeddings of the generated tokens and the input image. 
- ASIF - pictured above, uses a method to turn pre-trained uni-modal image and text models into multi-modal model for image captioning using a relatively small multi-modal dataset without additional training. 


# More Info on VLMs
- [Hugging Face - A Dive into Vision-Language Models](https://huggingface.co/blog/vision_language_pretraining)
- [[UNITER (UNiversal Image-TExt Representation Learning]]