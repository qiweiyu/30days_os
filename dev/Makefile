ROOT_DIR=$(shell cd .. && pwd)

setup:
	docker build -f ./Dockerfile -t os_dev .

build:
	docker run --rm -v $(ROOT_DIR)/src:/data os_dev /bin/build.sh
