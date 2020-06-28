SHELL := /bin/bash

build-package:
	ng build
	
build-docker: build-package
	docker build -t vergeops/k8s-rvstore-ui:1.0 .
	
run-docker: stop-docker
	docker run -p 80:80 --name rvstore-ui --net k8s-rvstore vergeops/k8s-rvstore-ui:1.0

stop-docker:
	-docker stop rvstore-ui
	-docker rm rvstore-ui

push-docker:
	docker push vergeops/k8s-rvstore-ui:1.0

run-k8s:
	kubectl apply -f k8s/deployment.yaml
	kubectl apply -f k8s/service.yaml