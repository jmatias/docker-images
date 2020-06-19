default: docker_build

DOCKER_IMAGE ?= jlmatias/helm-kubectl
DOCKER_TAG ?= 0.1.0
VCS_REF ?= $(DOCKER_TAG)

docker_build:
	docker build \
	  --build-arg VCS_REF=`git rev-parse --short HEAD` \
	  --build-arg BUILD_DATE=`date -u +"%Y-%m-%dT%H:%M:%SZ"` \
	  -t $(DOCKER_IMAGE):$(DOCKER_TAG) -t $(DOCKER_IMAGE):latest  .

docker-push:
	# Push to DockerHub
	docker push $(DOCKER_IMAGE):$(DOCKER_TAG)