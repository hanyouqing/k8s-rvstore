SHELL := /bin/bash

build-package:
	mvn package
	
build-docker:
	docker build -t vergeops/k8s-rvstore-order-api:1.0 .
	
run-docker:
	-docker stop rvstore-order-api
	-docker rm rvstore-order-api
	docker run -p 9002:9002 --net k8s-rvstore --name rvstore-order-api vergeops/k8s-rvstore-order-api:1.0
	
push-docker:
	docker push vergeops/k8s-rvstore-order-api:1.0