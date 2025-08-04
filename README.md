<div align="center">
  
<img width="1280" height="720" alt="H100" src="https://github.com/user-attachments/assets/ae29735c-9ec5-4574-b5a1-d09787592d56" />
  
# ComfyUI Workflows

[开始使用](#开始使用)  |  [工作流程](#工作流程)  |  [常见问题](#常见问题)

</div>

## 开始使用

> [!TIP]
> 如果你使用 [LibLib AI](https://www.liblib.art/comfy)、[RunComfy](https://www.runcomfy.com/zh-CN/comfyui-web) 或 [RunningHub](https://www.runninghub.cn/) 等 ComfyUI 云平台进行创作，请忽略以下安装步骤。

### 安装 ComfyUI

- [下载 Windows 版](https://download.comfy.org/windows/nsis/x64)（需要 NVIDIA 显卡）
- [下载 Mac 版](https://download.comfy.org/mac/dmg/arm64)（需要 Apple Silicon (M1, M2, M3)）
- [手动安装](https://github.com/comfyanonymous/ComfyUI?tab=readme-ov-file#manual-install-windows-linux)（支持所有操作系统和 GPU 类型（NVIDIA、AMD、Intel、Apple Silicon、Ascend））

### 安装 Flux 模型

> [!NOTE]
> 如需运行基于其它模型的工作流，请先安装对应的模型，包括 Checkpoint（U-Net、CLIP、VAE）、LoRA 等。

Flux 对硬件要求较高，原始权重版本最低显存要求：`> 16 GB`。

开源社区基于原始权重版本提供了多个版本，对硬件要求较低：

- **FP8 版本**：最低显存要求：`> 12 GB`，生成的图片质量牺牲较小；
- **GGUF 版本**：最低显存要求：`> 6 GB`，生成的图片质量有所损失。

如果你的电脑显存较大，请使用 Flux 的原始权重版本；如果你的电脑显存较小或性能不足，建议使用 **GGUF 版本**。

> [!TIP]
> **GGUF 版本**提供了多个不同质量的模型文件，如果你在对应的仓库下不知道该下载哪个模型文件，
>
> 这里有一个简单的引导规则：
>
> - Q 后面的数字越大，需要的显存越大，同时生成图片的质量越高；
> - 模型文件越大通常意味着生成的图片质量越高，同时需要的显存越大。
>
> 例如：Q2 需要的显存较小但生成的图片质量较低，Q8 需要的显存较大但生成的图片质量较高。

| 作者 | 模型名称 | 特性 | 下载地址 |
| --- | --- | --- | :---: |
| Black Forest Labs | `FLUX.1 [dev]` | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/black-forest-labs/FLUX.1-dev/resolve/main/flux1-dev.safetensors?download=true) |
| Black Forest Labs | `FLUX.1 [schnell]` | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/flux1-schnell.safetensors?download=true) |
| Black Forest Labs | `FLUX.1 Kontext [dev]` | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/black-forest-labs/FLUX.1-Kontext-dev/resolve/main/flux1-kontext-dev.safetensors?download=true) |
| Black Forest Labs | `FLUX.1 Krea [dev]` | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/black-forest-labs/FLUX.1-Krea-dev/resolve/main/flux1-krea-dev.safetensors?download=true) |
| Comfy Org | `FLUX.1 [dev]` **FP8** | 融合 Clip 及 VAE，仅需要下载一个模型 | [下载](https://huggingface.co/Comfy-Org/flux1-dev/resolve/main/flux1-dev-fp8.safetensors?download=true) |
| Comfy Org | `FLUX.1 [schnell]` **FP8** | 融合 Clip 及 VAE，仅需要下载一个模型 | [下载](https://huggingface.co/Comfy-Org/flux1-schnell/resolve/main/flux1-schnell-fp8.safetensors?download=true) |
| Comfy Org | `FLUX.1 Kontext [dev]` **FP8** | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/Comfy-Org/flux1-kontext-dev_ComfyUI/resolve/main/split_files/diffusion_models/flux1-dev-kontext_fp8_scaled.safetensors?download=true) |
| Comfy Org | `FLUX.1 Krea [dev]` **FP8** | 需要下载 CLIP、VAE、UNET 等几个模型 | [下载](https://huggingface.co/Comfy-Org/FLUX.1-Krea-dev_ComfyUI/resolve/main/split_files/diffusion_models/flux1-krea-dev_fp8_scaled.safetensors?download=true) |
| city96 | `FLUX.1 [dev]` **GGUF** | 需要下载 CLIP、VAE、UNET 等几个模型<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | [查看](https://huggingface.co/city96/FLUX.1-dev-gguf) |
| city96 | `FLUX.1 [schnell]` **GGUF** | 需要下载 CLIP、VAE、UNET 等几个模型<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | [查看](https://huggingface.co/city96/FLUX.1-schnell-gguf) |
| QuantStack | `FLUX.1 Kontext [dev]` **GGUF** | 需要下载 CLIP、VAE、UNET 等几个模型<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF)| [查看](https://huggingface.co/QuantStack/FLUX.1-Kontext-dev-GGUF) |
| QuantStack | `FLUX.1 Krea [dev]` **GGUF** | 需要下载 CLIP、VAE、UNET 等几个模型<br />需要安装 [ComfyUI-GGUF插件](https://github.com/city96/ComfyUI-GGUF) | [查看](https://huggingface.co/QuantStack/FLUX.1-Krea-dev-GGUF) |

> [!IMPORTANT]
>
> 1. 下载 **Flux** 模型文件，取决于你的显存配置；
> 2. 将文件拷贝到 `ComfyUI/models/diffusion_models/` 目录。
>
> ⚠️ **注意**
>
> - **GGUF 版本**请将文件拷贝到 `ComfyUI/models/unet/` 目录；
> - **单文件版本**（融合 CLIP 及 VAE）请将文件拷贝到 `ComfyUI/models/checkpoints/` 目录。

#### 安装 CLIP 模型

| 模型名称 | 文件大小 | 下载地址 | 备注 |
| --- | --- | :---: | --- |
| `clip_l.safetensors` | 246 MB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true) | / |
| `t5xxl_fp16.safetensors` | 9.79 GB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true) | 高显存（`> 32 GB`）|
| `t5xxl_fp8_e4m3fn_scaled.safetensors` | 5.16 GB | [下载](https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn_scaled.safetensors?download=true) | 低显存（`8 ～ 12 GB`）|

> [!IMPORTANT]
>
> 1. 下载 `clip\_l.safetensors` 模型文件；
> 2. 下载 **t5xxl** 模型文件，取决于你的显存配置；
> 3. 将文件拷贝到 `ComfyUI/models/text_encoders/` 目录。

#### 安装 VAE 模型

| 文件名称 | 文件大小 | 下载地址 | 备注 |
| --- | --- | :---: | --- |
| `ae.safetensors` | 335 MB | [下载](https://huggingface.co/black-forest-labs/FLUX.1-dev/resolve/main/ae.safetensors?download=true) | / |

> [!IMPORTANT]
>
> 1. 下载 `ae.safetensors` 模型文件；
> 2. 将文件拷贝到 `ComfyUI/models/vae` 目录。

### 安装 ComfyUI 插件（可选）

> [!NOTE]
> 你也可以在 ComfyUI 中直接导入模板文件（`*.json`），根据提示安装缺失的插件。

| 插件名称 | 插件功能 | 备注 |
| --- | --- | :---: |
| [ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF) | 用于加载和运行 GGUF 格式的模型文件 | **可选** |
| [cg-use-everywhere](https://github.com/chrisgoringe/cg-use-everywhere) | 使用虚拟连接减少节点之间的连线 | **推荐** |
| [ComfyUI_essentials](https://github.com/cubiq/ComfyUI_essentials) | 扩展 ComfyUI 节点，增强图像处理能力 | **推荐** |
| [efficiency-nodes-comfyui](https://github.com/jags111/efficiency-nodes-comfyui) | 提供丰富的效率节点，优化和加速工作流构建 | **推荐** |

## 工作流程

> [!NOTE]
> 由于设备限制，该仓库下的工作流大多使用 **GGUF 版本**（`.gguf`）的模型。
>
> 如需替换工作流中默认的模型版本或模型文件，你需要手动添加或移除对应的自定义节点。
>
> 例如：若使用 Flux 的原始权重版本替换工作流中的 GGUF 版本，需要将其中的 **Unet Loader (GGUF)** 节点替换为 **Load Diffusion Model** 节点；而使用 **FP8 版本**时则需要将其替换为 **Checkpoint Loader** 节点，同时移除 CLIP 及 VAE 的相关加载节点。

### Flux

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |
| **GGUF** 模型加载 | [查看](./FLUX/unet_loader_gguf.json) | [预览](./FLUX/output/unet_loader_gguf.png) |
| CFG 参数测试 | [查看](./FLUX/FLUX.1-Krea[dev]-CFG_XY_Plot.json) | [预览]() |
| Steps 参数测试 | [查看](./FLUX/FLUX.1-Krea[dev]-Steps_XY_Plot.json) | [预览]() |
| Guidance 参数测试 | [查看](./FLUX/FLUX.1-Krea[dev]-Guidance_XY_Plot.json) | [预览]() |
| CFG + Steps XY 图表 | [查看](./FLUX/FLUX.1-Krea[dev]-CFG+Steps_XY_Plot.json) | [预览]() |
| Sampler + Scheduler XY 图表，支持多组提示词 | [查看](./FLUX/FLUX.1-Krea[dev]-Sampler+Scheduler.json) | [预览]() |

### Kolors

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### Lumina

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### HiDream

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### OmniGen2

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### SDXL/SD3.5

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### Hunyuan

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### LTXV

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### Wan

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

### 其它

| 工作流程 | 模板文件 | 生成图像 |
| --- | :---: | :---: |

## 常见问题

- Q1

- Q2
