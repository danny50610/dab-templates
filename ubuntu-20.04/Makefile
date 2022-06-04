BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap
	
	echo "en_US.UTF-8" > ${BASEDIR}/etc/locale
	echo "en_US.UTF-8 UTF-8" > ${BASEDIR}/etc/locale.gen
	dab exec dpkg-reconfigure -f noninteractive locales
	
	dab install tmux htop git vim

	if [ -f "../files/.vimrc" ]; then cp ../files/.vimrc ${BASEDIR}/root/.vimrc; fi
	if [ -f "../files/.tmux.conf" ]; then cp ../files/.vimrc ${BASEDIR}/root/.tmux.conf; fi

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
