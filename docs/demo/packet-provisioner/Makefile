.PHONY: image

IMAGE?=packet-provisioner

image: packet-provisioner
	docker build -t $(IMAGE) -f Dockerfile.scratch .

packet-provisioner: $(shell find . -name "*.go")
	glide install -v
	CGO_ENABLED=0 go build -a -ldflags '-extldflags "-static"' -o packet-provisioner .

.PHONY: clean
clean:
	rm packet-provisioner
