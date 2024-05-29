> On Github this is a mirror of a private Gitlab repo

![Image](ollama-s6.jpeg)

### Install NVIDIA Container Toolkit
> sudo pacman -S nvidia-container-toolkit 

> sudo nvidia-ctk runtime configure --runtime=docker 

> sudo systemctl restart docker



### Build ollama

> docker compose -f docker-compose-ci.yml build


### Run ollama

> docker compose up


### Prompr ollama

```
 curl http://localhost:11434/api/generate -d '{
  "model": "phi3",
  "prompt":"Why is the sky blue?"
}'
```
