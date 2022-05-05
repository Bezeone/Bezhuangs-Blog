---
title: 云上搭建基于 Anaconda 的 Jupyter 数据科学环境
date: 2021-05-09
tags: []
categories: 云服务
references:
  - title: 如何在云服务器上设置可远端访问的jupyter notebook
    url: https://www.jianshu.com/p/fff4a61dee7a
---

> Jupyter Notebook是基于浏览器网页的用于交互计算的应用程序，支持Python、R、Julia和Scala等多种语言，在数据科学相关领域有着非常大的用途。JupyterLab是基于web的集成开发环境，包含了Jupyter Notebook所有功能的同时还支持操作终端、编辑markdown文本、打开交互模式、查看csv文件及图片等功能，最近在学习的IBM数据科学专项课程也都是基于Jupyter Lab的，在阿里云主机上部署Jupyter环境也能使研究和学习更加方便。

<!--more-->

### 安装Anaconda

- 通过清华源安装最新版本Anaconda

  ```bash
  wget http://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-2020.11-Linux-x86_64.sh
  bash Anaconda3-2020.11-Linux-x86_64.sh
  # 狂按Enter>>yes>>继续狂按Enter安装
  ```

- Anaconda默认安装在`/root/anaconda3`目录下

- 配置环境变量

  ```bash
  vim ~/.bashrc
  # 添加下面两行内容
  #added by Anaconda3 4.4.0 installer
  export PATH="/root/anaconda3/bin:$PATH"
  ```
  
- 激活Anaconda环境并测试

  ```bash
  source ~/.bashrc
  conda --version
  ```

- 添加清华镜像源，并搜索时显示通道地址

  ```bash
  conda config --add channels 'https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/'
  conda config --set show_channel_urls yes
  ```

- 创建jupyter notebook运行环境

  ```bash
  conda create -n jupyter_notebook python=3
  # source activate jupyter_notebook 激活环境
  # source deactivate 退出环境
  ```

### 安装配置Jupyter

- 通过Anaconda安装Jupyter Notebook

  ```bash
  conda install jupyter notebook
  # 输入jupyter notebook --ip=127.0.0.1 --allow-root 可运行则为安装成功
  ```

- 生成Jupyter Notebook配置文件

  ```bash
  jupyter notebook --generate-config
  ```

- 设置Jupyter Notebook密码

  ```bash
  ipython
  In [1]: from notebook.auth import passwd
  In [2]: passwd()
  Enter password: 
  Verify password: 
  Out[2]: '加密字符串'
  ```

- 修改配置文件

  ```bash
  vim /root/.jupyter/jupyter_notebook_config.py
  #修改如下行
  c.NotebookApp.ip = '*'
  c.NotebookApp.password = '加密字符串'
  c.NotebookApp.open_browser = False
  c.NotebookApp.allow_root = True
  ```

- 启动Jupyter Notebook

  ```bash
  jupyter notebook
  ```

- 访问[云服务器公网ip地址:8888](http://106.15.200.147:8888/)

- 启动Jupyter Lab

  ```bash
  jupyter lab
  ```

- 访问[云服务器公网ip地址:8888](http://106.15.200.147:8888/)

### 注意事项

- Jupyter Notebook只适用于单用户登录，如果想搭建多用户的Jupyter的话，要使用JupyterHub进行搭建
- 阿里云默认不打卡8888端口，需要在服务器管理控制台中设置开放端口

### 添加JAVA环境支持

- 安装JDK（过程略）

- 下载 java 内核压缩包`ijava`，[下载地址](https://github.com/SpencerPark/IJava/releases)

- 上传到服务器，使用`unzip`命令解压

- 安装Java内核

  ```bash
  python install.py --sys-prefix
  ```

- 查看Jupyter内核支持

  ```python
  jupyter kernelspec list
  '''
  Available kernels:
    java       /root/anaconda3/share/jupyter/kernels/java
    python3    /root/anaconda3/share/jupyter/kernels/python3
  '''
  ```

  

