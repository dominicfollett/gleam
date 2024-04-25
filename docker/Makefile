BINARY = gleam
SOURCE_DIR = github.com/chrislusf/gleam/distributed/gleam

all: gleam

.PHONY : clean deps docker dev run_docker

clean:
	go clean $(SOURCE_DIR)
	rm -f $(BINARY)

deps:
	go get $(GO_FLAGS) -d $(SOURCE_DIR)

gleam: deps
	GOOS=linux GOARCH=amd64 go build -o $(BINARY) $(SOURCE_DIR)

dev: gleam
	docker build -t gleam:local .
	rm -f $(BINARY)

docker: gleam
	docker build -t chrislusf/gleam .
	rm -f $(BINARY)
	docker push chrislusf/gleam:latest

run_docker: docker
	docker-compose up
