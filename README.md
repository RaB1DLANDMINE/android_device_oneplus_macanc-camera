# android_device_oneplus_macanc-camera

Prebuilt stock oplus Camera to include in custom ROM builds.

### How to use?

1. Clone this repo to `device/oneplus/macanc-camera`

2. Inherit it from `device.mk` in device tree:

```
# Camera
$(call inherit-product-if-exists, device/oneplus/macanc-camera/opluscamera.mk)
```

3. Ensure that the PRODUCT_BRAND is either oneplus or oppo or realme and that it is not overriden by any of the safetynet hacks.

### How to extract proprietary files?

From the ROM source root, place or clone this repo at `device/oneplus/macanc-camera`,
then run:

```
cd device/oneplus/macanc-camera
./extract-files.py /path/to/OP15/dump
```

The extractor reads `proprietary-files.txt`, pulls the listed files from the
dump, applies the blob fixups in `extract-files.py`, and writes the results to:

```
vendor/oneplus/macanc-camera/proprietary
```

It also regenerates the generated build files under:

```
vendor/oneplus/macanc-camera
```

After changing `proprietary-files.txt`, rerun `./extract-files.py` against the
OP15 dump before building.
