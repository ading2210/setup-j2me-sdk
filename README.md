# J2ME SDK Tutorial for Linux and Intellij

This is a tutorial for setting up the J2ME SDK on modern Linux distros, using a recent version of IntelliJ. You may find this guide useful if you are particpating in the [Hack Club Retrospect J2ME event](https://retrospect.hackclub.com/j2me). 

![image](https://github.com/user-attachments/assets/d8616f27-f887-444f-8319-5c4899f1761e)


## 1. Set up Directories
Create a directory to put the SDK and related files. I'll use `~/j2me`.
```
~$ mkdir ~/j2me
~$ cd j2me
```

## 2. Download the Sun Java Wireless Toolkit
Download and extract the [Sun Java Wireless Toolkit](https://www.oracle.com/java/technologies/java-archive-downloads-javame-downloads.html) by running these commands. Don't worry, you don't need an Oracle account here.
```
~/j2me$ wget -c --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh"
--2025-02-10 14:08:23--  https://download.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh
Resolving download.oracle.com (download.oracle.com)... 23.196.36.113
Connecting to download.oracle.com (download.oracle.com)|23.196.36.113|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh [following]
--2025-02-10 14:08:24--  https://edelivery.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2600:1406:5400:486::366, 2600:1406:5400:4af::366, 184.28.231.219
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2600:1406:5400:486::366|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://download.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh?AuthParam=1739225424_622a9caf2f8c1940e97052f7207447da [following]
--2025-02-10 14:08:24--  https://download.oracle.com/otn-pub/java/sun_java_wireless_toolkit/2.5.2_01/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh?AuthParam=1739225424_622a9caf2f8c1940e97052f7207447da
Connecting to download.oracle.com (download.oracle.com)|23.196.36.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39797585 (38M) [application/x-sh]
Saving to: ‘sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh’

sun_java_wireless_toolkit-2.5.2 100%[====================================================>]  37.95M  23.6MB/s    in 1.6s    

2025-02-10 14:08:26 (23.6 MB/s) - ‘sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh’ saved [39797585/39797585]

~/j2me$ mkdir sdk
~/j2me$ unzip -q sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh -d sdk/
warning [sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh]:  26624 extra bytes at beginning or within zipfile
  (attempting to process anyway)
~/j2me$ rm sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh 
```

## 3. Download a 32 Bit JDK
Download and extract the 32 bit Java 8 JDK by running these commands. We're going to use Huawei's mirror to skip logging into an Oracle account. 
```
~/j2me$ wget "https://repo.huaweicloud.com/java/jdk/8u202-b08/jdk-8u202-linux-i586.tar.gz"
--2025-02-10 14:10:27--  https://repo.huaweicloud.com/java/jdk/8u202-b08/jdk-8u202-linux-i586.tar.gz
Resolving repo.huaweicloud.com (repo.huaweicloud.com)... 199.91.74.185, 149.104.73.27, 199.91.74.184, ...
Connecting to repo.huaweicloud.com (repo.huaweicloud.com)|199.91.74.185|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 197025433 (188M) [application/octet-stream]
Saving to: ‘jdk-8u202-linux-i586.tar.gz’

jdk-8u202-linux-i586.tar.gz     100%[====================================================>] 187.90M  12.6MB/s    in 13s     

2025-02-10 14:10:42 (14.0 MB/s) - ‘jdk-8u202-linux-i586.tar.gz’ saved [197025433/197025433]

~/j2me$ tar -xf jdk-8u202-linux-i586.tar.gz 
~/j2me$ ls
jdk1.8.0_202  jdk-8u202-linux-i586.tar.gz  sdk
~/j2me$ rm jdk-8u202-linux-i586.tar.gz 
```

## 4. Install and run IntelliJ IDEA Community Edition 2019.3.

We're going to install this through snap, so [make sure that's installed](https://snapcraft.io/docs/installing-snapd). On Debian, do `sudo apt install snapd` first. 

```
~/j2me$ sudo snap install intellij-idea-community --channel=2019.3/stable --classic
intellij-idea-community (2019.3/stable) 2019.3.5 from jetbrains✓ installed
~/j2me$ snap run intellij-idea-community
```

## 5. Install Intellij Plugins

On the welcome screen, configure your plugins.

![image](https://github.com/user-attachments/assets/075c0b10-1024-4218-9e8d-c5e3a2d5649d)

You can install the J2ME plugin here.

![image](https://github.com/user-attachments/assets/a5aa6277-027a-452f-a77d-62c8d754cf0d)

## 6. Setup Intellij Project

Create a J2ME project and specify the path to the SDK you already downloaded.

![image](https://github.com/user-attachments/assets/6ce64ab8-97c6-498b-8bf9-9a074e2612e8)

Under the `File > Project Structure > SDKs` menu, add the JDK you downloaded earlier.

![image](https://github.com/user-attachments/assets/69b3b31a-e7dd-45da-863c-8e274e027d9b)

In the settings for the Sun Wireless Toolkit, make sure it's set to use `1.8` as the JavaSDK.

![image](https://github.com/user-attachments/assets/ccc08afe-c75c-4b51-a21b-d5ef0905a136)

Under `File > Settings > Build, Execution, Deployment > Compiler > Java Compiler` make sure the project bytecode version is `1.4`. 

![image](https://github.com/user-attachments/assets/93be440e-c389-4eb6-a3c3-d2326beb23bf)

Add in your `MainMIDlet` class.

![image](https://github.com/user-attachments/assets/d4fd8939-89e1-4a68-a065-0625636cee98)

In `File > Project Structure > Artifacts`, create a new JAR artifact with the proper module.

![image](https://github.com/user-attachments/assets/6cc8b808-f3be-4f03-8be9-8746567a22a0)

Make sure the output directory for your JAR is the same as the project's root directory.

![image](https://github.com/user-attachments/assets/4a100704-8db3-40ea-9380-1e2de9c988b5)

In the top right corner click on "Add Configuration"

![image](https://github.com/user-attachments/assets/3dac5168-a802-4f2e-a1e8-894e6c0ebc29)

In that menu, create a new J2ME run configuration.

![image](https://github.com/user-attachments/assets/762d131d-fb98-4603-b7cd-08e852f51b23)

Change the run mode to class, then set the proper MIDlet class.

![image](https://github.com/user-attachments/assets/16a640f5-1428-4bbf-ac26-4cf6817d7068)

In the before launch options, make it build the project and then the JAR artifact.

![image](https://github.com/user-attachments/assets/1e6359fd-3778-4ce8-aabc-9ce4b500ea23)

## 7. Fix SDK Emulator Script

The original emulator script tries to run the wrong Java version. 

The original script is located at `sdk/bin/emulator` and looks like this:
```
~/j2me$ cat sdk/bin/emulator 
#!/bin/sh

javapathtowtk=

PRG=$0

# Resolve soft links
while [ -h "$PRG" ]; do
    ls=`/bin/ls -ld "$PRG"`
    link=`/usr/bin/expr "$ls" : '.*-> \(.*\)$'`
    if /usr/bin/expr "$link" : '^/' > /dev/null 2>&1; then
        PRG="$link"
    else
        PRG="`/usr/bin/dirname $PRG`/$link"
    fi
done

KVEM_BIN=`dirname "$PRG"`
KVEM_HOME=`cd "${KVEM_BIN}/.." ; pwd`
KVEM_LIB="${KVEM_HOME}/wtklib"
export MMAPI_GM_SOUNDBANK="${KVEM_HOME}/lib/soundbank.dls"

"${javapathtowtk}java" -Dkvem.home="${KVEM_HOME}" \
    -Djava.library.path="${KVEM_HOME}/bin" \
    -cp "${KVEM_LIB}/kenv.zip:${KVEM_LIB}/ktools.zip:${KVEM_LIB}/customjmf.jar" \
    com.sun.kvem.environment.EmulatorWrapper "$@" 0
```

Edit the `javapathtowtk=` line to instead be:
```
javapathtowtk="$(realpath "$(dirname "$0")"/../../jdk1.8*)/bin/"
```
And save the file.

## 8. Install Missing 32 Bit Libraries

If you try running the emulator at this stage, it will fail because it's missing 32 bit shared libraries. Identify the ones you need using `ldd`.
```
~/j2me$ ldd sdk/bin/libzayit.so
	linux-gate.so.1 (0xf7efd000)
	libXt.so.6 => not found
	libX11.so.6 => /lib/i386-linux-gnu/libX11.so.6 (0xf76fd000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf75f8000)
	libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf75dd000)
	libICE.so.6 => /lib/i386-linux-gnu/libICE.so.6 (0xf75c0000)
	libSM.so.6 => /lib/i386-linux-gnu/libSM.so.6 (0xf75b5000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf75b0000)
	libstdc++.so.6 => /lib/i386-linux-gnu/libstdc++.so.6 (0xf7390000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf7369000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf713f000)
	libxcb.so.1 => /lib/i386-linux-gnu/libxcb.so.1 (0xf7111000)
	/lib/ld-linux.so.2 (0xf7eff000)
	libbsd.so.0 => /lib/i386-linux-gnu/libbsd.so.0 (0xf70fa000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xf70f0000)
	libXau.so.6 => /lib/i386-linux-gnu/libXau.so.6 (0xf70eb000)
	libXdmcp.so.6 => /lib/i386-linux-gnu/libXdmcp.so.6 (0xf70e4000)
	libmd.so.0 => /lib/i386-linux-gnu/libmd.so.0 (0xf70d5000)
```

If you're on Ubuntu or Debian, make sure your system is configured to install i386 packages by adding the corresponding package sources:
```
~/j2me$ sudo dpkg --add-architecture i386
~/j2me$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu oracular InRelease
Hit:2 http://archive.ubuntu.com/ubuntu oracular-security InRelease
Get:3 http://archive.ubuntu.com/ubuntu oracular/main i386 Packages [1064 kB]
Get:4 http://archive.ubuntu.com/ubuntu oracular/universe i386 Packages [8526 kB]
Get:5 http://archive.ubuntu.com/ubuntu oracular-security/main i386 Packages [103 kB]
Get:6 http://archive.ubuntu.com/ubuntu oracular-security/universe i386 Packages [49.7 kB]
Fetched 9743 kB in 1s (6932 kB/s)
11 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

If you're on Debian or Ubuntu, you can find which packages include the missing libraries using `apt-file`.
```
~/j2me$ apt-file search libXt.so.6
libxt6: /usr/lib/x86_64-linux-gnu/libXt.so.6
libxt6: /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
```

Then you can just install those packages. Make sure to specify that they are 32 bit.
```
~/j2me$ sudo apt install libxt6:i386
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  libxt6:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 192 kB of archives.
After this operation, 485 kB of additional disk space will be used.
Get:1 http://deb.debian.org/debian bookworm/main i386 libxt6 i386 1:1.2.1-1.1 [192 kB]
Fetched 192 kB in 0s (1,498 kB/s)
Selecting previously unselected package libxt6:i386.
(Reading database ... 626617 files and directories currently installed.)
Preparing to unpack .../libxt6_1%3a1.2.1-1.1_i386.deb ...
Unpacking libxt6:i386 (1:1.2.1-1.1) ...
Setting up libxt6:i386 (1:1.2.1-1.1) ...
Processing triggers for libc-bin (2.36-9+deb12u9) ...
```

## 9. Running the Project

Now, you can just hit the run button in IntelliJ to build your project and run it in the emulator. 

![image](https://github.com/user-attachments/assets/b3c5a1b4-8960-4340-a302-982c34600e5f)

You can even debug it.

![image](https://github.com/user-attachments/assets/6443aa50-e8ff-4c7c-813b-4fd7bf7a7b23)
