# Example codes for FCIS [1]

## Performance
SBD Train & Test

| Model | mAP@0.5 (Original [1]) | mAP@0.7 (Original [1]) | mAP@0.5 (weight conversion) | mAP@0.7 (weight conversion) |  mAP@0.5 (train) | mAP@0.7 (train) |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| FCIS ResNet101| 65.7 | 52.1 | 64.2 | 51.2 | 64.1 (1 GPU) | 51.2 (1 GPU) |

## Demo
Segment objects in an given image. This demo downloads SBD pretrained model automatically if a pretrained model path is not given.

```bash
python demo.py [--gpu <gpu>] [--pretrained-model <model_path>] <image.jpg>
```

## Evaluation
The evaluation can be conducted using [`chainercv/examples/instance_segmentation/eval_sbd.py`](https://github.com/chainer/chainercv/blob/master/examples/instance_segmentation)

## Train
You can train the model with the following code.
Note that this code requires `SciPy` module.

```bash
python train.py [--gpu <gpu>]
```

If you want to use multiple GPUs, use `train_multi.py`.
Note that this code requires `chainermn` module.

```bash
mpi4exec -n <n_gpu> python train_multi.py --lr  <n_gpu>*0.0005

```
You can download weights that were trained by ChainerCV.
- [FCIS ResNet101](https://chainercv-models.preferred.jp/fcis_resnet101_sbd_trained_2018_06_22.npz)

## Convert Mxnet model
Convert `*.params` to `*.npz`.
Note that the number of classes and network structure is specified by `--dataset`.

```bash
python mxnet2npz.py [--dataset sbd|coco] [--out <npz filename>] <param filename>
```


## References
1. Yi Li et al. "Fully Convolutional Instance-aware Semantic Segmentation" CVPR 2017.
