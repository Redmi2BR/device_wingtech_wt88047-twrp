## TWRP 64bits for Redmi 2 (wt88047) Treble oem-cache version.

note: I used https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni
branch: twrp-7.1

Preparation:

Add to `.repo/local_manifests/wt88047.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
	<remove-project path="bootable/recovery" name="android_bootable_recovery" />
	<project path="bootable/recovery" name="android_bootable_recovery" remote="omnirom" revision="android-8.1" groups="pdk-cw-fs"/>
	<project name="Redmi2BR/device_wingtech_wt88047_64-twrp" path="device/wingtech/wt88047"  remote="github" revision="android-7.1-treble64" />
</manifest>
```

Then run `repo sync  -f --force-sync --no-clone-bundle --no-tags -j$(nproc --all)` to check it out.

To build:

```sh
. build/envsetup.sh
lunch omni_wt88047-userdebug
mka recoveryimage
```

Kernel sources are available at: https://github.com/redmi2/kernel
