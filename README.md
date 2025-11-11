# Specialist vs. Generalist Vision-Language Models on Flickr30k

## Project Overview

This research project compares specialist (GLIP) and generalist (LLaVA) vision-language models on the Flickr30k Entities grounding benchmark. The project is inspired by the foundational paper "Flickr30k Entities: Collecting region-to-phrase correspondences for richer image-to-sentence models" (Plummer et al., 2015), and builds upon some of my previous work in computer vision research, including a [CS 444 research project on U-Net Variants for Semantic Segmentation](https://github.com/krishnankonda/unet-semantic-segmentation-cityscapes).

## Core Hypothesis

Testing whether modern SOTA "generalist" models (like LLaVA) have incidentally learned fine-grained grounding skills compared to "specialist" models (like GLIP) that were explicitly trained for this task.

## Installation

1. Clone this repository:
```bash
git clone https://github.com/krishnankonda/vlm-grounding-analysis
cd flickr30k-vision-language-comparison
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Data Download

The project requires two datasets:

1. **Flickr30k Entities Annotations**: Download `annotations.zip` from the [GitHub repository](https://github.com/BryanPlummer/flickr30k_entities)
2. **Flickr30k Images**: Download `flickr30k-images.tar.gz` from the UIUC research server

After downloading, extract both archives:
- Extract `annotations.zip` to `data/` (creates `data/Flickr30kEntities/` directory)
- Extract `flickr30k-images.tar.gz` to `data/flickr30k-images/`

Alternatively, the notebook includes code cells to download these files programmatically.

## Usage

The notebook is organized into 5 phases:

1. **Phase 1**: Environment setup and data preparation
2. **Phase 2**: Helper functions (IoU calculation, visualization)
3. **Phase 3**: GLIP (specialist model) experiment
4. **Phase 4**: LLaVA (generalist model) experiment
5. **Phase 5**: Quantitative comparison and qualitative failure analysis

Run the cells sequentially. The notebook will:
- Parse Flickr30k Entities XML annotations
- Create a reproducible 500-sample test set
- Evaluate both models in zero-shot settings
- Generate quantitative metrics (Mean IoU, Accuracy)
- Visualize failure cases and success cases

## Results Structure

The notebook generates:
- `test_set.csv`: The 500-sample test set used for evaluation
- Quantitative metrics comparing GLIP vs LLaVA
- Qualitative visualizations of success and failure cases
- Final conclusions summarizing key findings

## Current Status

**Results are pending** - Currently, I'm awaiting permission to access the Flickr30k images dataset from the UIUC research server. Once access is granted and the images are downloaded, I will be executing the full experimental pipeline (Phases 3-5) to generate comparative results between GLIP and LLaVA models.

## Requirements

- Python 3.8+
- CUDA-capable GPU
- ~10GB disk space for datasets
- ~15GB RAM (for loading LLaVA model)

## Citation

```
@inproceedings{plummer2015flickr30k,
  title={Flickr30k Entities: Collecting region-to-phrase correspondences for richer image-to-sentence models},
  author={Plummer, Bryan A and Wang, Liwei and Cervantes, Chris M and Caicedo, Juan C and Hockenmaier, Julia and Lazebnik, Svetlana},
  booktitle={Proceedings of the IEEE international conference on computer vision},
  year={2015}
}
```

```
@article{flickr30k,
    title={From image descriptions to visual denotations: New similarity metrics for semantic inference over event descriptions},
    author={Peter Young and Alice Lai and Micah Hodosh and Julia Hockenmaier},
    journal={TACL},
    volume={2},
    pages={67--78},
    year={2014}
}
```
