export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/kbudde/rabbitmq_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := master
export GO_VERSION := 1.6

all: build

build:
	mkdir -p $(GOPATH)
	git clone https://github.com/kbudde/rabbitmq_exporter.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	go get -u github.com/golang/glog
	git -C $(SRCDIR) apply < flag.patch
	make -C $(SRCDIR)
	cp -f $(SRCDIR)/rabbitmq_exporter $(SRCDIR)/prometheus-rabbitmq-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
