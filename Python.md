# Python

## Setting up the python environment

[Miniconda是什么？](https://docs.conda.io/projects/miniconda/en/latest/)

安装Conda:
```bash
curl -O https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
```

修改用户目录下的 .condarc 文件来使用 TUNA 镜像源:
```yaml
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```
运行`conda clean -i`清除索引缓存，保证用的是镜像站提供的索引。

## PyTorch 

常用安装：`conda install debugpy ipython pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia`

### Resources

### FAQ

* [A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/)
* High training variance at the end of epoch.
  * Symptoms: loss spike, divergence, trained to NaN.
  * Potential Causes:
    * Did you forget to call `model.train()` after using `model.eval()` for evaluation?
    * The training dataloader instantiated with `torch.utils.data.DataLoader`
      should use the argument `drop_last=True` to ensure the last batch is not too small.

## Experiment Logging

* Tensorboard
  * Tutorial: https://pytorch.org/tutorials/intermediate/tensorboard_tutorial.html
* Weights and Biases
  * https://wandb.ai
