# amazon_s3_cognito


Amazon S3 plugin for Flutter

Unofficial Amazon S3 plugin written in Dart for Flutter.

The plugin is extension if flutter-amazon-s3 plugin which can be found here 
https://pub.dev/packages/flutter_amazon_s3. This plugin adds image delete functionality and also
it allows user to upload image when region and sub-region are different.

Plugin in maintained by fäm properties<no-reply@famproperties.com>.

## Usage
To use this plugin, add `amazon_s3_cognito` as a [dependency in your pubspec.yaml file](https://flutter.io/platform-plugins/).


```yaml
dependencies:
The package is android-x compatible
  amazon_s3_cognito: '^0.2.0' 
```

### Example



``` dart
import 'package:amazon_s3_cognito/amazon_s3_cognito.dart';
import 'package:amazon_s3_cognito/aws_region.dart';

//this method only supports image upload. 
String uploadedImageUrl = await AmazonS3Cognito.uploadImage(
          _image.path, BUCKET_NAME, IDENTITY_POOL_ID);
          

//Use the below code to specify the region and sub region for image upload
//Also this method allows to upload all file type including images and pdf etc.
//We recommend to use this method always. 
String uploadedImageUrl = await AmazonS3Cognito.upload(
            _image.path,
            BUCKET_NAME,
            IDENTITY_POOL_ID,
            IMAGE_NAME,
            AwsRegion.US_EAST_1,
            AwsRegion.AP_SOUTHEAST_1)
            
//use below code to delete an image
 String result = AmazonS3Cognito.delete(
            BUCKET_NAME,
            IDENTITY_POOL_ID,
            IMAGE_NAME,
            AwsRegion.US_EAST_1,
            AwsRegion.AP_SOUTHEAST_1)
            
            
        

```
          
## Installation


### Android

No configuration required for Debug - the plugin should work out of the box.

For Release Version. You need to configure proguard.

1. Add below config at `android/app/build.gradle` file inside `buildTypes` section.

```
buildTypes {
    release {
            // Signing with the debug keys for now, so `flutter run --release` works.
            signingConfig signingConfigs.debug
            multiDexEnabled true
            minifyEnabled true
            useProguard true
            proguardFiles getDefaultProguardFile('proguard-android.txt'),
            'proguard-rules.pro'
        }
}
```
2. Create `proguard-rules.pro` File at `android\app\proguard-rules.pro` and add below content.

```
-keep class com.amazonaws.** { *; }
-keep class com.amazon.** { *; }
-keep class com.pycampers.** { *; }
```



### iOS

No configuration required - the plugin should work out of the box.          

### Authors
```
the plugin is created and maintained by fäm properties. 
Android version written by Prachi Shrivastava
IOS version written by Prachi Shrivastava
```
