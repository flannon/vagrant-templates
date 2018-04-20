VARDIR = var
ENVIRONMENTSDIR = puppetlabs/code/environments

.PHONY: r10k
r10k:
	cd puppetlabs; \
	r10k deploy environment development -p -v -c r10k/r10k.yaml

.PHONY: clean
clean:
	rm -rf ${ENVIRONMENTSDIR}/*

