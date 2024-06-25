# API SERVICE

## RETROFIT KE BUIL.GRADLE :

```JS
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
}

```

## MODAL DATA

    ```js

    data class User(
        val id: Int,
        val name: String,
        val username: String,
        val email: String
        )
    ```

## BUAT INTERFACE API SERVICE

    Buat interface yang mendefinisikan endpoint Api yang akan diakses :

    ```js

        import retrofit2.Call
        import retrofit2.http.GET

        interface ApiService {
            @GET("users")
            fun getUsers(): Call<List<User>>
        }

    ```

## INSTALASI RETROFIT

    Buat interface Retrofit yang akan digunkan untuk membuat panggilan APi :

    ```js

        import retrofit2.Retrofit
        import retrofit2.converter.gson.GsonConverterFactory

        object RetrofitClient {
            private const val BASE_URL = "https://jsonplaceholder.typicode.com/"

            val instance: Retrofit by lazy {
                Retrofit.Builder()
                    .baseUrl(BASE_URL)
                    .addConverterFactory(GsonConverterFactory.create())
                    .build()
            }

            val api: ApiService by lazy {
                instance.create(ApiService::class.java)
            }
        }

    ```

## MENGUNAKAN API SERVICE :

    Buat panggilan Api dan Proses Responnya :

    ```js

    import android.os.Bundle
    import android.util.Log
    import androidx.appcompat.app.AppCompatActivity
    import retrofit2.Call
    import retrofit2.Callback
    import retrofit2.Response

    class MainActivity : AppCompatActivity() {
        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContentView(R.layout.activity_main)

            // Memanggil API
            RetrofitClient.api.getUsers().enqueue(object : Callback<List<User>> {
                override fun onResponse(call: Call<List<User>>, response: Response<List<User>>) {
                    if (response.isSuccessful) {
                        val users = response.body()
                        users?.forEach {
                            Log.d("MainActivity", "User: ${it.name}, Email: ${it.email}")
                        }
                    }
                }

                override fun onFailure(call: Call<List<User>>, t: Throwable) {
                    Log.e("MainActivity", "Error: ${t.message}")
                }
            })
        }
    }

    ```
