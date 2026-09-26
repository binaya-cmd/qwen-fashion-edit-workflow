# Model downloads

No weights are included. Place downloads inside ComfyUI, outside this repository.

## Public low-budget graph

| Component | Exact filename | ComfyUI folder | Source |
| --- | --- | --- | --- |
| GGUF diffusion model | `qwen-image-edit-2511-Q4_K_M.gguf` | `models/diffusion_models/` | [Unsloth GGUF packaging](https://huggingface.co/unsloth/Qwen-Image-Edit-2511-GGUF) |
| Text/image encoder | `qwen_2.5_vl_7b_fp8_scaled.safetensors` | `models/text_encoders/` | [Comfy-Org components](https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/tree/main/split_files/text_encoders) |
| VAE | `qwen_image_vae.safetensors` | `models/vae/` | [Comfy-Org components](https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI/tree/main/split_files/vae) |

The GGUF is third-party quantized packaging, loaded by [city96/ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF). Do not rename a GGUF to a safetensors filename. No LoRA is needed by this graph. Source links identify the selected family, not the latest or best model.

Upstream references: [Qwen model card](https://huggingface.co/Qwen/Qwen-Image-Edit-2511) and [official ComfyUI tutorial](https://docs.comfy.org/tutorials/image/qwen/qwen-image-edit-2511). The tutorial's full BF16 model is an alternative reference requiring a different loader; it is not a drop-in replacement for this GGUF graph or a promised 12 GB recipe.

Review each source's license, exact filename, size and revision before downloading. Record revision and SHA-256, comparing against a trusted upstream checksum where available. A local hash alone does not establish provenance. Restart or refresh ComfyUI and select the exact model filenames.

These local files were used in one completed synthetic mannequin test. See [validation](validation.md) for their SHA-256 hashes, measured memory/time and visual limitations. External models and software retain their own licenses.
