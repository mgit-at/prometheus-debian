export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/node_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := v0.13.0

all: build

build:
	mkdir -p $(GOPATH)
	go get -u github.com/prometheus/node_exporter
	git -C $(SRCDIR) checkout -b $(BRANCH)
	#git -C $(SRCDIR) apply < systemd_private.patch
	go install github.com/prometheus/node_exporter
	cp -f $(GOPATH)/bin/node_exporter $(GOPATH)/bin/prometheus-node-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
