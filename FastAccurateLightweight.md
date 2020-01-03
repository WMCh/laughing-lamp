# I. Introduction
balance performance against applicability
- accurate (visual quality): on which most works focus - loss terms
- fast (inference speed): real-time application (video streaming or PC games) - operations
- lightweight (memory occupation): mobile device application - parameters

factors that affect the inference speed:
- reduction of the parameters: adopt the recursive manner or parameter sharing strategy (DRCN, DRRN, MemNet)
- the depth (operations) of the network: unusual convolution layer, cascading structure, neural architecture search (LapSRN, CARN, IDN, IMDN)
- the different scale factors

# II. Related work
## 1. recursive manner for less parameters
### (1) (CVPR 2016) Deeply-Recursive Convolutional Network for Image Super-Resolution [[paper](https://arxiv.org/abs/1511.04491)]
### (2) (CVPR 2017) Image Super-Resolution via Deep Recursive Residual Network [[paper](http://openaccess.thecvf.com/content_cvpr_2017/papers/Tai_Image_Super-Resolution_via_CVPR_2017_paper.pdf)] [[code](https://github.com/tyshiwo/DRRN_CVPR17)]
### (3) (ICCV 2017) MemNet: A Persistent Memory Network for Image Restoration [[paper](https://arxiv.org/abs/1708.02209)] [[code](https://github.com/tyshiwo/MemNet)]
## 2. unusual convolution
### (1) (CVPR 2017 / TPAMI 2018) LapSRN [[paper1](https://arxiv.org/abs/1704.03915)][[paper2](https://arxiv.org/abs/1710.01992)] [[code](https://github.com/phoenix104104/LapSRN)]
### (2) (ECCV 2018) Fast, Accurate, and Lightweight Super-Resolution with Cascading Residual Network [[paper](https://arxiv.org/abs/1803.08664)] [[code](https://github.com/nmhkahn/CARN-pytorch)]
cascading on both the local and global levels
- learning multi-level representations
- quickly propagate information from lower to higher layers
### (3) (CVPR 2018) Fast and Accurate Single Image Super-Resolution via Information Distillation Network [[paper](https://arxiv.org/abs/1803.09454)] [[code](https://github.com/Zheng222/IDN-Caffe)]
IDN = feature extraction block (FBlock) + information distillation blocks (DBlocks) + reconstruction block (RBlock)

DBlock = enhancement unit + compression unit

enhancement unit (S: slice, C: concatenation)

D3-D1=D1-D2=D6-D4=D4-D5=d, D3=D4 s.t. D_{i-1}=(s-1)*d

combine the previous information with some current information
- local short-path features: partially retain local short-path information
- local long-path features: further extract long-path feature maps

compression unit: 1x1 conv
### (4) (ACM MM 2019) Lightweight Image Super-Resolution with Information Multi-distillation Network [[paper](https://arxiv.org/abs/1909.11856)] [[code](https://github.com/Zheng222/IMDN)]
information multi-distillation block (IMDB) = progressive refinement module (PRM) + contrast-aware channel attention (CCA) layer + 1x1 conv

PRM: extract useful features little by little
- refined features: preserved
- coarse features: further processed

CCA: rich the information about structures, textures, and edges: replace global average pooling with the summation of standard deviation and mean
### (5) (arxiv 2019) Fast, Accurate and Lightweight Super-Resolution with Neural Architecture Search [[paper](https://arxiv.org/abs/1901.07261)] [[code](https://github.com/xiaomi-automl/FALSR)]
