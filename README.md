> On Github this is a mirror of a private Gitlab repo

![Image](ollama-s6.jpeg)

### Install NVIDIA Container Toolkit
> sudo pacman -S nvidia-container-toolkit 

> sudo nvidia-ctk runtime configure --runtime=docker 

> sudo systemctl restart docker


### ENV VARS

> LLM_MODEL=phi3 # set any model supported by Ollama
> OLLAMA_MEM_MIN=4G # set minimum memory for container 
> OLLAMA_MEM_MAX=8G # set maximum memory for container


### Build ollama

> docker compose -f docker-compose-ci.yml build


### Run ollama

> docker compose up


### Prompt ollama

```
 curl http://localhost:11434/api/generate -d '{
  "model": "phi3",
  "prompt":"Why is the sky blue?"
}'
```
