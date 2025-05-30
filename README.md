# CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning

[![CVPR 2025](https://img.shields.io/badge/CVPR-2025-blue.svg)]([https://openaccess.thecvf.com/content/CVPR2024/html/He_Gradient_Reweighting_Towards_Imbalanced_Class-Incremental_Learning_CVPR_2024_paper.html](https://cvpr.thecvf.com/))
[![PyTorch](https://img.shields.io/badge/PyTorch-Implementation-red.svg)](https://pytorch.org/)

This repository contains the official PyTorch implementation of **CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning**, accepted at CVPR 2025.

📄 **Paper**: [CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning](https://openaccess.thecvf.com/content/CVPR2024/html/He_Gradient_Reweighting_Towards_Imbalanced_Class-Incremental_Learning_CVPR_2024_paper.html)

## Overview

CL-LoRA introduces a novel approach for class-incremental learning without rehearsal, leveraging low-rank adaptation techniques to efficiently learn new classes while preserving knowledge of previously learned tasks.

## Getting Started

### Training

To train the model, navigate to the main directory and run:

```
python main.py <json_config_path>
```

### Supported Datasets

The following datasets are supported with pre-configured JSON files:

#### CIFAR-100
```
python main.py ./exps/cifar.json
```

#### ImageNet-R
```
python main.py ./exps/inr.json
```

#### ImageNet-A
```
python main.py ./exps/ina.json
```

#### VTAB
```
python main.py ./exps/vtab.json
```

### Configuration

The JSON configuration files contain experiment setup and hyperparameters. Key CL-LoRA specific parameters include:

- **`general_pos`**: Position indices for task-shared LoRA adapters
- **`specific_pos`**: Position indices for task-specific LoRA adapters  
- **`msa`**: Multi-Head Self-Attention adaptation settings for Query (Q), Key (K), and Value (V)
  - `1`: Apply adaptation
  - `0`: No adaptation

### Example Configuration

```json
{
  "msa": [1, 0, 1],
  "general_pos": [0, 1, 2, 3, 4, 5],
  "specific_pos": [6, 7, 8, 9, 10, 11]
}
```

This configuration:
- Adapts Q and V in Multi-Head Self-Attention (`msa`: [1, 0, 1])
- Uses task-shared LoRA in the first 6 ViT blocks (`general_pos`)
- Uses task-specific LoRA in the last 6 ViT blocks (`specific_pos`)

## Citation

If you find this work useful in your research, please cite:

```bibtex
@article{He_2025_CVPR,
    author    = {He, Jiangpeng and Duan, Zhihao and Zhu, Fengqing},
    title     = {CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning},
    booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
    month     = {June},
    year      = {2025}
}
```

## Acknowledgments

This implementation builds upon the **LAMDA-PILOT** framework. 

**LAMDA-PILOT Repository**: https://github.com/sun-hailong/LAMDA-PILOT

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or issues, please open an issue on GitHub or contact the authors.
