BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap
	dab install devuan-keyring
	dab exec bash -c "echo 10.0 > /etc/debian_version"
	dab exec apt-get -y purge x11-apps x11-common x11-session-utils x11-utils x11-xkb-utils x11-xserver-utils libgl1-mesa-dri libglapi-mesa libglx-mesa0 libllvm7
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
