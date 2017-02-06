Some Notes tips and tricks for my Android-phone
---------------------------

#### Need ssh, install dropbear

Dropbear is a Posix compatible minimalist SSH suite

Get the sources

> wget https://matt.ucc.asn.au/dropbear/dropbear-2016.73.tar.bz2

Extract files

> tar -xf dropbear-2016.73.tar.bz2

get the patch

> wget https://raw.githubusercontent.com/gerito1/notes/master/android/dropbear-android.patch

> cd dropbear-2016.73

Apply the patch

> patch -s -p1 < ../dropbear-android.patch

Download configuration files

> wget -O config.sub "http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD"
> wget -O config.guess "http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD"

Set enviroment variables

> ANDROID_NDK=/opt/android-ndk
> ANDROID_ABI="armeabi-v7a"
> ANDROID_NATIVE_API_LEVEL="android-15"
> export ANDROID_NDK
> export PATH=$ANDROID_NDK/toolchains/arm-linux-androideabi-4.9/prebuilt/linux-x86_64/bin/:$PATH
> export ARCH=$ANDROID_ABI
> SYSROOT=$ANDROID_NDK/platforms/$ANDROID_NATIVE_API_LEVEL/arch-arm
> export CFLAGS=--sysroot=$SYSROOT
> export LDFLAGS=--sysroot=$SYSROOT

Configure the build

> ./configure --host=arm-linux-androideabi --disable-utmp --disable-wtmp --disable-utmpx --disable-utmpx --disable-zlib --disable-syslog
> echo "#define USE_DEV_PTMX 1" >> config.h

Do the thing

> make PROGRAMS="dropbear dropbearkey scp" strip

and done!
