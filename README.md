### EMQ setup

+ Build Docker Image

```bash
git clone https://github.com/emqtt/emq_docker.git

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
+ Verify

```bash
mosquitto_sub -h <IP_1> -p 80 -d -t 'test/topic' 
mosquitto_pub -h <IP_2> -p 80 -d -t 'test/topic' -m 'hello'
```
