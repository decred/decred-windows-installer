include current_digests

export DCRDDIGEST
export DCRWALLETDIGEST
export PAYMETHEUSDIGEST

ifndef WIX
export WIX="/c/Program\ Files\ (x86)/WiX\ Toolset\ v3.10/"
endif

SUBDIRS = checkerouter paymetheus decred
TARGETS = cleanobjs clean current

all: $(SUBDIRS)

$(TARGETS):
	@for i in $(SUBDIRS); do echo "===> $$i ($@)"; "$(MAKE)" -C $$i/ $@; done

$(SUBDIRS):
	@echo "===> $@"
	"$(MAKE)" -C $@

.PHONY: all $(SUBDIRS) $(TARGETS)
