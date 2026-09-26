# Installation

This repository includes an experimental workflow JSON, not an installer. One synthetic mannequin API run completed on RTX 3060 12 GB; see [validation](validation.md) for tested conditions and remaining limits.

1. Install ComfyUI using the [official Windows portable guide](https://docs.comfy.org/installation/comfyui_portable_windows) or [manual installation guide](https://docs.comfy.org/installation/manual_install). Keep the installation outside this repository.
2. Check that ComfyUI detects your GPU. The budget target is an RTX 3060 **12 GB**, not the 8 GB variant; memory fit is not guaranteed.
3. Install [ComfyUI-GGUF](https://github.com/city96/ComfyUI-GGUF) according to its README. Use the Python environment belonging to ComfyUI when installing its requirements. Restart ComfyUI afterward.
4. Download the exact files listed in [model downloads](model-downloads.md) into their matching folders.
5. Download [Qwen_Fashion_Edit_3060.json](../workflows/low-budget/Qwen_Fashion_Edit_3060.json) and drag it onto ComfyUI. Select your model filenames in the three loader nodes.
6. Supply a source photo and garment reference, paint the source clothing mask, and follow the [workflow guide](../workflows/low-budget/README.md).

For a Windows portable installation, a low-memory launch command from the portable root is:

```bat
python_embeded\python.exe -s ComfyUI\main.py --windows-standalone-build --lowvram --preview-method none --listen 127.0.0.1 --port 8188
```

Open the local address printed by ComfyUI. Do not start a second instance on the same port. The supplied graph uses local model nodes; third-party extensions may have separate network behavior. Cloud instances process uploaded inputs remotely.

Missing `TextEncodeQwenImageEditPlus`, `CFGNorm` or `FluxKontextMultiReferenceLatentMethod` means the installed ComfyUI version needs review. Missing `UnetLoaderGGUF` means the GGUF extension did not load. Consult startup errors and [troubleshooting](troubleshooting.md).

Before reporting a successful run, record OS, GPU/VRAM, RAM, driver, Python/PyTorch versions, ComfyUI and custom-node commits, model revisions/hashes, dimensions, seed and all sampler/offload settings. No reproducible environment lock or performance certification is supplied yet.
