> On Github this is a mirror of a private Gitlab repo

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

### Build ollama

> nerdctl compose -f docker-compose-ci.yml build


### Run ollama

> nerdctl -f docker-compose.yml compose up #CPU only

> nerdctl -f docker-compose.yml -f docker-compose-gpu.yml compose up #GPU support


### Prompt ollama

```
 curl http://localhost:11434/api/generate -d '{
  "model": "qwen2:1.5b",
  "prompt":"Why is the sky blue?"
}'
```

### OLLAMA WEB UI

- Open Web UI is added to use with Ollama
