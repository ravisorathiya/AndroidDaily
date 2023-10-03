## Jetpack Datastore 

#### Docs

[https://developer.android.com/topic/libraries/architecture/datastore](https://developer.android.com/topic/libraries/architecture/datastore)

Jetpack datastore offical documentation

#### Dependency

```
   implementation("androidx.datastore:datastore-preferences:1.0.0")
```

#### Helper methods for shared-prefernces 

```kotlin

private val Context.dataStore: DataStore<Preferences> by preferencesDataStore(name = "settings")

suspend fun <T> Context.setValue(key: Preferences.Key<T>, value: T) {
    dataStore.edit {
        it[key] = value
    }
}

suspend fun <T> Context.readValue(key: Preferences.Key<T>): T? {
    return dataStore.data.first()[key]
}

suspend fun <T> Context.deletePrefKey(key: Preferences.Key<T>) {
    val dataStore = dataStore
    dataStore.edit {
        it.remove(key)
    }
}


suspend fun <T> Fragment.setValue(key: Preferences.Key<T>, value: T) {
    requireContext().dataStore.edit {
        it[key] = value
    }
}


suspend fun <T> Fragment.readValue(key: Preferences.Key<T>): T? {
    return requireContext().dataStore.data.first()[key]
}

suspend fun <T> Fragment.deletePrefKey(key: Preferences.Key<T>) {
    val dataStore = requireContext().dataStore
    dataStore.edit {
        it.remove(key)
    }
}

```

## Usage


#### by using extension function on the context  
```kotlin

 //  set preference
 setValue(stringPreferencesKey("your_key"), "value")
 setValue(booleanPreferencesKey("your_key"), true)
 setValue(intPreferencesKey("your_key"), 420)
 setValue(floatPreferencesKey("your_key"), 0.5f)
 setValue(doublePreferencesKey("your_key"), 10.5)
 setValue(longPreferencesKey("your_key"), 400L)

 //  get preference
 readValue(stringPreferencesKey("your_key"))
 readValue(booleanPreferencesKey("your_key"))
 readValue(intPreferencesKey("your_key"))
 readValue(floatPreferencesKey("your_key"))
 readValue(doublePreferencesKey("your_key"))
 readValue(longPreferencesKey("your_key"))

 //  delete preference
 deletePrefKey(stringPreferencesKey("your_key"))
 deletePrefKey(booleanPreferencesKey("your_key"))
 deletePrefKey(intPreferencesKey("your_key"))
 deletePrefKey(floatPreferencesKey("your_key"))
 deletePrefKey(doublePreferencesKey("your_key"))
 deletePrefKey(longPreferencesKey("your_key"))

```



