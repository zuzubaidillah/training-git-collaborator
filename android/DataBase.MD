# DATABASE API

## Api Service

```js
Interface ApiService{
    @Headers("Accept: */*")
    @GET
    suspend fun download(@Url url: String): ResponseBody

    @GET("mobile/app/authentication/schools")
    suspend fun listSekolah(
        @Query("take") take: Int,
        @Query("skip") skip: Int,
        @Query("name") search: String = ""
    ): SekolahResponse

    @Multipart
    @POST("mobile/app/accounts/user/{userUuid}/change-avatar")
    suspend fun uploadProfilePicture(
        @Path("userUuid") userUuid: String,
        @Part file: MultipartBody.Part?
    ): Any
}

```

## DbConverter

    ```js

    @TypeConverters(DbConverter::class)
    abstract class MemoryDB : RoomDatabase() {

        abstract fun login(): LoginDao
        abstract fun feed(): FeedDao
        abstract fun announcement(): AnnouncementDao
    }
    ```

## Interface

````js

    @Dao
    interface LoginDao {

        @Insert(onConflict = OnConflictStrategy.REPLACE)
        suspend fun insertSchool(data: List<SekolahItem>)

        @Insert(onConflict = OnConflictStrategy.REPLACE)
        suspend fun insertSchool(school: SekolahItem)

        @Query("select * from school where name like :search order by id desc")
        fun getListSchool(search: String): DataSource.Factory<Int, SekolahItem>

    ```
 "untuk data dan kebutuhan menyesuaikan sistem yang dibuat"

## Entity

```js
    @Keep
    @JsonClass(generateAdapter = true)
    data class SekolahResponse(val data: List<SekolahItem> = emptyList())

    @Keep
    @JsonClass(generateAdapter = true)
    @Entity(
    tableName = "school",
    indices = [Index(name = "school_rowidx", value = ["id"], unique = true)]
    )
    data class SekolahItem(
    @PrimaryKey val id: Int = 0,
    val uuid: String = "",
    val name: String = "",
    val image: String = "",
    val address: String = "",
    val coordinate_radius: String? = "50",
    val coordinate_latitude: Double? = 0.0,
    val coordinate_longitude: Double? = 0.0
    )
````

## ViewModel

```js
    class LoginViewModel @Inject constructor(
        val context: Context,
        val moshi: Moshi,
        val pref: PreferenceClass,
        val intentUtil: IntentUtil,
        val db: MemoryDB,
        private val apiWrapper: ApiWrapper,
        private val apiService: ApiService
    ) : ViewModel() {

        "untuk data sesuaikan disini"
    }
```
