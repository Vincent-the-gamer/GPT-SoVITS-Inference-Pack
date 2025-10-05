# GPT-SoVITS Inference Pack

_GPT-SoVITS语音模型推理包_

这个Fork仅用来做GPT-SoVITS语音模型推理。

This fork is made for inference only.

> [!IMPORTANT]
> 不要使用本项目做训练任务，需要跑训练请认准官方项目。
> 
> Please don't use this fork for training tasks, do it using the original repo.

## 我训练的模型 / Models I trained

以下所有模型均可以在Release下载

1. B站游戏UP主/主播：[丝茉茉i](https://space.bilibili.com/27564630)
    - GPT权重文件：silkmomo-e15.ckpt
    - SoVITS权重文件：silkmomo_e8_s144.pth

更多模型敬请期待...

## 使用方法

这里不再赘述，可以参考官方项目，总结一下就是：

1. 本地运行(可以手动安装依赖，也可以用懒人脚本一键启动)
2. Docker镜像打包
3. Jupyter Notebook

### 注意事项

> [!NOTE]
> GPT权重文件统一放到GPT_SoVITS/GPT_weights
> 
> SoVITS权重文件统一放到GPT_SoVITS/SoVITS_weights
> 
> 注意训练时使用的版本，比如丝茉茉i模型是使用v2Pro版本训练的，所以文件夹是GPT_weights_v2Pro和SoVITS_weights_v2Pro，以此类推
> 
> 在进行推理时，需要一个参考语音和对应的文本，可以有效影响推理效果。参考语音和文本已经打包进了Release对应模型压缩包中。
> 
> 此外，需要下载ffmpeg，注意版本，4，5，6，7都行，别用最新版
> 
> 本项目替换过inference-webui.py，这样不会报错

1. 创建虚拟环境，pip，conda都可以。pytorch对poetry支持不是很好，别用。
2. cd到项目路径，安装依赖
```shell
pip install -r requirements.txt
```
3. 安装最新版Stable的torch套件，根据实际情况决定是否安装gpu版
```shell
# 根据cuda版本选择链接，cu126代表Cuda 12.6
# --index-url https://download.pytorch.org/whl/cu126
pip install torch torchvision torchaudio torchcodec
```

4. 运行Web UI
```shell
python webui.py
```

注意看报错：
```
warning:  No Such Model:
    GPT_SoVITS/pretrained_models/v2Pro/s2Gv2Pro.pth
    GPT_SoVITS/pretrained_models/v2Pro/s2Dv2Pro.pth
    GPT_SoVITS/pretrained_models/s1v3.ckpt
    GPT_SoVITS/pretrained_models/chinese-roberta-wwm-ext-large
    GPT_SoVITS/pretrained_models/chinese-hubert-base
```

上面的我已经打包放到Release了，如果需要其它预训练模型，需要到[Hugging Face链接](https://huggingface.co/lj1995/GPT-SoVITS/tree/main)下载对应的预训练模型放到GPT_SoVITS/pretrained_models, 缺啥下啥就好。