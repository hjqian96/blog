---
title: Python 札记
mathjax: true
abbrlink: 8d2e3aa6
date: 2020-10-02 17:13:59
categories:
tags:
---
此post记录工作中用到的Python知识。

<!--more-->
## Python
#### 如何导入自己写的py文件

```bash
import sys 
sys.path.append(r'D:\')
import mymodule
mymodule.function() 
```

#### 如何解决 Memory Error ？
在程序正确的情况下，出现这种情况是分配的内存不够。在 Windows 系统下，
`This PC  (right click enter to properties)-> Advanced system settings  -> Performance Settings -> Advanced -> Virtual memory (click Change)`
进入到 Virtual Memory 的带动页面，可以选择一个容量够大的盘，在下面设置custom size。设置完成，点击确认一步一步退出后再重跑程序即可。

## Numpy
#### 如何求一个numpy list 的 [simple moving average](https://en.wikipedia.org/wiki/Moving_average)？
此处需要用到 pandas 的功能。

```python
list=[1,2,3,7,9]
periods=20
list_series=pd.Series(list)
windows=list_series.rolling(periods)
moving_averages=windows.mean()
ma_list = moving_averages.tolist()
ma_without_nans=ma_list[periods-1:]
```

### Pandas

### Jupyter Notebook
Jupyter notebook 如何存储数据？或者在python 中如何存储数据以便后续使用？深度学习或者数据分析中，一般会出现numpy array 和 DataFrame等数据类型，
- 对于多维numpy array, 可以直接使用 `np.save(file='filename.npy',arr=your_data)`
- 对于DataFrame,可以创建一个HDF5文件，然后依次存储需要的数据。
```python
store=pd.HDFStore('fileName.h5')
store['data1']=data1
store['data2']=data2
```

- keras 神经网络的模型保存

```python
model.save('filename.h5',overwrite=True, include_optimizer=True)
# 重新加载 model
from keras.models import load_model
model=load_model('filename.h5')
```
overwrite: 如果源文件存在，是否需要覆盖。此方法会保存模型的结构，权重，训练配置（损失函数、优化器），优化器的状态等。

#### Jupyternote Book 快捷键
`command+]` 向右缩进
`ctrl+/` 注释（单行或多行）
`esc+F` 代码查找、替换和忽略输出
`shift+M` 合并 cell

