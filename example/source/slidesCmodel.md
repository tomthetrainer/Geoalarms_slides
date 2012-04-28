!SLIDE source

# `model` #

    @@@
    ~/repos/GeoAlarms/src/main/java
    └── com
        └── geoalarms
            └── model
                ├── Alarm.java
                └── Coordinates.java

!SLIDE
# `Alarm` #

## stores information about an alarm:
* radius
* coordinates
* name
* description

<!SLIDE small transition=scrollLeft>

# `Coordinates` #

## our representation of coordinates:
* latitude 
* longitude

## convert to/from Android location objects:
* `android.location.Location`
* `com.google.android.maps.GeoPoint`
