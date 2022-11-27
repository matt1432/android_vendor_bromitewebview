# Bromite System Webview

This is a repositery hosting the make files and apk to successfully implement Bromite's System Webview in an arm64/armv8 android device ROM by using an overlay and adding the app to the system. I recommend using [lineageos4microg/docker-lineage-cicd](https://github.com/lineageos4microg/docker-lineage-cicd) to build it.


To do this, add a repo manifest file to include this repository like so :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
	  <project name="matt1432/android_vendor_bromitewebview" path="vendor/bromite" remote="github" revision="master" />
</manifest>
```


If you are using [lineageos4microg/docker-lineage-cicd](https://github.com/lineageos4microg/docker-lineage-cicd), you need to add `BromiteWebview BromiteWebviewOverlay` in the `CUSTOM_PACKAGES` environment variable in your docker-compose.yml file.

Otherwise, you need to edit the "vendor/lineage/config/common.mk" file by adding :

```yml
$(call inherit-product-if-exists, vendor/bromite/app/BromiteWebview/Android.mk)
$(call inherit-product-if-exists, vendor/bromite/product/overlay/BromiteWebviewOverlay/Android.mk)
```
# Credits

* [Bromite](https://github.com/bromite/bromite) themselves
* [arovlad/bromite-webview-overlay](https://github.com/arovlad/bromite-webview-overlay) for inspiration and examples I used
