!SLIDE source transition=fade

# `model` #

    @@@
    ~/repos/GeoAlarms/src/main/java
    └── com
        └── geoalarms
            └── model
                ├── Alarm.java
                └── Coordinates.java

!SLIDE transition=scrollLeft
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

* public Coordinates(Location location);
* public Coordinates(GeoPoint point);
* public GeoPoint toGeoPoint();
