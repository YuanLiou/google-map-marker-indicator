# google-map-marker-indicator [![](https://jitpack.io/v/YuanLiou/google-map-marker-indicator.svg)](https://jitpack.io/#YuanLiou/google-map-marker-indicator)

A simple and quick library to add number indicator on the marker of Android Google Map  <br>
<br>
<img width="400" alt="2018-09-22 21 29 49" src="https://user-images.githubusercontent.com/4803452/45917753-c6bf3d00-be6b-11e8-9785-60b7f1e07cfa.png">


## How to use
 1. Create a `MarkerIndicator`
   ```Kotlin
       // Create MarkerIndicator
       val markerIndicatorBuilder = MarkerIndicator.MarkerIndicatorBuilder(context)
       
       // set to `false` if you wish to use the value from `R.dimen.value`
       // or a pure pixel value
       markerIndicatorBuilder.setAutoConvertToDp(true)
       
       markerIndicatorBuilder.setTextSize(13f)
       markerIndicatorBuilder.setTextColor(R.color.primary_orange)
       markerIndicatorBuilder.setStrokeWidth(1.2f)
       markerIndicatorBuilder.setStrokeColor(R.color.primary_orange)
       markerIndicatorBuilder.setIndicatorRadius(9f)
       markerIndicatorBuilder.setBackgroundColor(R.color.white)
       markerIndicatorBuilder.setIndicatorMarginEnd(0.5f)
       markerIndicatorBuilder.setIndicatorMarginTop(2.7f)
       
       val markerIndicator = markerIndicatorBuilder.build()
   ```
 2. Create a marker `Bitmap` with indicator attached via `MarkerIndicator`
   ```Kotlin
       // Create Marker Bitmap
       val pinBitmap = markerIndicator.attachToMarkerDrawable(R.drawable.ic_pin, "<your_number_string>")
   ```
 3. Use `BitmapDescriptorFactory.fromBitmap(indicatorAttachedBitmap)` to create `BitmapDescriptor`
   ```Kotlin
       // Create BitmapDescriptor
       val bitmapDescriptor = BitmapDescriptorFactory.fromBitmap(pinBitmap)
   ```  
 4. Use this `BitmapDescriptor` to create marker.
   ```Kotlin
       // Create Marker
       val options = MarkerOptions().also {
           it.position(latLng)
           it.title(title)
           it.snippet(snippet)
           it.icon(bitmapDescriptor)
       }
       val generatedMarker = googleMap?.addMarker(options)
   ```
 
 We're done!
 
 ## Integration
 
  1. Add it in your root build.gradle at the end of repositories
   ```groovy
   allprojects {
       repositories {
           maven { url 'https://jitpack.io' }
       }
   }
   ```
  2. Add the dependency
   ```groovy
   implementation 'com.github.YuanLiou:google-map-marker-indicator:{latest_version}'
   ```

 ## Other
 #### Enable drawing debug Rect
 
 Preview:  <br>
 <img width="100" alt="2018-09-22 22 35 21" src="https://user-images.githubusercontent.com/4803452/45918331-ed35a600-be74-11e8-8760-974099fa5a82.png">

 It'll draw a semi-transparent gray layer to the marker.  <br>
 This feature help to check the actual marker size.
 
 ```kotlin
     // Enable drawing debug Rect
     markerIndicator.setDrawDebugBackgroundRect(true)
 ```
 
 
 
 
 
 
