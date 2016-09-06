export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/prometheus/alertmanager
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := v0.4.2

all: build

build:
	mkdir -p $(SRCDIR)
	git clone https://github.com/prometheus/alertmanager.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	make -C $(SRCDIR) build
	cp -f $(SRCDIR)/alertmanager $(SRCDIR)/prometheus-alertmanager

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
