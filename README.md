[Bug 69661 - mwifiex_usb on MS Surface Pro 1 is unstable](https://bugzilla.kernel.org/show_bug.cgi?id=69661) patch applied kernel how to

1. Download latest debian kernel and install required dependencies
$ sudo apt-get update
$ sudo apt-get install fakeroot build-essential devscripts
$ sudo apt-get build-dep linux
$ sudo apt-get source linux

2. Uncompress kernel and copy files from patches/ folder into the kernel root folder
$ tar zxvf linux_4.*.gz
$ cd linux-*
$ wget (put patches URL here)

3. Run patcher
$ patch -p1 < surfacepro-1.patch
$ patch -p1 < surfacepro-2.patch
$ patch -p1 < surfacepro-3.patch
$ patch -p1 < surfacepro-5.patch

4. Compile kernel
$ make deb-pkg LOCALVERSION=-c1 KDEB_PKGVERSION=1

5. Install them.
$ sudo dpkg -i linux-headers-4.1*.deb linux-image-4.1*.deb
$ sudo reboot


To uninstall,
$ sudo apt-get remove 'linux-headers-4.1*' 'linux-image-4.1*'
