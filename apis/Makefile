image = apis
container = apis
deployment = apis
tag := $(shell TZ=Etc/Utc date "+%Y%m%dt%H%M%S")

default:
	@echo "build the apis!"

build:
	docker build . -t $(image)

tag:
	docker tag $(image) $(image):$(tag)

deploy: tag
	kubectl set image deployment/$(deployment) $(container)=$(image):$(tag)
