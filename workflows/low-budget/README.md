# Qwen fashion edit: experimental low-budget baseline

[Download the workflow JSON](Qwen_Fashion_Edit_3060.json) using GitHub's Download raw file button, then drag it into ComfyUI.

This graph uses a source photo, a garment reference and a hand-painted clothing mask. It targets experiments on an RTX 3060 12 GB with offloading. It is an experimental graph, not a benchmarked or production-ready recipe. No demo images are included.

## Dependencies

- ComfyUI with `TextEncodeQwenImageEditPlus`, `CFGNorm` and `FluxKontextMultiReferenceLatentMethod`.
- [city96/ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF) for `UnetLoaderGGUF`; follow its installation instructions using ComfyUI's own Python environment.
- The three exact model files listed in [model downloads](../../docs/model-downloads.md). No LoRA is used.

## Run one edit

1. Select the installed GGUF, text encoder and VAE in the loader nodes.
2. In node 1, upload a source photo you own or have permission to edit.
3. In node 2, upload an everyday garment product reference.
4. Right-click the source image and open MaskEditor. Paint the clothing region that should change, leaving the face, hair and background outside it; save the mask.
5. Review the general fashion instruction in node 9 and run one image.
6. Inspect the output in ComfyUI's output folder under `Qwen_Fashion_Edit`. Check seams, texture, color, silhouette and mask boundaries before use.

Defaults: 0.5 megapixels (dimension multiple 32), seed 20260915, 20 steps, CFG 4, Euler/simple, denoise 1.0, sampling shift 3.1, CFG normalization 1.0, tiled VAE decode 512/64. The second reference is not explicitly resized by this graph; start with a modest-size image.

The final composite keeps the source dimensions. Pixels where the mask equals zero come from the source; soft edges blend. The generated region is resized from working resolution, so this is not native high-resolution generation. An empty mask returns an unchanged source image. A larger new garment needs a mask covering its intended outline.

## Validation status

The public JSON passed structural and typed-link checks on 2026-09-26. Earlier local setup checks recognized the baseline's model files and graph inputs, reporting only the two missing input images. This is not a successful inference test. The sanitized public graph still needs an end-to-end run with cleared demo inputs, environment/model revision capture, quality review, peak VRAM/RAM and timings before it can be described as tested.

Use this for ordinary fashion and e-commerce work with permission. Keep private assets and commercial workflows outside this repository.
