# CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning [CVPR 2025] 

This repository is the official PyTorch implementation of **CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning** [[paper]](https://openaccess.thecvf.com/content/CVPR2024/html/He_Gradient_Reweighting_Towards_Imbalanced_Class-Incremental_Learning_CVPR_2024_paper.html).

## Running with Pre-trained Models:
The implementation of our method **CL-LoRA** is also available in **LAMDA-PILOT**: https://github.com/sun-hailong/LAMDA-PILOT


## Training Instructions

To run the code, navigate to /script/ and execute the provided bash script with the following format:

```
bash main.sh <approach> <gpu> <dataset> <scenario> <initial_classes> <total_tasks>
```

### Parameter Specifications:

- `<approach>`: Approach to be used, located in `./src/approaches/`.
  - `DGR`: our proposed Decoupled Gradients Reweighting (DGR) method.
- `<gpu>`: Index of the GPU to run the experiment.
- `<dataset>`: Dataset to be used (Options: `cifar100`, `imagenet_subset`, `imagenet_1000`, `Food101`).
- `<scenario>`: Learning scenario, including:
  - `conv`: Conventional CIL.
  - `lt`: Shuffled long-tailed scenario (experiments in main paper).
  - `ltio`: Ordered long-tailed scenario.
- `<initial_classes>`: Number of classes in the first base task.
- `<total_tasks>`: Total number of tasks (including the base task).

### Examples:

- Shuffled long-tailed case with LFS, 20 tasks on CIFAR100:
```
bash main.sh DGR 0 cifar100 lt 5 20
```

- Shuffled long-tailed case with LFH, 10 tasks on ImageNetSubset:
```
bash main.sh DGR 0 imagenet_subset lt 50 11
```

- Ordered long-tailed case with LFH, 5 tasks on Food101:
```
bash main.sh DGR 0 Food101 ltio 51 6
```

- Conventional case with LFS, 10 tasks on ImageNet_1000:
```
bash main.sh DGR 0 imagenet_1000 conv 100 10
```


### Reference:
If you find this work useful, please cite us by: 
```
@article{He_2025_CVPR,
    author    = {He, Jiangpeng},
    title     = {CL-LoRA: Continual Low-Rank Adaptation for Rehearsal-Free Class-Incremental Learning},
    journal = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
    month     = {June},
    year      = {2024},
    pages     = {16668-16677}
}
```
