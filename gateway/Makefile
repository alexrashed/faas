TAG?=latest

.DEFAULT_GOAL := all

amd64-build:
	docker build --build-arg http_proxy="${http_proxy}" --build-arg https_proxy="${https_proxy}" -t alexrashed/gateway:$(TAG)-amd64 .

amd64-push:
	docker push alexrashed/gateway:$(TAG)-amd64

armhf-build:
	docker build --build-arg http_proxy="${http_proxy}" --build-arg https_proxy="${https_proxy}" -t alexrashed/gateway:$(TAG)-armhf . -f Dockerfile.armhf

armhf-push:
	docker push alexrashed/gateway:$(TAG)-armhf

arm64-build:
	docker build --build-arg http_proxy="${http_proxy}" --build-arg https_proxy="${https_proxy}" -t alexrashed/gateway:$(TAG)-arm64 . -f Dockerfile.arm64

arm64-push:
	docker push alexrashed/gateway:$(TAG)-arm64

multiarch-create:
	docker manifest create --amend alexrashed/gateway:$(TAG) alexrashed/gateway:$(TAG)-amd64 alexrashed/gateway:$(TAG)-armhf alexrashed/gateway:$(TAG)-arm64

multiarch-push: 
	docker manifest push alexrashed/gateway:$(TAG)

all: arm64-build amd64-build armhf-build arm64-push amd64-push armhf-push multiarch-create multiarch-push
