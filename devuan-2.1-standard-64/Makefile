BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap
	dab install devuan-keyring
	dab exec bash -c "echo 9.0 > /etc/debian_version"
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
