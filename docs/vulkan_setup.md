# Vulkan Backend Setup

Real-ESRGAN can upscale images and videos through the NCNN Vulkan backend. Use `--backend=vulkan` to enable it when calling the inference scripts.

## Requirements for RTX 4090

- NVIDIA driver **520.56** or newer providing Vulkan 1.3 support.
- `realesrgan-ncnn-vulkan` binary installed and available on `PATH`.
- Vulkan runtime libraries (`libvulkan1`, `vulkan-tools`, or the Vulkan SDK).

## Environment variables

On systems with multiple ICD files, select the NVIDIA implementation:

```bash
export VK_ICD_FILENAMES=/usr/share/vulkan/icd.d/nvidia_icd.json
```

When running under WSL, expose the Vulkan libraries:

```bash
export LD_LIBRARY_PATH=/usr/lib/wsl/lib:$LD_LIBRARY_PATH
```

## Usage

```bash
python inference_realesrgan_video.py -i input.mp4 --backend=vulkan
```

The command pipes frames through the `realesrgan-ncnn-vulkan` executable similarly to the CUDA path.
