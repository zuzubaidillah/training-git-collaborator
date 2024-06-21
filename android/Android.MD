# API ANDROID STUDIO (KOTLIN)

    A. PROSES PENGUNAAN API

    1. MEMBUAT MODEL DATA
        BUAT CLASS DATA UNTUK MENATAKAN RESPON DARI API YANG DIBUAT
        EXSEMPEL JSON :

# API

```json
{
    "userId": 1,
    "Id"     = 1,
    "title"  = "sampel"
    "Body"   = "sampel"
}
```

# CLASS DATA API

```kotlin
{
    val userId = Int,
    val Id     = Int,
    val title  = String,
    val Body   = String
}
```

    2. MEMBUAT INTERFACE API (API SERVICE)
        DIBUAT UNTUK MENGIDENTIFIKASI ENPOINT API MENGUNAKAN "RETROFIT"

        EX :
            Import retrofit2.Call
            Import retrofit2.Http.* / Get

            Interface ApiService {
                @Get ("Post")

                fun Get Post() : Call<List<post>>
            }

    3. KONFIGURASI RETROFIT
        BUAT INTERFACE RETROFIT DI CLASS YANG SESUAI

    4. MENGUNAKAN API DI ACTIVITY ATAU VIEW MODEL
        BERFUNGSI UNTUK MEMBUAT PRINTAH JAGRINGAN UANG DIAMBIL DARI API



    # LIBRARY RECYCERVIEW KONFIGURASI IMPLEMENTASI NETWORKING API

    ```Implementasi

    // Butterknife
    implementation 'com.jakewharton:butterknife:9.0.0-rc2'
    annotationProcessor 'com.jakewharton:butterknife-compiler:9.0.0-rc2'

    // Recyclerview
    implementation 'com.android.support:recyclerview-v7:28.0.0'

    // Design
    implementation 'com.android.support:design:28.0.0'

    // Retrofit
    implementation 'com.squareup.retrofit2:retrofit:2.5.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.5.0'

    // Okhttp
    implementation 'com.squareup.okhttp3:okhttp:3.12.0'
    implementation 'com.github.bumptech.glide:glide:4.8.0'

    ```
