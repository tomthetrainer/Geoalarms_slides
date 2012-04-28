!SLIDE source

# database #

    @@@
    ~/repos/GeoAlarms/src/main/java
    └── com
        └── geoalarms
            └── database
                ├── AlarmDatabaseHelper.java
                └── AlarmManager.java

!SLIDE database

# A simple model #

     @@@sql
     CREATE TABLE alarms (
         radius      INTEGER NOT NULL,
         latitude    INTEGER NOT NULL,
         longitude   INTEGER NOT NULL,
         name        TEXT UNIQUE,
         description TEXT);

!SLIDE database

# AlarmDatabaseHelper #

## Encapsulates low-level database access. ##

* database creation
* insertion
* deletion


<!SLIDE GeoAlarms smaller>

# AlarmDatabaseHelper.java #
    @@@java
    public class AlarmDatabaseHelper extends SQLiteOpenHelper {

        // ...

        public void insert(int radius, 
                           int latitude, 
                           int longitude, 
                           String name, 
                           String description) {
            // ...
        }

        // ...

	    public void delete(String name) {
	        // ...
        }
    }

!SLIDE 

# AlarmManager #

## Our tiny ORM. ##

* Object-oriented interface to the database
* CRUD operations


<!SLIDE GeoAlarms smaller>

# `add` #
    @@@java
    public class AlarmManager { 

        // ...
 
        public void add(Alarm... alarms) {
            for(Alarm alarm: alarms) {
                try {
                    this.dbHelper
                        .insert(alarm.radius,
                                alarm.coordinates.latitude,
                                alarm.coordinates.longitude,
                                alarm.name,
                                alarm.description);
                } catch (SQLiteException e) {
                    // ...
                }
            }
        }
    }

<!SLIDE GeoAlarms smaller>

# `read` #
    @@@java
    public Alarm getAlarm(String name) {
        String nameField = "'" + name + "'";
        String where = this.dbHelper.KEY_NAME + 
                       "=" + nameField; 

        SQLiteDatabase db = this.dbHelper
                                .getReadableDatabase();
        Cursor cursor = db
                        .query(this.dbHelper.DATABASE_NAME,
                               this.dbHelper.KEYS,
                               where,                               
                               null,
                               null,
                               null,
                               null,
                               null);

        if (cursor.moveToFirst())
            return this.alarmFromCursor(cursor);
        else
            return null;
    }

<!SLIDE GeoAlarms smaller>

# from `Cursor` to `Alarm` #
    @@@java
    private Alarm alarmFromCursor(Cursor cursor) {
        int id = cursor.getInt(0);
        int radius = cursor.getInt(1);

        int latitude = cursor.getInt(2);
        int longitude = cursor.getInt(3);
        Coordinates coords = new Coordinates(latitude, 
                                             longitude);

        String name = cursor.getString(4);
        String description = cursor.getString(5);
 
        return new Alarm(id,
                         radius,
                         coords,
                         name,
                         description);
    } 
