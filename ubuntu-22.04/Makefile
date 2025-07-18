BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap

	mkdir -p ${BASEDIR}/etc/systemd/system-preset
	cp systemd-presets ${BASEDIR}/etc/systemd/system-preset/00-pve-template.preset
	
	echo "en_US.UTF-8 UTF-8" > ${BASEDIR}/etc/locale.gen
	dab exec locale-gen
	dab exec update-locale LANG="en_US.UTF-8"
	dab exec dpkg-reconfigure -f noninteractive locales
	
	dab install tmux htop git vim curl

	if [ -f "../files/.vimrc" ]; then cp ../files/.vimrc ${BASEDIR}/root/.vimrc; fi
	if [ -f "../files/.tmux.conf" ]; then cp ../files/.tmux.conf ${BASEDIR}/root/.tmux.conf; fi
	if [ -f "../files/.config/htop/htoprc" ]; then mkdir -p ${BASEDIR}/root/.config/htop && cp ../files/.config/htop/htoprc ${BASEDIR}/root/.config/htop/htoprc; fi

	sed -i 's/xterm-color) color/xterm-color|*-256color) color/' ${BASEDIR}/root/.bashrc

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
