> On Github this is a mirror of a private Gitlab repo

![Image](ollama-s6.jpeg)

### Install NVIDIA Container Toolkit
> sudo pacman -S nvidia-container-toolkit 

> sudo nvidia-ctk runtime configure --runtime=containerd

> sudo systemctl restart nerdctl


### ENV VARS

> OLLAMA_LLM_MODEL=qwen2:1.5b # set any model supported by Ollama

> OLAMA_LLM_EMBED=nomic-embed-text # embedding generating model

> OLLAMA_MEM_MIN=4G # set minimum memory for container 

> OLLAMA_MEM_MAX=8G # set maximum memory for container

> OLLAMA_GPU_DRIVER=nvidia # to run with Nvidia GPU 

> OLLAMA_GPU_COUNT=1 # no. of GPUs available

### Build ollama

> nerdctl compose -f docker-compose-ci.yml build


### Run ollama

> nerdctl compose up


### Prompt ollama

```
 curl http://localhost:11434/api/generate -d '{
  "model": "qwen2:1.5b",
  "prompt":"Why is the sky blue?"
}'
```

### OLLAMA WEB UI

- Open Web UI is added to use with Ollama
