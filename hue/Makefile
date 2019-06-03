up:
	mkdir data
	docker network create hadoop-net
	docker-compose up -d

down:
	docker-compose down
	docker network rm hadoop-net
	rm -rf data
