# Human example: simple dress to party dress

> Historical 0.5 MP / 20-step baseline report. The current main canvas has been revised to 1 MP / 40 steps, reference detail and separate masks; the settings and hashes below describe the recorded earlier test.


One actual local Qwen run completed on 2026-09-26 using a newly generated fictional adult and a separately generated party-dress reference. No client photographs, private model images or real-person references were used.

[View before / reference / actual result](../examples/HUMAN-PARTY.md). The saved output is unretouched. The earlier [mannequin report](validation.md) is a separate test.

## Test conditions

This test used the same public baseline graph, model files, software environment and launch settings documented in [the mannequin report](validation.md#environment-and-settings). Model SHA-256 hashes are listed [there](validation.md#model-file-identity). The server was restarted before this run. No hardware-comparison claim is made.

Only source/reference filenames, the fashion instruction and output prefix changed. A comparison of both API graphs confirmed every other input and node class was unchanged. This is an API execution of the public graph, not verification of interactive canvas import or MaskEditor operation.

- GPU: NVIDIA RTX 3060 12 GB; 32 GB system RAM class; Windows 11.
- ComfyUI 0.32.0; Python 3.13.14; PyTorch 2.13.0+cu130; NVIDIA driver 616.92.
- Q4_K_M GGUF diffusion model, FP8 text/image encoder, Qwen VAE; no LoRA.
- Source and reference: 768 × 768; working-resolution setting 0.5 MP, multiple 32.
- Seed 20260915, 20 steps, CFG 4, Euler/simple, denoise 1, shift 3.1, CFG normalization 1.0; tiled VAE decode 512/64.
- Clothing mask: manually defined binary polygon, stored as inverse alpha in `human-source-masked.png`. The final composite retains source pixels wherever the mask is zero.
- Launch: low-VRAM mode, previews disabled, only ComfyUI-GGUF custom nodes enabled; metadata embedding disabled; isolated input/output folders and in-memory SQLite. Same offline/telemetry environment flags as the mannequin run.

## Measurements

| Measure | Observed result |
| --- | --- |
| Attempts for this example | 1 completed run; no alternate output selection |
| Server execution time | 641.296 seconds (10m 41.3s), includes model loading |
| Client wall time | 645.612 seconds, includes polling overhead |
| Peak whole-device GPU memory used | 11.32 GiB |
| Peak ComfyUI resident RAM | 18.04 GiB |
| Peak whole-system RAM used | 30.48 GiB |
| Output dimensions | 768 × 768 |
| Changed pixels outside mask | 0 |
| Maximum channel difference outside mask | 0 on an 8-bit RGB scale |
| Changed pixels within mask | 59,090 / 59,092 |
| Head-region maximum channel difference | 0 (top 130 rows, including hair and face) |

Memory was sampled every second with NVML and psutil. GPU and whole-system values include other applications; process resident memory is not committed memory. Short peaks can be missed. These figures are observations, not minimum hardware requirements. Timing includes loading, encoding, sampling, decoding and saving; no warm-run median or isolated loading time was measured. OS disk cache was not controlled.

## Visual review

The plain beige dress changed to a dark midnight-blue satin-style party dress, with short sleeves, a fitted waist, matching waistband, stronger skirt folds and a sparkling hem treatment. The face, hair, hands and other pixels outside the mask were unchanged in the saved 8-bit RGB image.

The reference's silver botanical embroidery on the bodice is largely missing. Its detailed botanical hem pattern became a simpler band of small light speckles. The skirt retains the source-constrained silhouette rather than reproducing the wider reference exactly. Thin beige remnants and soft transitions remain around parts of the neckline, shoulders/sleeves and side boundaries. The satin highlights and broad party-dress appearance transferred, but the result is not a faithful product replica. It is suitable as an honest experimental demonstration, not an exact catalogue reconstruction.


Preservation of unmasked pixels is a result of compositing. It does not prove the generative model independently preserves identity. The mask constrains the silhouette and excludes the face, exposed limbs and shoes; a substantially different cut or skirt shape needs a revised mask. This single front-facing synthetic example does not validate arbitrary people, poses, occlusions or exact product reconstruction.

## Reproduction and provenance

[human-test-api.json](../examples/human-test-api.json) contains the exact submitted instruction and settings. [HUMAN-PARTY.md](../examples/HUMAN-PARTY.md) includes source-generation prompts and input/mask usage. Use the ordinary public UI JSON for the canvas; API JSON is a different format.

Still pending: interactive import/mask-painting checks, more poses and garment styles, refined mask edges, repeated warm timings, clean-install validation and higher-memory hardware comparisons.
