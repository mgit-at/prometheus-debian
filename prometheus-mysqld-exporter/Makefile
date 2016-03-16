export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/node_exporter
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := 0.7.1
export GO_VERSION := 1.6

all: build

build:
	mkdir -p $(GOPATH)
	git clone https://github.com/prometheus/mysqld_exporter.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	make -C $(SRCDIR)
	cp -f $(SRCDIR)/mysqld_exporter $(SRCDIR)/prometheus-mysqld-exporter

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
	make
	./mysqld_exporter <flags>
