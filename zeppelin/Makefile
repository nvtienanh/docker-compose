ZEPPELIN_TAG := 0.8.1
up:
	mkdir -p data
	mkdir -p notebook
	docker network create spark-net
	docker-compose up -d

down:
	docker-compose down
	docker network rm spark-net
	# rm -rf data
	# rm -rf notebook

push:
	docker push nvtienanh/zeppelin:$(ZEPPELIN_TAG)
