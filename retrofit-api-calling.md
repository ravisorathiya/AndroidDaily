# Api Calling

### Installation

```sh
implementation ("com.squareup.retrofit2:retrofit:2.9.0")
implementation ("com.google.code.gson:gson:2.9.0")
```

### Create Retrofit Singleton
```sh
object RetrofitClient {

    private const val BASE_URL = "https://jsonplaceholder.typicode.com/"

    val retrofit: Retrofit by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .addConverterFactory(GsonConverterFactory.create())
            .build()
    }

    val apiService: ApiService by lazy {
        RetrofitClient.retrofit.create(ApiService::class.java)
    }

}
```

### Create an interface for calling API

```sh

@GET("get_all_todo.php")
suspend fun getParticles(): JsonObject

@GET("shared_post.php?fromApp=true&id=:id")
suspend fun getApiData(@Query("id") id: String): JsonObject

```
