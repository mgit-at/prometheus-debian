export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/alertmanager
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := 0.1.0

all: build

build:
	mkdir -p $(GOPATH)
	go get -u github.com/prometheus/alertmanager
	git -C $(SRCDIR) checkout -b $(BRANCH)
	go install github.com/prometheus/alertmanager
	cp -f $(GOPATH)/bin/alertmanager $(GOPATH)/bin/prometheus-alertmanager

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
