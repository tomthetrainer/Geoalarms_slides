!SLIDE source

# model #

    @@@
    ~/repos/GeoAlarms/src/main/java
    └── com
        └── geoalarms
            └── model
                ├── Alarm.java
                └── Coordinates.java

!SLIDE
# Alarm #
* int         : radius
* Coordinates : coordinate
* String      : name
* String      : description

!SLIDE small transition=scrollLeft
# Coordinates #
* int : longitude
* int : latitude 

# Remarcable methods #
* public Coordinates(Location location);
* public Coordinates(GeoPoint point);
* public GeoPoint toGeoPoint();
