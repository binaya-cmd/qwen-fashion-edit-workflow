# Qwen fashion edit — 1 MP / 40 steps

[Download the main workflow JSON](Qwen_Fashion_Edit_3060.json) using **Download raw file**, then drag it into ComfyUI. The main download already includes the detail-reference input and separate generation/blend masks; no API graph is needed for this setup.

## Dependencies

Install ComfyUI with Qwen Image Edit 2511 nodes and [ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF). Obtain the three exact files in [model downloads](../../docs/model-downloads.md). No LoRA is used. See [installation](../../docs/installation.md).

## Run one edit

1. **Node 1:** load your source photo and use **MaskEditor** to paint the generation mask. Cover both the old outfit and intended target silhouette; protect the face and hands where possible.
2. **Node 2:** load the full target garment reference. Its design and length guide the output.
3. **Node 20:** load a close-up of details from that same reference. If no detail crop is available, load the full reference again.
4. **Node 21:** load the **same source photo/crop, with exactly the same dimensions and alignment**, and paint a separate blend mask in MaskEditor. This controls which generated pixels appear in the final image. Include areas needed to remove the old garment; carefully refine boundaries near hands and hems.
5. Save both masks. These nodes use **alpha masks**: an ordinary RGB black-and-white mask PNG does not work as the LoadImage MASK output. Use MaskEditor or a correctly prepared alpha-bearing source image.
6. Review the instruction in **node 9**. Defaults are **1 MP, 40 steps, CFG 4, Euler/simple, denoise 1**, one image. Select the installed model files and press **Run**.
7. Inspect the output saved under `Qwen_Fashion_Edit`. Refine masks and use targeted inpainting if edges or garment details need correction. Exact reproduction is not guaranteed.

For small garment details, manually prepare a tight source crop before loading it into nodes 1 and 21. This graph saves at the supplied source dimensions; it does not automatically crop, stitch into a full photograph, or run a second repair pass. An empty blend mask returns the unchanged source. Proper masks and inpainting improve results but cannot guarantee a perfect match.

Other defaults: seed 20260915, resolution multiple 32, sampling shift 3.1, CFG normalization 1.0, tiled VAE decode 512/64. Reference files are not explicitly resized by this graph; use sensible image sizes. Zero blend-mask pixels retain the source; soft mask edges blend.

## Validation and example provenance

This revised canvas JSON passed parsing, typed-link, dependency-order and installed-node schema checks on 2026-09-26. No new inference or interactive mask-painting test was run for this assembled export. The [recorded quality experiment](../../docs/quality-validation.md) tested 1 MP / 40 steps with reference detail and separate masks, plus manual crop assembly and a second repair pass. Its timings and final image do not describe a single run of this canvas.

Earlier 0.5 MP / 20-step runs are historical baselines. The front-page party-dress preview is separately retouched, not an unretouched output or a quality guarantee. Use your own permitted images; keep private assets outside this repository.
