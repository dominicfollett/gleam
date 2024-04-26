all: gen

.PHONY : gen

gen:
	protoc gleam.proto --go-grpc_out=./ --go_out=./
