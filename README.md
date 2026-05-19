Here's a bunch of setups I use on my PC for serving local LLM models via llama.cpp docker (Vulkan acceleration).

Hardware:
```
XFX Radeon RX 6600 (8GB GDDR6)
AMD Ryzen 5 5600 (6C/12T, 32MB L3 Cache, 3MB L2 Cache, no iGPU)
64 GiB of RAM (DDR4, 2x Kingston KF3200C16D4/32GX @ 3200 MTS)
```

You can copy-paste example compose.yml file and point mounts on your models directory (my directory structure is done by LM Studio)

------
Benchmark results for attached presets (from BENCHMARK_RUN.sh):


|file|model|tps|context|
|-|-|-|-|
|[qwen35_4b_q6_mtp_coding](qwen35_4b_q6_mtp_coding.yml)|[Qwen 3.5 4B Q6K](https://huggingface.co/unsloth/Qwen3.5-4B-MTP-GGUF)|57.96|150k|
|[qwen35_9b_q6_mtp_coding](qwen35_9b_q6_mtp_coding.yml)|[Qwen 3.5 9B Q6K](https://huggingface.co/unsloth/Qwen3.5-9B-MTP-GGUF)|13.11|150k|
|[qwen36_27b_q4_mtp_coding](qwen36_27b_q4_mtp_coding.yml)|[Qwen 3.6 27B Q4KM](https://huggingface.co/froggeric/Qwen3.6-27B-MTP-GGUF)|~ 3.40|150k|
|[qwen36_35b_q6_coding](qwen36_35b_q6_coding.yml)|[Qwen 3.6 35B A3B Q6K](https://huggingface.co/unsloth/Qwen3.6-35B-A3B-MTP-GGUF)|19.95|150k|