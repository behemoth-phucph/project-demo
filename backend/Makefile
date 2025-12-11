IMAGE_NAME := us-east1-docker.pkg.dev/project-demo-480213/demo-1/docker/backend-rails

TAG := $(shell git rev-parse --short HEAD)

.PHONY: build push auth

build:
	docker build --platform linux/amd64 -t $(IMAGE_NAME):$(TAG) .
	docker tag $(IMAGE_NAME):$(TAG) $(IMAGE_NAME):latest

# Ensure Docker is configured to authenticate with Artifact Registry before pushing
push: auth
	docker push $(IMAGE_NAME):$(TAG)
	docker push $(IMAGE_NAME):latest

auth:
	gcloud auth configure-docker us-east1-docker.pkg.dev --quiet
