SHELL := /bin/bash

create-network:
	docker network create k8s-rvstore

run-docker: stop-docker
	docker run --rm --net k8s-rvstore -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=secret --name rvstore-db mongo:latest

stop-docker:
	-docker stop rvstore-db
	-docker rm rvstore-db

run-k8s:
	kubectl apply -f k8s/configmap.yaml
	kubectl apply -f k8s/deployment.yaml
	kubectl apply -f k8s/service.yaml