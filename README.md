# llama.cpp RTX 5060 Ti 16 GB presets

Presets for running Qwen3.8-27B with an ASCII-condensed vocabulary on an NVIDIA RTX 5060 Ti 16 GB.

## Models

Download the target for your chosen preset and the matching draft:

| Preset | Target model |
| --- | --- |
| [50K](rtx-5060-ti-16gb/qwen3.8-iq4xs-27b-ascii-dflash4-50k.ini) | [ASCII-condensed UD-IQ4_XS](https://huggingface.co/bsaleh03/Qwen3.8-27B-ASCII-Condensed)  |
| [100K](rtx-5060-ti-16gb/qwen3.8-q3kxl-27b-ascii-dflash4-100k.ini) | [ASCII-condensed UD-Q3_K_XL v3](https://huggingface.co/Blazestorm001/Qwen3.8-27B-ASCII-Condensed-UD-Q3_K_XL-GGUF) |

Both presets use the [ASCII-condensed DFlash2 Q2_K draft](https://huggingface.co/Blazestorm001/Qwen3.8-27B-ASCII-Condensed-DFlash2-GGUF).

## Build llama.cpp

Follow the [official CUDA build instructions](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#cuda).

The local setup used CUDA build 10807, reporting [commit `163a40796`](https://github.com/ggml-org/llama.cpp/commit/163a40796), with CUDA architectures 75 and 120. Your build must support `draft-dflash` and the options in these presets.

## Launch

Edit `model` and `spec-draft-model` in your chosen INI to point to the downloaded GGUF files. The presets use `CUDA0`; change `device` and `spec-draft-device` if your GPU has a different device index.

From this presets repository directory, launch with your CUDA-enabled binary:

```sh
/path/to/llama.cpp/build/bin/llama-server --models-preset rtx-5060-ti-16gb/qwen3.8-q3kxl-27b-ascii-dflash4-100k.ini
```

Credits: [Qwen](https://huggingface.co/Qwen/Qwen3.8-27B), [Unsloth](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF), and [bsaleh03](https://huggingface.co/bsaleh03/Qwen3.8-27B-ASCII-Condensed) for the ASCII pruning approach and IQ4_XS target.
