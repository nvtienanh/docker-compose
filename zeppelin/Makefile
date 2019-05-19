ZEPPELIN_TAG := 0.8.1
up:
	docker network create spark-net
	docker-compose up -d

down:
	docker-compose down
	docker network rm spark-net

bash:
	docker exec -it docker-zeppelin_zeppelin_1 bash

build:
	docker build -t nvtienanh/zeppelin:$(ZEPPELIN_TAG) ./zeppelin/.

push:
	docker push nvtienanh/zeppelin:$(ZEPPELIN_TAG)
