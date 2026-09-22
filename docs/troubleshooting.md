# Troubleshooting
| Symptom | First checks |
| --- | --- |
| GPU out of memory | Batch 1; close other GPU jobs; reduce dimensions; check actual VRAM. Full BF16 is not a validated budget path. |
| System RAM exhausted | Inspect RAM and paging during offloading; reduce the workload or use more suitable hardware. |
| Model missing | Check folder, filename, completed download, and loader; refresh/restart. |
| Missing core nodes | Update ComfyUI through its official install method; inspect startup errors. Stable releases may lag new templates. |
| Missing custom nodes | Check the graph's actual dependency documentation before installing extensions. |
| Shape/type mismatch | Verify model family, precision, encoder, VAE, loader, and optional LoRA match the graph. |
| Slow generation | Separate cold loading from warm runs; inspect CPU fallback and offloading. |
| Garment/identity drift | Reduce edit scope, compare against the original, and reject misleading outputs. |
| Broken logos/text/texture | Inspect at full size; generated edits do not guarantee faithful product details. |
| Launcher exits | Read the first console error and check driver/runtime compatibility against the official installation guide. |

For public issues, provide sanitized error text, versions, model filenames, GPU/VRAM, dimensions, and a safe reproduction. Remove tokens, private paths, client names, confidential prompts, and embedded workflow data.

See [installation](installation.md) and the [official tutorial](https://docs.comfy.org/tutorials/image/qwen/qwen-image-edit-2511).
