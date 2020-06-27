SHELL := /bin/bash

create-network:
	docker network create k8s-rvstore

run-mongo:
	-docker rm -f rvstore-db
	docker run --rm --net k8s-rvstore -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=secret --name rvstore-db mongo:latest