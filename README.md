# TWRP configuration for Sony Tama (SDM845) platform devices

## Supported Sony Snapdragon 845 based devices

- Xperia XZ2 H8216/H8266/H8296    => [akari](https://www.gsmarena.com/sony_xperia_xz2-9081.php)
- Xperia XZ2 Compact H8314/H8324  => [apollo](https://www.gsmarena.com/sony_xperia_xz2_compact-9082.php)
- Xperia XZ2 Premium H8116/H8166  => [aurora](https://www.gsmarena.com/sony_xperia_xz2_premium-9166.php)
- Xperia XZ3 H8416/H9436/H9493    => [akatsuki](https://www.gsmarena.com/sony_xperia_xz3-9232.php)

## Clone manifest twrp-14.1

```bash
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-14.1
```

## Sync manifest twrp-14.1

```bash
repo sync -j$(nproc --all)
```

## Clone the device tree

```bash
git clone https://github.com/j4nn/android_device_sony_tama.git -b android-14.1 device/sony/tama
```

## Build

```bash
unset JAVAC
unset JAVA_HOME
unset LEX
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
export USE_CUSTOM_VERSION=true

lunch twrp_akari-ap2a-userdebug; mka bootimage
lunch twrp_apollo-ap2a-userdebug; mka bootimage
lunch twrp_aurora-ap2a-userdebug; mka bootimage
lunch twrp_akatsuki-ap2a-userdebug; mka bootimage
```

## Thanks

- [MartinX3](https://github.com/MartinX3) ([android9 twrp](https://github.com/MartinX3-AndroidDevelopment/TWRP_android_device_sony_akari_old) for tama devices including touch type detection)
- TWRP developers (other devices setup as a base template)
- Lineage OS developers (multiple picks from tama devices configs)

Please see commits history for proper attribution.
