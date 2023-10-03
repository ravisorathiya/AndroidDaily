# Room Database

### Installation
```sh
val room_version = "2.5.2"
implementation("androidx.room:room-runtime:$room_version")
kapt("androidx.room:room-compiler:$room_version")
implementation("androidx.room:room-ktx:$room_version")
```
### Create Database  Singleton
```sh
import android.content.Context
import androidx.room.Database
import androidx.room.Room
import androidx.room.RoomDatabase

@Database(
    entities = [YourEntityClass::class],
    version = 1,
    exportSchema = true
)
abstract class AppDatabase : RoomDatabase() {
    abstract fun getDao(): SampleDao

    companion object {

        @Volatile
        private var INSTANCE: AppDatabase? = null

        fun getDatabase(context: Context): AppDatabase {
            val tempInstance = INSTANCE
            if (tempInstance != null) {
                return tempInstance
            }
            synchronized(this) {
                val instance = Room.databaseBuilder(
                    context.applicationContext,
                    AppDatabase::class.java,
                    (AppDatabase::class.java).toString()
                ).build()
                INSTANCE = instance
                return instance
            }
        }
    }
}
```

### Create interface dao
```sh
@Dao
interface SampleDao {

    @Query("SELECT * FROM tbl_theme WHERE isLiked = 1")
    fun getLikedTheme(): Flow<List<TempEntity>>

    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insertTheme(theme: TempEntity)

    @Query("DELETE FROM tbl_theme WHERE isLiked = 0")
    suspend fun deleteLikedThemes()

    @Delete
    suspend fun deleteThemes(theme: TempEntity): Int

    @Query("SELECT *  FROM tbl_theme WHERE id = :id")
    suspend fun getLikedTheme(id: String): TempEntity?

    @Query("DELETE FROM tbl_theme WHERE id = :id")
    suspend fun deleteFavIfExist(id : String)

}
```
