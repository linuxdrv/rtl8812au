1.Download wpa_supplicant 
	cd~
	git clone git://w1.fi/srv/git/hostap.git
2.Install Additional package 
	sudo apt-get -y install libssl-dev libnl-genl-3-dev
3.Config wpa_supplicant for supporting P2P
	cd ~/hostap/wpa_supplicant
	cp defconfig .config
	echo CONFIG_LIBNL32=y >> .config
	echo "#Arun Kumar: Enabling Modules for Wi-Fi Direct aka P2P" >> .config
	echo CONFIG_P2P=y >> .config
	echo CONFIG_AP=y >> .config
	echo CONFIG_WPS=y >> .config
	echo CONFIG_DRIVER_NL80211=y>>.config
	echo CONFIG_CTRL_IFACE=y>>.config
	echo CONFIG_WPS2=y>>.config
3.compile wpa_supplicant
	make
	sudo make install
4.

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -B

