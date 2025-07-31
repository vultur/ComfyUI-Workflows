<div align="center">
  
<img width="1029" height="436" alt="ComfyUI Workflows" src="https://github.com/user-attachments/assets/a7a2bfda-4459-49fb-9fae-febd5d1af364" />
  
# ComfyUI Workflows

[开始使用](#开始使用)  |  [工作流程](#工作流程)  |  [常见问题](#常见问题)

</div>

## 开始使用

> [!TIP]
> 如果使用 [LibLib AI](https://www.liblib.art/comfy)、[RunComfy](https://www.runcomfy.com/zh-CN/comfyui-web)、[RunningHub](https://www.runninghub.cn/)或 [ComfyUI Web](https://comfyuiweb.com/) 等 ComfyUI 云平台进行创作，请忽略以下安装步骤。

### 安装 ComfyUI

- [下载 Windows 版](https://download.comfy.org/windows/nsis/x64)（需要 NVIDIA 显卡）
- [下载 Mac 版](https://download.comfy.org/mac/dmg/arm64)（需要 Apple Silicon (M1, M2, M3)）
- [手动安装](https://github.com/comfyanonymous/ComfyUI?tab=readme-ov-file#manual-install-windows-linux)（支持所有操作系统和 GPU 类型（NVIDIA、AMD、Intel、Apple Silicon、Ascend））

### 安装 Flux 模型

> [!NOTE]
> 使用基于其它模型的工作流时，请自行完成模型安装，包括 Checkpoint（U-Net、CLIP、VAE）、ControlNet、LoRA 等。

如果你的电脑显存较大，可以考虑使用 Flux.1 的原始版本；如果你的电脑显存较小或者性能不足建议直接使用 **GGUF** 版本。

> [!TIP]
> GGUF 格式的 Flux 模型提供了多个不同质量的模型文件，如果你在对应的仓库下不知道该下载哪个模型文件，这里有一个简单的引导规则：
> Q 后面的数字越大，需要的显存越大，同时生成图片的质量越高。例如：Q2 需要的显存较小但生成的图片质量较低，Q8 需要的显存较大但生成的图片质量较高。
> 此外，你也可以根据模型的文件大小来判断对应的质量，文件越大通常意味着生成的图片质量越高，同时需要的显存也越大。

| 作者 | 模型名称 | 特性 | 显存要求 | 文件大小 | 下载地址 |
| --- | --- | --- | --- | --- | --- |
| Black Forest Labs | Flux.1 Dev | 需要下载 CLIP、VAE、UNET 等几个模型 | 16GB+ | 23.8GB | [下载](https://huggingface.co/black-forest-labs/FLUX.1-dev/resolve/main/flux1-dev.safetensors?download=true) |
| Black Forest Labs | Flux.1 Schnell | 需要下载 CLIP、VAE、UNET 等几个模型 | 16GB+ | 23.8GB | [下载](https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/flux1-schnell.safetensors?download=true) |
| Black Forest Labs | Flux.1 Kontext Dev | 需要下载 CLIP、VAE、UNET 等几个模型 | 16GB+ | 23.8 GB | [下载](https://huggingface.co/black-forest-labs/FLUX.1-Kontext-dev/resolve/main/flux1-kontext-dev.safetensors?download=true) |
| ComfyUI | Flux.1 Dev FP8 | 融合 Clip 及 VAE，仅需要下载一个模型 | 8GB+ | 17.2GB | [下载](https://huggingface.co/Comfy-Org/flux1-dev/resolve/main/flux1-dev-fp8.safetensors?download=true) |
| ComfyUI | Flux.1 Schnell FP8 | 融合 Clip 及 VAE，仅需要下载一个模型 | 8GB+ | 17.2GB | [下载](https://huggingface.co/Comfy-Org/flux1-schnell/resolve/main/flux1-schnell-fp8.safetensors?download=true) |
| ComfyUI | Flux.1 Kontext Dev FP8 | 需要下载 CLIP、VAE、UNET 等几个模型 | 8GB+ | 11.9GB | [下载](https://huggingface.co/Comfy-Org/flux1-kontext-dev_ComfyUI/resolve/main/split_files/diffusion_models/flux1-dev-kontext_fp8_scaled.safetensors?download=true) |
| Kijai | Flux.1 Dev FP8 | 融合 Clip 及 VAE，仅需要下载一个模型 | 8GB+ | 11.9GB | [下载](https://huggingface.co/Kijai/flux-fp8/resolve/main/flux1-dev-fp8.safetensors?download=true) |
| Kijai | Flux.1 Schnell FP8 | 融合 Clip 及 VAE，仅需要下载一个模型 | 8GB+ | 11.9GB | [下载](https://huggingface.co/Kijai/flux-fp8/resolve/main/flux1-schnell-fp8-e4m3fn.safetensors?download=true) |
| City96 | Flux.1 Dev GGUF | 需要下载 CLIP、VAE、UNET 等几个模型；<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | 6GB+ | / | [下载](https://huggingface.co/city96/FLUX.1-dev-gguf) |
| City96 | Flux.1 Schnell GGUF | 需要下载 CLIP、VAE、UNET 等几个模型；<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | 6GB+ | / | [下载](https://huggingface.co/city96/FLUX.1-schnell-gguf) |
| bullerwins | Flux.1 Kontext Dev GGUF | 需要下载 CLIP、VAE、UNET 等几个模型；<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | 6GB+ | / | [下载](https://huggingface.co/bullerwins/FLUX.1-Kontext-dev-GGUF) |

> [!IMPORTANT]
> 1. 下载 **Flux 模型文件**，取决于你的显存配置；
> 2. 将文件拷贝到 `ComfyUI/models/unet/` 目录。
> 
> **注意**：如果使用 ComfyUI 或 Kijai 提供的融合模型，请将文件拷贝到 `ComfyUI/models/checkpoints/` 目录。

#### 安装 CLIP 模型

| 模型名称 | 文件大小 | 下载地址 | 备注 |
| --- | --- | --- | --- |
| `clip_l.safetensors` | 246 MB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true) | / |
| `t5xxl_fp16.safetensors` | 9.79GB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true) | 高显存（>32GB） |
| `t5xxl_fp8_e4m3fn.safetensors` | 4.89GB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn.safetensors?download=true) | 低显存（8～12GB）|
| `t5xxl_fp8_e4m3fn_scaled.safetensors` | 5.16 GB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn_scaled.safetensors?download=true) | 推荐，低显存 (8～12GB) |

> [!IMPORTANT]
> 1. 下载 **clip\_l.safetensors** 模型文件；
> 2. 下载 **t5xxl\_fp16.safetensors** 或 **t5xxl\_fp8\_e4m3fn.scaled.safetensors** 模型文件，取决于你的显存配置；
> 3. 将文件拷贝到 `ComfyUI/models/text_encoders/` 目录。

#### 安装 VAE 模型

| 文件名称 | 文件尺寸 | 下载地址 | 备注 |
| --- | --- | --- | --- |
| `ae.safetensors` | 335 MB | [下载](https://huggingface.co/black-forest-labs/FLUX.1-dev/resolve/main/ae.safetensors?download=true) | / |

> [!IMPORTANT]
> 1. 下载 `ae.safetensors` 模型文件；
> 2. 将文件拷贝到 `ComfyUI/models/vae` 目录。

### 安装 ComfyUI 插件

- [ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF)（**可选**）：用于加载和运行 GGUF 格式的模型文件；
