export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/blackbox_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := master
export GO_VERSION := 1.6

all: build

build:
	git clone https://github.com/prometheus/blackbox_exporter.git $(SRCDIR)
	make -C $(SRCDIR)
	cp -f $(SRCDIR)/blackbox_exporter $(SRCDIR)/prometheus-blackbox-exporter
	
clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
