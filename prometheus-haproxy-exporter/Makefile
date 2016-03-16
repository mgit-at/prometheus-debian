export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/haproxy_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := 0.5.0
export GO_VERSION := 1.6

all: build

build:
	mkdir -p $(GOPATH)
	git clone https://github.com/prometheus/haproxy_exporter.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	make -C $(SRCDIR)
	cp -f $(SRCDIR)/haproxy_exporter $(SRCDIR)/prometheus-haproxy-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
