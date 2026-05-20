Here's a bunch of setups I use on my PC for serving local LLM models via llama.cpp docker (Vulkan acceleration).

Hardware:
```
XFX Radeon RX 6600 (8GB GDDR6)
AMD Ryzen 5 5600 (6C/12T, 32MB L3 Cache, 3MB L2 Cache, no iGPU)
ASUS ROG Strix X570-I Gaming
64 GiB of RAM (DDR4, 2x Kingston KF3200C16D4/32GX @ 3200 MTS)
```

You can copy-paste example compose.yml file and point mounts on your models directory (my directory structure is done by LM Studio)

Then rename preset file to `compose.override.yml` so it sets parameters for container while you run `docker compose up`

------
Benchmark results for attached presets (from BENCHMARK_RUN.sh):


|file|model|tps|context|
|-|-|-|-|
|[gemma4_26b_q6](gemma4_26b_q6.yml)|[Gemma 4 26B A4B Q6K](https://huggingface.co/llmfan46/gemma-4-26B-A4B-it-uncensored-heretic-GGUF)|15.34|200k|
|[gemma4_31b_q6](gemma4_31b_q6.yml)|[Gemma 4 31B Q6K](https://huggingface.co/llmfan46/gemma-4-31B-it-uncensored-heretic-GGUF)|TODO (+- 1.5)|200k|
|[gemma4_e2b_q6](gemma4_e2b_q6.yml)|[Gemma 4 E2B Q6K](https://huggingface.co/HauhauCS/Gemma-4-E2B-Uncensored-HauhauCS-Aggressive)|77.77|200k|
|[gemma4_e4b_q4_vision](gemma4_e4b_q4_vision.yml)|[Gemma 4 E4B Q4KM](https://huggingface.co/HauhauCS/Gemma-4-E4B-Uncensored-HauhauCS-Aggressive)|52.31|128k|
|[qwen35_4b_q6_mtp_coding](qwen35_4b_q6_mtp_coding.yml)|[Qwen 3.5 4B Q6K](https://huggingface.co/unsloth/Qwen3.5-4B-MTP-GGUF)|58.34|150k|
|[qwen35_9b_q6_mtp_coding](qwen35_9b_q6_mtp_coding.yml)|[Qwen 3.5 9B Q6K](https://huggingface.co/unsloth/Qwen3.5-9B-MTP-GGUF)|19.58|150k|
|[qwen36_27b_q4_mtp_coding](qwen36_27b_q4_mtp_coding.yml)|[Qwen 3.6 27B Q4KM](https://huggingface.co/froggeric/Qwen3.6-27B-MTP-GGUF)|3.65|150k|
|[qwen36_35b_q6_coding](qwen36_35b_q6_coding.yml)|[Qwen 3.6 35B A3B Q6K](https://huggingface.co/unsloth/Qwen3.6-35B-A3B-MTP-GGUF)|20.69|150k|