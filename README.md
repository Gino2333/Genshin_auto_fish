<div align='center' >

# ✨✨GenshinAutoFish✨✨
</div>

## |简介
原神自动钓鱼AI主要由YOLOX组成。使用迁移学习，半监督学习进行训练。 模型也包含一些使用opencv等传统数字图像处理方法实现的不可学习部分。

其中YOLOX用于鱼的定位和类型的识别以及鱼竿落点的定位。opencv识别游标，pywin32控制钓鱼过程的点击，让力度落在最佳区域内。

## 更新和修复

- 请查看[LOG](./doc/LOG.md)

- [ ] 自动选择鱼饵也自适应分辨率（目前换鱼饵仅支持1920*1080）
- [ ] 适配须弥地区的鱼
### 😢须弥地区的鱼的图片紧缺😢

## |安装使用流程
### 0.5.必要环境配置
- 安装Visual Studio

前往[Visual Studio官网](https://visualstudio.microsoft.com/zh-hans/downloads/)下载社区版并安装

打开 **Visual Studio Installer** 在工作负荷选项栏中勾选 **使用 C++ 的桌面开发**，把安装路径改到你喜欢的文件夹中，开始安装

- 安装CUDA和CUDNN **(非NVIDA显卡请跳过)**

我的环境中使用的是**CUDA v11.8.0**，**CUDNN v8.6.0 for CUDA 11.x**

前往NVIDIA官网的[CUDA下载页面](https://developer.nvidia.cn/cuda-toolkit-archive)根据你的机器型号选择下载并安装

前往NVIDIA官网的[cuDNN下载页面](https://developer.nvidia.cn/rdp/cudnn-archive)下载Windows版本的zip压缩包

解压下载下来的cuDNN zip压缩包，将里面的所有文件复制到以下目录 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v**.*\

**如果你已完成以上步骤，请重启电脑后进入Python环境配置的步骤**

### 1.Python环境配置

安装python运行环境（解释器），推荐使用[Anaconda](https://www.anaconda.com/).

在开始菜单找到 **anaconda prompt(命令行界面)** 打开，创建新Python环境并激活:

```shell
# 创建虚拟环境
conda create -n ysfish python=3.10

# 激活虚拟环境
conda activate ysfish
```
经测试 **Python3.10** 环境下可正常运行

### 2.下载项目代码

- 使用Git下载， 如果没有Git请查看[Git安装教程](https://cloud.tencent.com/developer/article/2099150)

```shell
git clone -b development https://github.com/HuYo-OS/Genshin_auto_fish.git
```

或**Code > Download ZIP**下载后直接解压。

### 3.依赖库安装

切换命令行到本工程所在目录
```shell
cd Genshin_auto_fish
```

安装PyTorch

- 如果你已经安装CUDA和cuDNN:

```shell
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117
```


- 如果你的不是**NVIDIA**显卡 或 只想用CPU跑的

```shell
pip3 install torch torchvision torchaudio
```

- 安装依赖
```shell
pip install -U pip
pip install -r requirements.txt
```

然后从 [Releases](https://github.com/HuYo-OS/Genshin_auto_fish/releases) 下载[**best_tiny3.pth**]放到这个项目的 weights 文件夹下

### 3.运行钓鱼AI

使用显卡加速
```shell
python fishing.py --device gpu
```

使用CPU运行
```shell
python fishing.py --device cpu
```
运行后出现init ok后按r键开始钓鱼，原神需要以1920x1080的分辨率运行。出于性能考虑检测框不会实时显示，处理运算后台进行。

## |常见问题

- Q: 为什么启动之后到游戏内按**r**之后始终没有开始钓鱼
- A-1: 这可能是你没有以管理员身份运行，请在终端内Ctrl+C结束程序再在管理员模式的终端内运行本项目
---
- Q: 启动时报错**pywintypes.error: (1400, 'GetClientRect', '无效的窗口句柄。')**
- A-1: 需要打开**原神**再运行本项目哦
---
