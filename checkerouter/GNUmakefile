DCRD=github.com/decred/dcrd
DCRWALLET=github.com/decred/dcrwallet

PAYMETHEUSPATH=~/git/Paymetheus

ifndef PAYMETHEUSDIGEST
$(error PAYMETHEUSDIGEST not set)
endif

ifndef DCRDDIGEST
$(error DCRDDIGEST not set)
endif

ifndef DCRWALLETDIGEST
$(error DCRWALLETDIGEST not set)
endif

all: paymetheus dcrd dcrwallet

clean:

current: $(PAYMETHEUSPATH) $(GOPATH)/src/$(DCRD) $(GOPATH)/src/$(DCRWALLET)
	# paymetheus
	cd $(PAYMETHEUSPATH)/ && git clean -xdf
	cd $(PAYMETHEUSPATH)/ && git checkout master
	cd $(PAYMETHEUSPATH)/ && git pull --ff
	# dcrd
	cd $(GOPATH)/src/$(DCRD) && git checkout master
	cd $(GOPATH)/src/$(DCRD) && git pull --ff
	cd $(GOPATH)/src/$(DCRD) && glide install
	# wallet
	cd $(GOPATH)/src/$(DCRWALLET) && git checkout master
	cd $(GOPATH)/src/$(DCRWALLET) && git pull --ff
	cd $(GOPATH)/src/$(DCRWALLET) && glide install

paymetheus: $(PAYMETHEUSPATH)
	cd $(PAYMETHEUSPATH)/ && git clean -xdf
	cd $(PAYMETHEUSPATH)/ && git checkout master
	cd $(PAYMETHEUSPATH)/ && git pull --ff
	cd $(PAYMETHEUSPATH)/ && git checkout $(PAYMETHEUSDIGEST)

$(PAYMETHEUSPATH):
	cd `dirname $(PAYMETHEUSPATH)` && git clone https://github.com/decred/`basename $(PAYMETHEUSPATH)`.git

dcrd: $(GOPATH)/src/$(DCRD)
	cd $(GOPATH)/src/$(DCRD) && git checkout master
	cd $(GOPATH)/src/$(DCRD) && git pull --ff
	cd $(GOPATH)/src/$(DCRD) && git checkout $(DCRDDIGEST)
	cd $(GOPATH)/src/$(DCRD) && glide install

$(GOPATH)/src/$(DCRD):
	cd `dirname $(GOPATH)/src/$(DCRD)` && git clone https://github.com/decred/`basename $(DCRD)`.git

dcrwallet: $(GOPATH)/src/$(DCRWALLET)
	cd $(GOPATH)/src/$(DCRWALLET) && git checkout master
	cd $(GOPATH)/src/$(DCRWALLET) && git pull --ff
	cd $(GOPATH)/src/$(DCRWALLET) && git checkout $(DCRWALLETDIGEST)
	cd $(GOPATH)/src/$(DCRWALLET) && glide install

$(GOPATH)/src/$(DCRWALLET):
	cd `dirname $(GOPATH)/src/$(DCRWALLET)` && git clone https://github.com/decred/`basename $(DCRWALLET)`.git

.PHONY: all clean dcrd dcrwallet paymetheus
