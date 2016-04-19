export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/alertmanager
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := master

all: build

build:
	mkdir -p $(GOPATH)
	go get -v -u github.com/prometheus/alertmanager
	git -C $(SRCDIR) checkout $(BRANCH)
	make -C $(SRCDIR) build
	cp -f $(SRCDIR)/alertmanager $(SRCDIR)/prometheus-alertmanager

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
