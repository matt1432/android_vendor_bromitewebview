# android_vendor_bromitewebview

arm64 / armv8

use it to build rom with bromite's webview

in manifests -->
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
	  <project name="matt1432/android_vendor_bromitewebview" path="vendor/bromite" remote="github" revision="master" />
</manifest>
```

for lineage, add "BromiteWebview BromiteWebviewOverlay" in custom apps

- https://github.com/arovlad/bromite-webview-overlay
- https://github.com/bromite/bromite/releases/download/107.0.5304.114/arm64_SystemWebView.apk
- https://github.com/bromite/bromite
