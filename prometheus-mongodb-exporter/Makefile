export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/dcu/mongodb_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := master
export GO_VERSION := 1.6

all: build

build:
	mkdir -p $(GOPATH)
	git clone https://github.com/dcu/mongodb_exporter.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	git -C $(SRCDIR) apply < oplog.patch
	go get -u github.com/golang/glog
	make -C $(SRCDIR) build
	cp -f $(SRCDIR)/mongodb_exporter $(SRCDIR)/prometheus-mongodb-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
