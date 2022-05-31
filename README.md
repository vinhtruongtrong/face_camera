# face_camera

#### A Flutter camera plugin that detects face in real-time.

### Installation
First, add `face_camera` as a dependency in your pubspec.yaml file.

```yaml  
face_camera: ^0.0.1
```

### iOS
* Minimum iOS Deployment Target: 10.0
* Follow this <a href="https://developer.apple.com/support/required-device-capabilities/">link</a> and setup  `ML Kit` this is required for `face_camera` to function properly in `iOS`

Add two rows to the `ios/Runner/Info.plist:`
* one with the key `Privacy - Camera Usage Description` and a usage description.
* and one with the `key Privacy - Microphone Usage Description` and a usage description.

If editing `Info.plist` as text, add:

```xml  
<key>NSCameraUsageDescription</key>
<string>your usage description here</string>
<key>NSMicrophoneUsageDescription</key>
<string>your usage description here</string>
  
```


### Android
* Change the minimum Android sdk version to 21 (or higher) in your `android/app/build.gradle` file.

```groovy
minSdkVersion 21
```


### Usage
* The first step is to initialize `face_camera` in `main.dart`
```dart
void main() async{
  WidgetsFlutterBinding.ensureInitialized(); //Add this

  await FaceCamera.intialize(); //Add this

  runApp(const MyApp());
}
```
* Then render the component in your application setting the onCapture callback.
```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SmartFaceCamera(
          autoCapture: true,
          defaultCameraLens: CameraLens.front,
          message: 'Center your face in the sqaure',
          onCapture: (File? image){
            setState(()=> _capturedImage=image);
          },
        )
    );
  }
```

## Customization

Here is a list of properties available to customize your widget:

| Name | Type | Description |
|-----|-----|------|
|imageResolution| ImageResolution | used this to set image resolution |
|defaultCameraLens| CameraLens | used this to set initial camera lens direction |
|defaultFlashMode| CameraFlashMode | used this to set initial camera flash mode |
|enableAudio| bool | set false to disable caputre sound |
|autoCapture| bool | set true to capture image on face detected |
|showControls| bool | set false to hide all controls |
|showCaptureControl| bool | set false to hide capture icon button |
|showFlashControl| bool | set false to hide flash control icon button |
|showCameraLensControl| bool | set false to hide camera lens control icon button |
|message| String | use this pass a message above the camera |
|messageStyle| TextStyle | style applied to the message widget |
|orientation| CameraOrientation | use this to lock camera orientation |
|onCapture| Function(File) | callback invoked when camera captured image |
|captureControlIcon| Widget | use this to render a custom widget for capture control |
|lensControlIcon| Widget | use this to render a custom widget for camera lens control |
|flashControlBuilder| FlashControlBuilder | use this to build a custom widget for flash control based on camera flash mode |


### Support the Library

You can support the library by liking it on pub, staring in on Github and reporting any bugs you encounter.