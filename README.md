parole-opus-for-openwrt
=======================

Run parole on OpenWRT. parole is a simple voip program that lets you make a voice call from the terminal using the Opus codec.

For more information see http://holdenc.altervista.org/parole/


To build, you need the OpenWRT SDK. Put the files from this repository in their respecive places. Then:

```
make oldconfig
# Select opus and parole
make package/opus/compile V=99
# To just run the packaging again (in case you want to try something)
make package/opus/compile V=99 CONFIG_AUTOREBUILD=
```
