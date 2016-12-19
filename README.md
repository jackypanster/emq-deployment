### EMQ setup

#### Build Docker Image
```bash
git clone https://github.com/emqtt/emq_docker.git
vi Dockerfile
#add the following line
RUN apk add --update bash

cd emq_docker && docker build -t emq:latest .
```
