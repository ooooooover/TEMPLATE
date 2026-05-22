# Unified Transferability Metrics for Time Series Foundation Models [NeurIPS 2025]

## Authors

**Weiyang Zhang**​<sup>1</sup>, ​**Xinyang Chen**​<sup>1,📧</sup>, ​**Xiucheng Li**​<sup>1</sup>, ​**Kehai Chen**​<sup>1</sup>, ​**Weili Guan**​<sup>2</sup>, ​**Liqiang Nie**​<sup>1</sup>

<sup>1</sup> School of Computer Science and Technology, Harbin Institute of Technology (Shenzhen)

<sup>2</sup> School of Information Science and Technology, Harbin Institute of Technology (Shenzhen)

## Introduction

This repository is the official implementation of the paper **Unified Transferability Metrics for Time Series Foundation Models** (NeurIPS 2025).

We propose **unified transferability metrics** to reliably estimate how effectively pre-trained time series foundation models can transfer to downstream tasks. Our metrics evaluate transferability without full fine-tuning, enabling fast and consistent comparison across models.

## Model Zoo

We use models from four model families as our model zoo.

| Model Family    | Code                                                         | Pretrained Weight                                            |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| MOMENT          | [moment-timeseries-foundation-model/moment: MOMENT: A Family of Open Time-series Foundation Models, ICML'24](https://github.com/moment-timeseries-foundation-model/moment) | [AutonLab (Auton Lab)](https://huggingface.co/AutonLab)      |
| Timer、Timer-XL | [thuml/Large-Time-Series-Model: Official code, datasets and checkpoints for "Timer: Generative Pre-trained Transformers Are Large Time Series Models" (ICML 2024) and subsequent works](https://github.com/thuml/Large-Time-Series-Model) | [thuml/timer-base-84m · Hugging Face](https://huggingface.co/thuml/timer-base-84m) |
| UniTS           | [mims-harvard/UniTS: A unified multi-task time series model.](https://github.com/mims-harvard/UniTS/tree/main) | [Release Pretrained weights · mims-harvard/UniTS](https://github.com/mims-harvard/UniTS/releases/tag/ckpt) |

## Datasets

We follow the experimental settings of TSLib, and the required datasets can be found in [thuml/Time-Series-Library: A Library for Advanced Deep Time Series Models for General Time Series Analysis.](https://github.com/thuml/Time-Series-Library).

## Usage

 ### Installation Environment 

Environment requirement: Python > 3.11

```
conda create -n template python==3.11

conda activate pretrain

# Install the MOMENT package

pip install git+https://github.com/moment-timeseries-foundation-model/moment.git

# Install all dependencies

pip install -r requirements.txt
```



### Feature Extraction

By modifying the forward propagation process of the model, we extract and store embeddings. The model architectures can be found in the `model` directory, and the corresponding feature matrices are obtained via forward propagation.

### Score Calculation

You can input features into the TEMPLATE to estimate the transferability score.

```
from metric.metrics import TEMPLATE

dl_score,pl_score,ta_score = TEMPLATE(feature, first_feature,trend_feature)
```

The final transferability score is obtained by normalizing the three scores and then summing them up.

## Acknowledgement

We thank the contributors of MOMENT, Timer, UniTS, and Time-Series-Library for their open-source code and models.

## Citation

If you find this work helpful for your research, please kindly cite the following paper:

```
@inproceedings{zhangTEMPLATE,
  title={Unified Transferability Metrics for Time Series Foundation Models},
  author={Zhang,Weiyang and Chen,Xinyang and Li, Xiucheng and Chen, Kehai and Guan, Weili and Nie, Liqiang},
  booktitle={Annual Conference on Neural Information Processing Systems (NeurIPS)},
  year={2025}
}
```
## License

This project is released under the ​**Apache License 2.0**​.
