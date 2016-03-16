export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/collectd_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := 0.2.0

all: build

build:
	mkdir -p $(GOPATH)
	go get -v -u github.com/prometheus/collectd_exporter
	git -C $(SRCDIR) checkout -b $(BRANCH)
	go install github.com/prometheus/collectd_exporter
	cp -f $(GOPATH)/bin/collectd_exporter $(GOPATH)/bin/prometheus-collectd-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
