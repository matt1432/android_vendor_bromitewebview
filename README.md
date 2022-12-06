# Bromite System Webview

This is a repositery hosting the make files and apk to successfully implement Bromite's System Webview in an ARM64/ARMv8 android device ROM. It uses an overlay, adds the app to the system and removes AOSP's webview to do so. 

I recommend using [lineageos4microg/docker-lineage-cicd](https://github.com/lineageos4microg/docker-lineage-cicd) to build it.

## Implementation
To do this, add a repo manifest file to include this repository like so :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
	  <project name="matt1432/android_vendor_bromitewebview" path="vendor/bromite" remote="github" revision="master" />
</manifest>
```
### With [lineageos4microg/docker-lineage-cicd](https://github.com/lineageos4microg/docker-lineage-cicd)
You need to make a `before.sh` script in the `/srv/userscripts` [folder](https://github.com/lineageos4microg/docker-lineage-cicd#volumes) and add these lines in it :

```yml
sed -i "1s;^;\$(call inherit-product-if-exists, vendor/bromite/bromite.mk)\n\n;" "/srv/src/LINEAGE_19_1/vendor/lineage/config/common.mk"
(cd "/srv/src/LINEAGE_19_1/vendor/bromite/" && git lfs pull)
```
No need to add anything to your `CUSTOM_PACKAGES` variable in your docker-compose.yml!

### Without [lineageos4microg/docker-lineage-cicd](https://github.com/lineageos4microg/docker-lineage-cicd)
You need to edit the "vendor/lineage/config/common.mk" file by adding :

```yml
$(call inherit-product-if-exists, vendor/bromite/bromite.mk)
```
and then `git lfs pull` inside the repository at `vendor/bromite` to have the APK

# Credits

* [Bromite](https://github.com/bromite/bromite) themselves
* [Magisk-Module/open_webview](https://github.com/Magisk-Modules-Alt-Repo/open_webview) for overlay's AndroidManifest.xml
* [arovlad/bromite-webview-overlay](https://github.com/arovlad/bromite-webview-overlay) for inspiration and examples I used
