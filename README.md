# flutter_seuic_scanner_plugin_sdk

A Flutter plugin based on the seuic(东集) UTouch mobile phone scanning SDK

## Getting Started

Before use, it is necessary to add it in AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
```

in pubspec.yml dependencies add

```yaml

flutter_seuic_scanner_plugin_sdk:
  git:
    url: https://github.com/Soullose/flutter_seuic_scanner_plugin_sdk.git

```

## Get Scanned QR Code

```dart

final _flutterSeuicScannerPluginSdkPlugin = FlutterSeuicScannerPluginSdk();


void initScanner() {
    String barcode;
    _flutterSeuicScannerPluginSdkPlugin
        .getScanner()
        .listen((BarcodeScanner event) {
      barcode = event.barcode ?? '无';
      setState(() {
        _barCode = barcode;
      });
    });
  }

  Future<void> startScannerService() async {
    String result;
    try {
      result = await _flutterSeuicScannerPluginSdkPlugin.startScannerService();
    } on PlatformException {
      result = 'Failed to start scanner service.';
    }
    setState(() {
      _result = result;
    });
  }

  Future<void> stopScannerService() async {
    String result;
    try {
      result = await _flutterSeuicScannerPluginSdkPlugin.stopScannerService();
    } on PlatformException {
      result = 'Failed to stop scanner service.';
    }
    setState(() {
      _result = result;
    });
  }
```
