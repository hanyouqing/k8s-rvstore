SHELL := /bin/bash

build:
	go build

build-docker: build
	docker build -t vergeops/k8s-rvstore-product-api:1.0 .
	
run-docker: stop-docker
	docker run  -p 9001:9001 --net k8s-rvstore  --name rvstore-product-api vergeops/k8s-rvstore-product-api:1.0

stop-docker:
	-docker stop rvstore-product-api
	-docker rm rvstore-product-api
	
push-docker:
	docker push vergeops/k8s-rvstore-product-api:1.0

run-k8s:
	kubectl apply -f k8s/deployment.yaml
	kubectl apply -f k8s/service.yaml