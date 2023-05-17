---
title: Colab Tutorial and PyTorch Tutorial
date: 2023-05-01
tags: [PyTorch]
categories: 人工智能与数据科学
references: 
  - title: 李宏毅 2023 春机器学习课程
    url: https://speech.ee.ntu.edu.tw/~hylee/ml/2023-spring.php

---

> 吴恩达说：AI 是最新的电力，大约在一百年前，我们社会的电气化改变了每个主要行业，从交通运输行业到制造业、医疗保健、通讯等方面，如今我们见到了 AI 明显的令人惊讶的能量，带来了同样巨大的转变。而在 AI 的各个分支中，发展的最为迅速的就是深度学习。去年初时，我尝试学习过[动手学深度学习](/动手学深度学习/)课程，但是没坚持下来。这次选择李宏毅 2023 年春季最新的机器学习课程，这门课专注于深度学习领域，和最新技术的应用。以下为我在学习作业零：Colab Tutorial and PyTorch Tutorial 时所做的笔记，可供参考。

<!--more-->

### 一、Colab Tutorial 

#### 什么是 Colab？

Colab，即“Colaboratory”，允许您在浏览器中编写和执行 Python，零配置，免费使用 GPU，轻松分享。无论您是学生、数据科学家还是 AI 研究人员，Colab 都可以让您的工作更轻松。 您可以在代码块中键入 Python 代码，或使用前导感叹号 `!` 将代码块更改为 bash 环境以执行 Linux 代码（`!ls`）。

使用感叹号 `!` 启动一个新的 shell，执行操作，然后终止该 shell，而百分比 `%` 影响与笔记本相关的进程，它被称为魔术命令。对于 `cd`（更改目录）命令，使用 `%cd` 而不是 `!` ，其他魔术命令列在[这里](https://ipython.readthedocs.io/en/stable/interactive/magics.html)。

要使用 Google 提供的免费 GPU，请单击 "Runtime" -> "Change Runtime Type"。“Hardward Accelerator” 下有三个选项，选择“GPU”。

导入 PyTorch 并检查分配的 GPU，如果拿到 K80 可能会跑非常久：

```python
import torch
torch.cuda.is_available() # is GPU available
# Outputs True if running with GPU
```

```python
# check allocated GPU type
!nvidia-smi
```

#### Colab 文件操作

通过 Google Drive 下载文件：存储在 Google Drive 中的一个文件有以下分享链接，可以使用 `--fuzzy` 命令通过知道链接的 Colab 下载文件。

```python
# Download the file with the following link, and rename it to pikachu.png
!gdown --fuzzy https://drive.google.com/file/d/14FK5G6DOh7EdLyoj4D5teRSzriTOUPD7/view?usp=sharing --output pikachu.png
```

```python
# List all the files under the working directory
!ls
```

挂载 Google Drive：如果你不想每次开始新的会话都下载数据，或者你希望一些文件永久保存，你可以将自己的 Google Drive 挂载到Colab，直接下载/保存数据到你的 Google Drive。

```python
from google.colab import drive
drive.mount('/content/drive')
# your google drive will be mounted at /content/drive
```

挂载驱动器后，Google Drive 的内容将被挂载到名为 MyDrive 的目录中。

```python
%cd /content/drive/MyDrive 
#change directory to google drive
!mkdir ML2023 #make a directory named ML2023
%cd ./ML2023
#change directory to ML2023
```

```python
!pwd #output the current directory
```

#### 可能遇到的问题

由于 Colab 会侦测使用者是否在电脑前面使用，因此一定时间没有动作会自动断线。开启 F12 控制台，贴上 Javascript：

```js
function ClickConnect() {
    console.log("Working...");  // debug 用
    // 去選擇按鈕
    var connectbutton = document.querySelector(
        "colab-toolbar-button" +
        "#connect-icon.big-icon.icon-okay");
    // 點個兩下
    connectbutton.click(); connectbutton.click();
};

// 設定固定每 10 分鐘點一下
const stopit = setInterval(
    ClickConnect, 10 * 60 * 1000);

// 這行沒有沒關係，只是避免停不下來
const stopping = stopper => clearInterval(stopper);
```

有用的 Linux 命令（在 Colab 中）：

-   `ls` : 列出当前目录下的所有文件，
-   `ls -l `: 列出当前目录下所有文件的详细信息，
-   `pwd `: 输出工作目录，
-   `mkdir <dirname>` : 创建一个目录 `<dirname>`，
-   `cd <dirname> `: 移动到目录 `<dirname>`，
-   `gdown `：从谷歌驱动器下载文件，
-   `wget` : 从网上下载文件，
-   `python <python_file>`：执行一个 Python 文件。

### 二、PyTorch Tutorial

#### 什么是 PyTorch？

PyTorch 是 Python 中的机器学习框架。两个主要特点：N-dimensional Tensor computation (like NumPy) on GPUs & Automatic differentiation for training deep neural networks（自动计算微分）。

训练神经网络需要：定义神经网络（Define Neural Network）、损失函数（Loss Function）、优化算法（Optimization Algorithm）。

在 Pytorch 中训练和测试神经网络需要：加载数据（Load Data）、训练（Training）、验证（Validation）、测试（Testing）。

#### Dataset & Dataloader

Dataset：存储数据样本和期望值。

Dataloader：批量分组数据，启用多处理。
