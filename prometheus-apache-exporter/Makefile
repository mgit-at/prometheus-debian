export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/neezgee/apache_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := 0.1

all: build

build:
	mkdir -p $(GOPATH)
	go get -v -u github.com/neezgee/apache_exporter
	git -C $(SRCDIR) checkout $(BRANCH)
	go install github.com/neezgee/apache_exporter
	cp -f $(GOPATH)/bin/apache_exporter $(GOPATH)/bin/prometheus-apache-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
