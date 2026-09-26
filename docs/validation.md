# Validation: one synthetic mannequin run

On 2026-09-26, one local run completed successfully and saved a 768 × 768 output. The beige dress became green. This establishes execution for these inputs, not production readiness or a general hardware benchmark.

## What ran

- Public graph: `workflows/low-budget/Qwen_Fashion_Edit_3060.json`, introduced in commit `dc911d9627f8017844b9b0f6d9dd206bb9e34569`; 19 nodes, 27 typed connections checked.
- Workflow file SHA-256: `a62b5c3a4815912f47320ff9790b5289bd982513205a381195de0c5a03ffcb76`.
- [Submitted API graph](../examples/test-api.json): node classes and links matched the public graph. Input filenames, the mannequin-specific instruction and output prefix were changed; model and sampler defaults were retained.
- This was a server API execution. Interactive drag-and-drop import and MaskEditor operation were not tested in this run.
- [Inputs, mask, prompt and result](../examples/README.md) are supplied. Source/reference were original synthetic assets, resized to 768 × 768. No client/model photographs were used.
- A binary polygon mask was encoded into inverse alpha on `source-masked.png`. This is a reproducible hand-defined mask, not automatic segmentation.

## Result and measurements

| Measure | Observed result |
| --- | --- |
| Runs | 1 completed, 0 failed; no retries or alternate output selection |
| Cold execution | 699.849 seconds (11m 39.849s), server execution-start to execution-success timestamps |
| Client wall time | 701.217 seconds, includes polling overhead |
| Peak total GPU memory used | 11.21 GiB |
| Peak ComfyUI process resident RAM | 18.04 GiB |
| Peak whole-system RAM used | 30.75 GiB |
| Output dimensions | 768 × 768 |
| Changed pixels outside binary mask | 0 (maximum channel difference 0) |
| Changed pixels inside mask | 89,163 of 89,245 |

Timing includes model loading, encoding, sampling, decoding and saving. No nodes were cached in the execution record. This was a fresh server process, not a controlled cold disk-cache benchmark. Model-load time was not measured separately; warm execution time is unknown.

Memory was sampled every second with NVML and psutil during the request. GPU usage covers the whole device, and whole-system RAM includes other applications; neither is an isolated workflow requirement. Process resident memory is not committed memory. Short-lived peaks can fall between samples. High system use means this result should not be read as a comfortable minimum-RAM specification.

## Visual findings

The output visibly follows the green color, short sleeves and round neckline of the reference. The mannequin, stand and background outside the mask are pixel-identical to the source. The image is an unretouched saved Qwen output.

Small beige remnants remain near the underarms and side outline. Garment edges are soft or clipped where the generated silhouette meets the binary mask. Fine texture and seam details are smoother/different from the product reference. The result is useful as a pipeline example but does not establish exact product fidelity. A better-reviewed mask and additional tests are needed before practical use.

This simplified headless mannequin does not test face identity, hands, hair, complex poses, occlusion, fabric logos, realistic fit on a person or batch reliability.

## Environment and settings

| Component | Tested value |
| --- | --- |
| OS | Windows-11-10.0.26200-SP0 |
| GPU | NVIDIA GeForce RTX 3060, 12 GB |
| System RAM | 32 GB installed class; 31.93 GiB reported available physical capacity |
| NVIDIA driver | 616.92 |
| Python / PyTorch | 3.13.14 / 2.13.0+cu130 |
| ComfyUI | 0.32.0; commit `c2bcbecd82ec5ae66594340b395c24ef0217b238` |
| Frontend | 1.48.7 |
| ComfyUI-GGUF | commit `6ea2651e7df66d7585f6ffee804b20e92fb38b8a` |
| Working-resolution setting | 0.5 megapixels, dimension multiple 32; final composite at source size |
| Sampler | Seed 20260915; 20 steps; CFG 4; Euler; simple scheduler; denoise 1.0 |
| Other settings | Sampling shift 3.1; CFG normalization 1.0; no LoRA; tiled VAE decode 512 with overlap 64 |

The launch used `--lowvram --preview-method none --listen 127.0.0.1 --port 8188 --disable-auto-launch --disable-metadata --disable-api-nodes --disable-all-custom-nodes --whitelist-custom-nodes ComfyUI-GGUF`. Input/output/temp/user folders were isolated for this test and the database used in-memory SQLite. `HF_HUB_OFFLINE=1`, `TRANSFORMERS_OFFLINE=1` and `HF_HUB_DISABLE_TELEMETRY=1` were set. These are test conditions, not a complete environment lock or a network-isolation guarantee.

The console reported dynamic model offloading. Other custom extensions were disabled for this test. Repeating it with a different runtime or active extensions may change behavior and resource use.

## Model file identity

Sources are documented in [model downloads](model-downloads.md). The exact downloaded repository revisions were not captured; these SHA-256 values identify the local files that ran.

| Filename | SHA-256 |
| --- | --- |
| `qwen-image-edit-2511-Q4_K_M.gguf` | `8677bac90627adbbc11efab87b1870e701c4eb3689ee865a3de8ab81b705a723` |
| `qwen_2.5_vl_7b_fp8_scaled.safetensors` | `cb5636d852a0ea6a9075ab1bef496c0db7aef13c02350571e388aea959c5c0b4` |
| `qwen_image_vae.safetensors` | `a70580f0213e67967ee9c95f05bb400e8fb08307e017a924bf3441223e023d1f` |

## Still pending

- Repeated warm runs, median timings and isolated memory measurements.
- Interactive UI import and mask-painting verification.
- More garments, poses, texture/pattern fidelity and mask-boundary evaluation.
- The same controlled workload on higher-memory GPUs; other platforms and lower-memory cards.
- A clean-environment installation test and dependency lock.

The front-page concept illustration and technology banner were created separately with an image-generation tool. They are decorative/explanatory assets, not test evidence. [Asset provenance](../ASSET-MANIFEST.md).
