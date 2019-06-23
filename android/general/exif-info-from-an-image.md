# How to read exif info from an image

To read exif info an image add the following dependency into your apps build.gradle file
```
compile/implementation "com.android.support:exifinterface:25.1.0"
```

For apps that receive images from other apps with a content:// URI (such as those sent by apps that target API 24 or higher), ExifInterface now works directly off of an InputStream; this allows you to easily extract Exif information directly out of content:// URIs you receive without having to create a temporary file.
```
Uri uri; // the URI you've received from the other app
InputStream in;
try {
  in = getContentResolver().openInputStream(uri);
  ExifInterface exifInterface = new ExifInterface(in);
  // Now you can extract any Exif tag you want
  // Assuming the image is a JPEG or supported raw format
} catch (IOException e) {
  // Handle any errors
} finally {
  if (in != null) {
    try {
      in.close();
    } catch (IOException ignored) {}
  }
}
```

Note: ExifInterface will not work with remote InputStreams, such as those returned from a HttpURLConnection. It is strongly recommended to only use them with content:// or file:// URIs.

For most attributes, you'd simply use the getAttributeInt(), getAttributeDouble(), or getAttribute() (for Strings) methods as appropriate.

One of the most important attributes when it comes to displaying images is the image orientation, stored in the aptly-named TAG_ORIENTATION, which returns one of the ORIENTATION_ constants. To convert this to a rotation angle, you can post-process the value.
```
int rotation = 0;
int orientation = exifInterface.getAttributeInt(
    ExifInterface.TAG_ORIENTATION,
    ExifInterface.ORIENTATION_NORMAL);
switch (orientation) {
  case ExifInterface.ORIENTATION_ROTATE_90:
    rotation = 90;
    break;
  case ExifInterface.ORIENTATION_ROTATE_180:
    rotation = 180;
    break;
  case ExifInterface.ORIENTATION_ROTATE_270:
    rotation = 270;
    break;
}
```

There are some helper methods to extract values from specific Exif tags. For location data, the getLatLong() method gives you the latitude and longitude as floats and getAltitude() will give you the altitude in meters. Some images also embed a small thumbnail. You can check for its existence with hasThumbnail() and then extract the byte[] representation of the thumbnail with getThumbnail() - perfect to pass to BitmapFactory.decodeByteArray().

Working with Exif: Everything is optional
One thing that is important to understand with Exif data is that there are no required tags: each and every tag is optional - some services even specifically strip Exif data. Therefore throughout your code, you should always handle cases where there is no Exif data, either due to no data for a specific attribute or an image format that doesn't support Exif data at all (say, the ubiquitous PNGs or WebP images).
