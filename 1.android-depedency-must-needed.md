## Android Must Needed Depedency


#### Dependency
```sh
// ActivityX
val activity_version = "1.7.2"
implementation("androidx.activity:activity-ktx:$activity_version")

// FragmentX
val fragment_version = "1.6.1"
implementation("androidx.fragment:fragment-ktx:$fragment_version")

// Coroutines
implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.6.4")

// ViewModel and LifeCycle
val lifecycleVersion = "2.6.1"
implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:$lifecycleVersion")
implementation("lifecycle:lifecycle-viewmodel-ktx:$lifecycleVersion")
implementation("lifecycle:lifecycle-process:$lifecycleVersion")

// Glide
implementation ("com.github.bumptech.glide:glide:4.16.0")

val dataStoreVersion = "1.0.0"
implementation("androidx.datastore:datastore-preferences:$dataStoreVersion")

```
