BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap --minimal
	dab install devuan-keyring
	# Workaround to avoid: unable to create CT 100 - unsupported Devuan version 'chimaera/ceres'
	dab exec bash -c "echo ascii > /etc/devuan_version"
	dab finalize

info/init_ok: dab.conf
	dab init
	touch $@

.PHONY: clean
clean:
	dab clean
	rm -f *~

.PHONY: dist-clean
dist-clean:
	dab dist-clean
	rm -f *~
