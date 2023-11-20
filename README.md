### Device specific configuration to build TWRP for [Raspberry Pi 4](http://konstakang.com/devices/rpi4/TWRP) and [Raspberry Pi 5](http://konstakang.com/devices/rpi5/TWRP).

***

### How to build:

1. Establish [Android build environment](https://source.android.com/setup/initializing) and install [repo](https://source.android.com/docs/setup/develop#installing-repo).

2. Initialize repo:

```
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11 --depth=1
curl -o .repo/local_manifests/manifest_brcm_rpi.xml -L https://raw.githubusercontent.com/twrp-raspberry/android_local_manifest/twrp-11/manifest_brcm_rpi.xml --create-dirs
repo sync
```

3. Compile:

```
. build/envsetup.sh
lunch twrp_rpi-eng
make ramdisk-recovery -j$(nproc)
```

4. Copy ramdisk-recovery.img to Android boot partition.
