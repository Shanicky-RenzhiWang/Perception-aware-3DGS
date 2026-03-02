# Perception-aware-3DGS

Official implementation of the ICLR 2026 paper:

> **Beyond Visual Reconstruction Quality: Object Perception-aware 3D Gaussian Splatting for Autonomous Driving**  
> [Paper](https://openreview.net/forum?id=PmQlMTBmpa)  
> [Renzhi Wang](https://renzhiwang.xyz/), [Yuxiang Fu](https://github.com/function-y-x), [Wuqi Wang](https://scholar.google.com/citations?hl=zh-CN&user=LTBq-4MAAAAJ), [Haigen Min](https://js.chd.edu.cn/xxgcxy/mhg/list.htm), [Wei Feng](https://cic.tju.edu.cn/faculty/fengwei/index.html), [Lei Ma](https://www.malei.org/), [Qing Guo](https://tsingqguo.github.io/)

## Overview

This repository provides perception-aware optimization objectives for 3DGS-based autonomous driving reconstruction.

- **Method 1:** Perception-aligned Loss (`--use_obj_loss`)
- **Method 2:** Object Zone Quality Loss (`--use_perception_metric`)

The optimization is integrated with the following bases:

- [S^3Gaussian](https://github.com/nnanhuang/S3Gaussian)
- [OmniRe (DriveStudio)](https://github.com/ziyc/drivestudio)
- EMD (for 3DGS settings built on similar pipelines)

## Preparation

1. Clone this repository **with submodules**.
2. Set up environments by following the instructions of the corresponding base repositories.
3. Make sure you can run each base method's sample pipeline before enabling perception-aware losses.

## Installation

Install the additional dependency:

```bash
pip install ultralytics==8.1.36
```

## Usage

### 1) S^3Gaussian + Optimization

1. Generate offline GT bounding boxes (for speed-up):

```bash
python generate_gt_bbox.py
```

2. Train with Perception-aligned Loss (Method 1):

```bash
python train.py -s {SCENE_DATA_INFO} --port 6017 --expname "waymo" --model_path {MODEL_PATH} --use_obj_loss
```

3. Train with Object Zone Quality Loss (Method 2):

```bash
python train.py -s {SCENE_DATA_INFO} --port 6017 --expname "waymo" --model_path {MODEL_PATH} --use_perception_metric
```

### 2) OmniRe + Optimization

1. Generate offline GT bounding boxes (for speed-up):

```bash
python generate_gt_bbox.py
```

2. Run with Perception-aligned Loss (Method 1):

```bash
bash run_bbox.sh {SCENE_ID}
```

3. Run with Object Zone Quality Loss (Method 2):

```bash
bash run_iou.sh {SCENE_ID}
```

### 3) EMD + Optimization

EMD 3DGS workflows can be used in a similar way.

1. Generate offline GT bounding boxes (for speed-up):

```bash
python generate_gt_bbox.py
```

2. Run with Perception-aligned Loss (Method 1):

```bash
bash scripts/dynamic/run_dynamic_recon.sh {GPU_ID} {SCENE_ID} --use_obj_loss
```

3. Run with Object Zone Quality Loss (Method 2):

```bash
bash scripts/dynamic/run_dynamic_recon.sh {GPU_ID} {SCENE_ID} --use_perception_metric
```

## Acknowledgements

We thank the authors of [S^3Gaussian](https://github.com/nnanhuang/S3Gaussian) and [OmniRe](https://github.com/ziyc/drivestudio) for their contributions to the community.

## TODO

- Package the optimization module as a reusable Python library.
