#  Ferrarri Device,Vendor,Kernel,Oplus Trees

>  Build By : [Omkar Parte](https://t.me/rakmoparte) ( RAKMOSOLUTIONS )

## Clone repos (Bringup)

```
git clone https://github.com/Realme-GT-2-PRO/device_realme_ferrarri.git device/realme/ferrarri
```
```
git clone https://github.com/Realme-GT-2-PRO/device_oneplus_sm8450-common.git device/oneplus/sm8450-common
```
```
git clone https://gitlab.com/ram-unlok/proprietary_vendor_realme_ferrarri.git vendor/realme/ferrarri
```
```
git clone https://gitlab.com/ram-unlok/proprietary_vendor_oneplus_sm8450-common.git vendor/oneplus/sm8450-common
```
```
git clone https://github.com/Realme-GT-2-PRO/android_hardware_oplus.git -b A14 hardware/oplus
```
```
git clone https://github.com/pjgowtham/android_kernel_oneplus_sm8450.git kernel/oneplus/sm8450
```
### OR 
```
git clone https://github.com/Machad3x/android_kernel_oneplus_sm8450.git kernel/oneplus/sm8450
```
```
git clone https://github.com/pjgowtham/android_kernel_oneplus_sm8450-modules.git kernel/oneplus/sm8450-modules
```
### OR 
```
git clone https://github.com/Machad3x/android_kernel_oneplus_sm8450-modules.git kernel/oneplus/sm8450-modules
```
```
git clone https://github.com/pjgowtham/android_kernel_oneplus_sm8450-devicetrees.git kernel/oneplus/sm8450-devicetrees
```
### OR 
```
git clone https://github.com/Machad3x/android_kernel_oneplus_sm8450-devicetrees.git kernel/oneplus/sm8450-devicetrees
```
```
git clone https://gitlab.com/ram-unlok/proprietary_vendor_oplus_camera.git vendor/oplus/camera
```


## Clone repos (Bringup) Depth=1

```
git clone --depth=1 https://github.com/Realme-GT-2-PRO/device_realme_ferrarri.git device/realme/ferrarri
```
```
git clone --depth=1 https://github.com/Realme-GT-2-PRO/device_oneplus_sm8450-common.git device/oneplus/sm8450-common
```
```
git clone --depth=1 https://gitlab.com/ram-unlok/proprietary_vendor_realme_ferrarri.git vendor/realme/ferrarri
```
```
git clone --depth=1 https://gitlab.com/ram-unlok/proprietary_vendor_oneplus_sm8450-common.git vendor/oneplus/sm8450-common
```
```
git clone --depth=1 https://github.com/Realme-GT-2-PRO/android_hardware_oplus.git -b A14 hardware/oplus
```
```
git clone --depth=1 https://github.com/pjgowtham/android_kernel_oneplus_sm8450.git kernel/oneplus/sm8450
```
### OR 
```
git clone --depth=1 https://github.com/Machad3x/android_kernel_oneplus_sm8450.git kernel/oneplus/sm8450
```
```
git clone --depth=1 https://github.com/pjgowtham/android_kernel_oneplus_sm8450-modules.git kernel/oneplus/sm8450-modules
```
### OR 
```
git clone --depth=1 https://github.com/Machad3x/android_kernel_oneplus_sm8450-modules.git kernel/oneplus/sm8450-modules
```
```
git clone --depth=1 https://github.com/pjgowtham/android_kernel_oneplus_sm8450-devicetrees.git kernel/oneplus/sm8450-devicetrees
```
### OR 
```
git clone --depth=1 https://github.com/Machad3x/android_kernel_oneplus_sm8450-devicetrees.git kernel/oneplus/sm8450-devicetrees
```
```
git clone --depth=1 https://gitlab.com/ram-unlok/proprietary_vendor_oplus_camera.git vendor/oplus/camera
```


- To Update trees which were cloned with depth=1 use below

```
git pull -f --depth=1 --rebase
```
```
git lfs fetch --all
```

## Some Tweaks For Building the ROM

- Build BCR (add this to your blaze_device.mk)
- Thanks to [chenxiaolong](https://github.com/chenxiaolong)

```
git clone https://gitlab.com/ram-unlok/bcr.git vendor/bcr
```
```
$(call inherit-product, vendor/bcr/bcr.mk)
```

- Build VIPERFX RE
- Thanks to [TogoFire](https://github.com/TogoFire)

```
git clone --depth 1 https://github.com/TogoFire/packages_apps_ViPER4AndroidFX.git packages/apps/ViPER4AndroidFX
```
```
$(call inherit-product, packages/apps/ViPER4AndroidFX/config.mk)
```

- Change Build Time and Date to Indian time
- Replace `date -u` in `vendor/blaze/config/version.mk` with

```
TZ=IST-5:30 date
```

- Basic Commands for start building

> Build using less space and network bandwidth

```
repo init --depth=1 -u https://github.com/RAM-UNLOK/blaze-manifest.git -b 14
```
```
repo sync -c -j$(nproc --all) --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune && repo forall -c git lfs pull
```
```
. build/envsetup.sh
```
```
lunch blaze_$device-userdebug
```
```
make bacon
```

## Update Vendor Blobs From Dump

- Lets Extract Dump from OTA

> [Detailed Guide is here](https://baalajimaestro.me/posts/extract-vendor-2/)

```
git clone https://github.com/RAM-UNLOK/dumpyara.git
```
```
cd dumpyara
```
```
bash setup.sh
```
```
bash dumpyara.sh /otazippathname.zip
```
```
git clone https://github.com/LineageOS/android_tools_extract-utils -b lineage-21.0 android/tools/extract-utils
```
```
git clone https://github.com/LineageOS/android_prebuilts_extract-tools -b lineage-21.0 android/prebuilts/extract-tools
```


- Lets extract Images from OTA zip files

1. Extract the OTA zip or 7z file

2. Download and extract [payload-dumper-go](https://github.com/ssut/payload-dumper-go/releases)

3. Drag and drop payload.bin on payload-dumper-go executable


- move to you device tree where extract-files.sh is located

```
bash extract-files.sh /otadumppath/
```

- ( usually home/username/dumpyara/working/otazippathname/ )

```
python3 reorder-libs.py
```

- (rearanges files in proprietary-files)

```
sort proprietary-files.txt | uniq -cd | sort -nr
```

- (Finds Duplicate in proprietary-files.txt)


## Grep Commands

```
grep -r filename
```
- (Do to the dir where you want to search for and then use the above command)


## Fix Sepolicy

Download Fix from [Dexer125/SELinux-Denials-Tool](https://github.com/Dexer125/SELinux-Denials-Tool/releases) or [DarkJoker360/selinux-denial-fixer](https://github.com/DarkJoker360/selinux-denial-fixer.git)

```
java -jar SELinuxDenialsTool.jar
```
```
python3 denials.py
```

## Find and replace one word from multiple dir

```
grep -rli 'EXPORT_SYMBOL' | xargs sed -i 's/EXPORT_SYMBOL(/EXPORT_SYMBOL_GPL(/g'
```
