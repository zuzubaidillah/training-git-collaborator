# API ANDROID STUDIO (KOTLIN)

    A. PROSES PENGUNAAN API

    1. MEMBUAT MODEL DATA
        BUAT CLASS DATA UNTUK MENATAKAN RESPON DARI API YANG DIBUAT
        EXSEMPEL JSON :

        # API
        {
            "userId" = 1,
            "Id"     = 1,
            "title"  = "sampel"
            "Body"   = "sampel"
        }

        # CLASS DATA API
        {
            val userId = Int,
            val Id     = Int,
            val title  = String,
            val Body   = String
        }

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
