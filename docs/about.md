# About

Totly is built with [Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform.html). All business logic is shared Kotlin, rendered with Compose Multiplatform on Android and desktop and with native SwiftUI on iOS.

## Libraries Used

### Shared

* [Kotlin Multiplatform](https://github.com/JetBrains/kotlin) - shared code across Android, desktop and iOS
* [App Platform](https://github.com/vRallev/app-platform) - presenters, renderers, scopes and module structure
* [Metro](https://github.com/ZacSweers/metro) - compile-time dependency injection
* [Coroutines](https://github.com/Kotlin/kotlinx.coroutines) - asynchronous code and flows
* [kotlinx-datetime](https://github.com/Kotlin/kotlinx-datetime) - multiplatform date time library
* [SQLDelight](https://github.com/sqldelight/sqldelight) - sqlite database
* [multiplatform-settings](https://github.com/russhwolf/multiplatform-settings) - key value storage
* [moko-resources](https://github.com/icerockdev/moko-resources) - localized strings shared with iOS
* [BuildKonfig](https://github.com/yshrsmz/BuildKonfig) - build-time configuration

### Client

* [Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform) - Android and desktop UI, Material 3 and icons
* [Navigation 3](https://github.com/JetBrains/compose-multiplatform-core) - back stacks for the Compose UI
* [AndroidX Activity](https://github.com/androidx/androidx) - Android entry point
* [SwiftUI](https://developer.apple.com/xcode/swiftui/) - native iOS UI

### Server

* [Supabase](https://supabase.com/) - auth, database, storage and edge functions
* [supabase-kt](https://github.com/supabase-community/supabase-kt) - Kotlin Multiplatform Supabase client
* [Ktor](https://github.com/ktorio/ktor) - HTTP client (OkHttp on Android and desktop, Darwin on iOS)

### Testing

* [Kotlin test](https://kotlinlang.org/api/core/kotlin-test/) - KMP testing framework
* [AssertK](https://github.com/willowtreeapps/assertk) - assertions
