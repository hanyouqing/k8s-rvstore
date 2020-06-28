SHELL := /bin/bash

build-package:
	mvn package
	
build-docker:
	docker build -t vergeops/k8s-rvstore-order-api:1.0 .
	
run-docker:stop-docker
	docker run -p 9002:9002 --net k8s-rvstore --name rvstore-order-api vergeops/k8s-rvstore-order-api:1.0

stop-docker:
	-docker stop rvstore-order-api
	-docker rm rvstore-order-api

push-docker:
	docker push vergeops/k8s-rvstore-order-api:1.0

run-k8s:
	kubectl apply -f k8s/deployment.yaml
	kubectl apply -f k8s/service.yaml