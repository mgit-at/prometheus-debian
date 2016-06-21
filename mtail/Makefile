export GOROOT := /opt/go
export GOPATH := $(shell pwd)/gopath
export SRCDIR := $(GOPATH)/src/github.com/google/mtail
export PATH   := $(GOROOT)/bin:$(PATH)
export BRANCH := master
export GO_VERSION := 1.6

all: build

build:
	mkdir -p $(GOPATH)
	git clone https://github.com/google/mtail.git $(SRCDIR)
	git -C $(SRCDIR) checkout $(BRANCH)
	git -C $(SRCDIR) apply < address.patch
	make -C $(SRCDIR)

clean:
	rm -rf $(SRCDIR)

deb:
	eatmydata debuild -I -us -uc

.PHONY: all clean deb
