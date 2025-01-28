[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

![Image](ollama-s6.jpeg)

### Install NVIDIA Container Toolkit
> sudo pacman -S nvidia-container-toolkit 

> sudo nvidia-ctk runtime configure --runtime=containerd

> sudo systemctl restart nerdctl


### ENV VARS

> OLLAMA_LLM_MODEL=nomic-embed-text,qwen2:1.5b # set list of any model supported by Ollama

> OLLAMA_MEM_MIN=4G # set minimum memory for container 

> OLLAMA_MEM_MAX=8G # set maximum memory for container

> OLLAMA_GPU_DRIVER=nvidia # to run with Nvidia GPU 

> OLLAMA_GPU_COUNT=1 # no. of GPUs available

`https://smcleod.net/2024/12/bringing-k/v-context-quantisation-to-ollama/`

> OLLAMA_FLASH_ATTENTION="1"

> OLLAMA_KV_CACHE_TYPE="q8_0" # fp16. q8_0, q4_0

### Build ollama

> nerdctl compose -f docker-compose-ci.yml build


### Run ollama

> nerdctl compose -f docker-compose.yml up #CPU only

> nerdctl compose -f docker-compose.yml -f docker-compose-gpu.yml up #GPU support


### Prompt ollama

```
 curl http://localhost:11434/api/generate -d '{
  "model": "qwen2:1.5b",
  "prompt":"Why is the sky blue?"
}'
```

### OLLAMA WEB UI

- Open Web UI is added to use with Ollama
