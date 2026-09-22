# Installation
This repository is documentation, not a ComfyUI installer or executable workflow.

## Windows with NVIDIA
1. Check GPU memory and driver status in your system tools or with `nvidia-smi`.
2. Follow the [official Windows portable guide](https://docs.comfy.org/installation/comfyui_portable_windows). Download the matching build from its official links and extract it outside this repository.
3. Start the packaged NVIDIA launcher as directed by that guide. Open the local address printed by ComfyUI.
4. Confirm the console detects the GPU before downloading models.

## Linux, macOS, or an existing Python environment
Use the [official manual installation guide](https://docs.comfy.org/installation/manual_install) for the appropriate Python, PyTorch, and accelerator combination. Use an isolated environment. This starter has not validated non-NVIDIA hardware or a specific dependency lock.

## Load an upstream reference
1. Update ComfyUI using the instructions for your installation type; keep a backup of any existing working setup.
2. Open Workflow Templates and search for **Qwen-Image-Edit-2511**, or use the template linked in the [official tutorial](https://docs.comfy.org/tutorials/image/qwen/qwen-image-edit-2511).
3. Read the selected graph before running it. It is an upstream material-edit example, not this project's tested fashion workflow.
4. Install the matching files from [model downloads](model-downloads.md). Select the exact filenames in the loaders.
5. Replace every input with a non-sensitive image you created. Keep outputs outside this repository.
6. Start at batch size 1. Preserve the template's matching sampler and model settings initially; smaller image dimensions may reduce memory demand.
7. Queue one run. Check the output and console before changing one setting at a time.

The full reference model is not a promised 12 GB recipe. Consult the [low-budget placeholder](../workflows/low-budget/README.md) before trying that route.

## Local and remote operation
Local processing requires local model nodes; API nodes and third-party extensions may contact external services. Inspect the graph and extensions. Keep ComfyUI bound locally unless you have configured authenticated remote access. A cloud GPU receives the uploaded inputs; use non-sensitive demos for initial testing.

## Record a working environment
Record OS, GPU/VRAM, driver, Python/PyTorch versions, ComfyUI commit or release, custom-node versions (if any), model revision and hash, graph revision, dimensions, seed, sampler, steps, precision, and offload settings. No working combination is certified by this starter yet.
