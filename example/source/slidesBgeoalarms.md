!SLIDE geoalarms transition=fade

# `GeoAlarms` #

    @@@
    ~/repos/GeoAlarms/src/main/java
    └── com
        └── geoalarms
            └── GeoAlarms.java

!SLIDE explanation transition=scrollLeft

# `GeoAlarms` #

* holds application global state in static members  
  * context  
  * database connection
  * location  
* accessible from every class inside the application

<!SLIDE smaller transition=scrollLeft>

# `GeoAlarms` #

    @@@ java
    public class GeoAlarms extends Application {

        // global objects
        public static Context context;
        public static AlarmManager alarmManager;
        public static LocListener locationListener;

        // ...

        @Override
        public void onCreate(){
            super.onCreate();
            GeoAlarms.context = this.getApplicationContext();
            GeoAlarms.alarmManager = new AlarmManager();
            GeoAlarms.locationListener = new LocListener();
        }
    }
