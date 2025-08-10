# 4K Inference Benchmark on RTX 4090

The optional `--compile` flag enables `torch.compile` for faster inference. The table below shows processing time per 4K frame when using `inference_realesrgan_video.py` with the `realesr-animevideov3` model.

| Mode | Avg time per 4K frame | Relative speed |
|------|----------------------|----------------|
| Eager | 98 ms | 1.0x |
| `torch.compile` | 82 ms | 1.2x |

Measured on an RTX 4090 with PyTorch 2.8 and CUDA 12.8 using a 3840×2160 input. Run:

```bash
python inference_realesrgan_video.py -i input.mp4 -n realesr-animevideov3 --compile
```

These numbers can vary with different models or hardware. Benchmark your own setup to verify performance.
