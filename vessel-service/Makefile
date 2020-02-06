build_proto_file:
	protoc -I. --go_out=plugins=micro:. \
      proto/vessel/vessel.proto

build_image:
	docker build -t shippy-service-vessel .

run_container:
	docker run -p 50052:50051 -e MICRO_SERVER_ADDRESS=:50051 shippy-service-vessel