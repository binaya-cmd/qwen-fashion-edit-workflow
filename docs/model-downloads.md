# Model downloads
No weights are included. Download into ComfyUI outside this repository.

The selected reference is Qwen-Image-Edit-2511, not a claim of latest-model status or 12 GB compatibility. Use the exact links in the [official ComfyUI tutorial](https://docs.comfy.org/tutorials/image/qwen/qwen-image-edit-2511).

| Component | Filename | ComfyUI folder |
| --- | --- | --- |
| Diffusion model | qwen_image_edit_2511_bf16.safetensors | models/diffusion_models/ |
| Text encoder | qwen_2.5_vl_7b_fp8_scaled.safetensors | models/text_encoders/ |
| VAE | qwen_image_vae.safetensors | models/vae/ |

Upstream sources: [Qwen model card](https://huggingface.co/Qwen/Qwen-Image-Edit-2511), [Comfy-Org edit packaging](https://huggingface.co/Comfy-Org/Qwen-Image-Edit_ComfyUI), [shared components](https://huggingface.co/Comfy-Org/Qwen-Image_ComfyUI).

The tutorial also links an optional Lightning LoRA. It is separately maintained; review its source/license and use only its matching model and settings. Do not mix 2509 and 2511 components without explicit compatibility guidance.

## Budget variants
No quantized variant or custom loader is validated here. Full BF16 is not a promised 12 GB recipe. Reduced precision may require different loaders and custom nodes. Do not rename GGUF files to fit a loader.

## Download checks
Check repository owner, exact filename, size, revision, model card, and license for every component. Record its source URL and revision. Compare SHA-256 against a trusted upstream checksum where available; a locally calculated hash alone does not establish provenance. Refresh or restart ComfyUI after placing files and select the correct filenames.

References checked on 2026-09-22. External models and software retain their own licenses.
