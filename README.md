# SpiderMonkey

spider monkey with different versions 


=====================================================



## version 24.2.0

http://ftp.mozilla.org/pub/mozilla.org/js/mozjs-24.2.0.tar.bz2

Download MD5 sum: 5db79c10e049a2dc117a6e6a3bc78a8e

Download size: 15 MB

Estimated disk space required: 1.8 GB

Estimated build time: 4.2 SBU (additional 1.6 SBU for the tests)


To Build and Test:
```
tar -xvf mozjs-24.2.0.tar.bz2
cd mozjs-24.2.0/js/src/
./configure
make -j4
./shell/js test.js
# or using --no-baseline for disabling JIT
./shell/js --no-baseline  test.js
```
Before `make -j4`, change one line in file `./mozjs-24.2.0/js/src/shell/jsoptparse.cpp`

```
256         if (value[0] == "\0")
257             return error("A value is required for option %.*s", eq - argv[*i], argv[*i]);
```

The binary locates in:
***`~/mozjs-24.2.0/js/src/shell/js`***


## version 52.9.1

To build 52.9.1, first install autoconf2.13.
Install Autoconf by running the following commands:
```
tar -xvf autoconf-2.13.tar.gz
cd autoconf-2.13
patch -Np1 -i ../autoconf-2.13-consolidated_fixes-1.patch &&
mv -v autoconf.texi autoconf213.texi                      &&
rm -v autoconf.info                                       &&
./configure --prefix=/usr --program-suffix=2.13           &&
make
```
Then install:
```
sudo make install                                      &&
sudo install -v -m644 autoconf213.info /usr/share/info &&
sudo install-info --info-dir=/usr/share/info autoconf213.info
sudo ln -s /bin/mktemp /usr/bin/mktemp
```

Then download source file for 52 from Gitlab:
```
git clone https://salsa.debian.org/gnome-team/mozjs.git
cd mozjs
git branch -a
git checkout remotes/origin/upstream/52
cd ./js/src/
mkdir build
cd build
../configure
touch ../configure
touch ./config.status
make -j4
./js/src/shell/js --version
```
The binary locates in:
***`~/mozjs/js/src/build/js/src/shell/js`***




========================================================


Ref: 

- https://www.linuxfromscratch.org/blfs/view/8.0/general/JS2.html
- http://ftp.mozilla.org/pub/js/
- https://hg.mozilla.org/releases/
