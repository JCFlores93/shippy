update_proto:
#	protoc -I. --go_out=plugins=grpc:. proto/consignment/consignment.proto
#	protoc -I. --go_out=plugins=grpc:. ./consignment.proto
#  	For go-micro
    protoc -I. --go_out=plugins=micro:. \
        		./consignment.proto
create_image:
	docker build -t shippy-service-consignment .

run_container:
	 docker run -p 50051:50051 shippy-service-consignment
	 docker run -p 50051:50051 \
     	-e MICRO_SERVER_ADDRESS=:50051 \
        shippy-service-consignment