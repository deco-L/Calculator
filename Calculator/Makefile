SHELL = bash

SRC = ./src

all: stop build run

build:
	docker build \
	-f $(SRC)/Dockerfile \
	--build-arg HTTP_PROXY=${HTTP_PROXY} \
	--build-arg HTTPS_PROXY=${HTTPS_PROXY} \
	-t calculator ${SRC}

run:
	docker run -d -p 3000:3000 --name calculator_container calculator

stop:
	docker stop calculator_container || true
	docker rm calculator_container || true

clean: stop
	docker rmi calculator || true

.PHONY: all build run stop clean
