---
title: HPC 配置深度学习环境
mathjax: true
abbrlink: 8ac8ca6d
date: 2020-10-02 17:13:59
categories:
tags:
---
### Step 1 连接 HPC 中心 (Linux/Mac OS)
在 Mac terminal 中运行以下的代码
`ssh yournetid@login.storrs.hpc.uconn.edu`
通常此时会要求输入密码。

为了避免每次都输入很长的命令，我们可以自定义 ssh 别名
<!--more-->

```python
import time
import numpy as np
import pandas as pd
import tensorflow as tf
from tensorflow import keras
import matplotlib.pyplot as plt

get_ipython().run_line_magic('matplotlib', 'inline')
get_ipython().run_line_magic('config', "InlineBackend.figure_format = 'svg'")

#set suppress to not use scientific counting
np.set_printoptions(suppress=True)
```

```bash
cd ~./ssh
touch config  #如果这里没有config文件
vim config  # 用Vim 编辑config文件
```
在 `vim config` 之后, 在 vim 编辑器写入一下代码

```python
Host uconn-hpc  # the short name you want
    Hostname login.storrs.hpc.uconn.edu
    User hoq20002  #你的login id
    ForwardAgent no
```
然后，就可以直接通过 `ssh uconn-hpc` 连接学校的 HPC 中心了。

### Step 2 conda 配置Python环境
下面以Deep_Filter项目为例
```Bash
mkdir Deep_Filter
cd Deep_Filter #单独建立一个folder后进入
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh  # download 最新的miniconda 包
bash Miniconda3-latest-Linux-x86_64.sh -b -p miniconda

module load cuda/10.1      #具体的version 需要参考学校 HPC 提供的 module, 可用 module avail 查看
module load cudnn/7.6.5

# 创建一个名为 pyGPUrtx 的 python 环境

miniconda/bin/conda create -n pyGPUrtx python=3.8.3  
source miniconda/bin/activate pyGPUrtx
# 在激活 pyGPUrtx 之后就可以安装所需要的 python pacakage

pip install tensorflow
pip install keras
pip install matplotlib
pip install sklearn
pip install pandas
```
基本按照上述操作就可以配置好深度学习所需要的环境。注意：不要在 login mode 下直接 pip 安装所需要的 package, 此时一般不会安装成功。最好就是先用 conda 创建自己的 python 环境, 再安装需要的包。

### Step 3: Slurm submit job
当我们配置好了 python 环境，我们就准备把写好的脚本提交到HPC (参考 Appendix 如何把脚本上传到HPC)。按照目前所了解的信息，HPC 中心都会要求用 slurm (workload manager) 提交任务。

`vim submit.sh # 创建并进入 submit.sh 文件`

```Bash
#在 vim 模式下编辑 submit.sh 的内容如下
#！/bin/bash
#SBATCH --partition=gpu_rtx  # 此处选的是gpu_rtx, 一般会提供四种partition: gpu, gpu_rtx, gpu_v100, gpu_gtx.
#SBATCH --gres=gpu：1

module load cuda/10.1
module load cudnn/7.6.5
source miniconda/bin/activate pyGPUrtx 

python xxx.py
```
退出 vim  编辑器后输入以下命令提交任务

```bash
sbatch submit.sh #提交
#上面命令运行后，会出现类似 slurm-xxxxx.out 
# 比如: slurm-3764657.out

cat slurm-3764657.out  # 查看结果
```

### Appendix: 上传脚本至HPC
1. FileZilla
2. Github
比较友好，学习成本低的方式是直接使用 FileZilla。 如果对 Github 操作熟悉的可以直接用 Github 链接文件夹（Deep_Filter), 请转这篇文章。

### 参考文献
1. [Introduction to GPU computing on HPC](https://sydney-informatics-hub.github.io/training.artemis.gpu/aio.html)
2. [Storrs HPC Cluster](https://wiki.hpc.uconn.edu/index.php/Main_Page)
3. [MATH-5800-Spring-2020](http://jeremy9959.net/Math-5800-Spring-2020/Cluster.html)
4. [Getting Started on the HL  HPC platform](https://ulhpc-tutorials.readthedocs.io/en/latest/beginners/)
