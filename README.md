### EMQ setup

+ Build Docker Image

```bash
git clone https://github.com/emqtt/emq_docker.git
vi Dockerfile
#add the following line
RUN apk add --update bash

cd emq_docker && sudo docker build -t emq:latest .
```
+ Run the image

```bash
sudo docker run --restart=always -itd --net='host' -e 'EMQ_TCP_PORT=80' -e 'EMQ_NAME=emqttd' -e 'EMQ_HOST=<IP>'  --name emq emq:latest
```

+ Or build from source code

```bash
git clone https://github.com/emqtt/emq-relx.git
cd emq-relx && make
cd _rel/emqttd && ./bin/emqttd console
```

+ Set up the cluster

```bash
./bin/emqttd_ctl cluster join emqttd@<IP>
```
