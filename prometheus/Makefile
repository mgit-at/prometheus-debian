GOROOT := /opt/go
GOPATH := $(shell pwd)/gopath
SRCDIR := $(GOPATH)/src/github.com/prometheus/prometheus
PATH   := $(GOROOT)/bin:$(PATH)
BRANCH := v1.4.1

all: build

clone:
	mkdir -p $(SRCDIR)
	git clone -b $(BRANCH) https://github.com/prometheus/prometheus.git $(SRCDIR)

build: clone
	GOROOT=$(GOROOT) GOPATH=$(GOPATH) PATH=$(PATH) make -C $(SRCDIR) build

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
