ALPINE_VERSION := 3.19.1
JAVA_VERSION := 8
DOCKER_REGISTRY_HUB := docker.io
DOCKER_REGISTRY_PRE := pre.azurecr.io
DOCKER_REGISTRY_PFM := pfm.azurecr.io
DOCKER_REGISTRY_PRO := pro.azurecr.io
DOCKER_IMAGE := openjdk

all: build test

build: clean-pre
	docker build -t $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) --build-arg ALPINE_VERSION=$(ALPINE_VERSION) --build-arg JAVA_VERSION=$(JAVA_VERSION) .

test:
	docker image inspect $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)
	docker run --rm --entrypoint java $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) -version

run:
	docker run -t -i --rm --entrypoint /bin/sh $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

clean-hub:
	docker image rm $(DOCKER_REGISTRY_HUB)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) > /dev/null 2>&1 || true

clean-pre:
	docker image rm $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) > /dev/null 2>&1 || true

clean-pfm:
	docker image rm $(DOCKER_REGISTRY_PFM)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) > /dev/null 2>&1 || true

clean-pro:
	docker image rm $(DOCKER_REGISTRY_PRO)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) > /dev/null 2>&1 || true

clean: clean-pre clean-pfm clean-pro

pull-hub: clean-hub
	docker pull $(DOCKER_REGISTRY_HUB)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

pull-pre: clean-pre
	docker pull $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

pull-pfm: clean-pfm
	docker pull $(DOCKER_REGISTRY_PFM)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

pull-pro: clean-pro
	docker pull $(DOCKER_REGISTRY_PRO)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

push-hub: clean-hub
	docker tag $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) $(DOCKER_REGISTRY_HUB)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)
	docker push $(DOCKER_REGISTRY_HUB)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

push-pre:
	docker push $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

push-pfm: clean-pfm
	docker tag $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) $(DOCKER_REGISTRY_PFM)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)
	docker push $(DOCKER_REGISTRY_PFM)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

push-pro: clean-pro
	docker tag $(DOCKER_REGISTRY_PRE)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION) $(DOCKER_REGISTRY_PRO)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)
	docker push $(DOCKER_REGISTRY_PRO)/$(DOCKER_IMAGE):$(JAVA_VERSION)-alpine$(ALPINE_VERSION)

# vim:ft=make
