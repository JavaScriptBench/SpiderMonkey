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
```
Before `make -j4`, change one line in file `./mozjs-24.2.0/js/src/shell/jsoptparse.cpp`

```
256         if (value[0] == "\0")
257             return error("A value is required for option %.*s", eq - argv[*i], argv[*i]);
```

The binary locates in:
***`~/mozjs-24.2.0/js/src/shell/js`***





========================================================


Ref: 

- https://www.linuxfromscratch.org/blfs/view/8.0/general/JS2.html
- http://ftp.mozilla.org/pub/js/
- https://hg.mozilla.org/releases/
