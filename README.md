fluid-country
=============

[![Maven Central](https://img.shields.io/maven-central/v/io.fluidsonic.country/fluid-country?label=Maven%20Central)](https://search.maven.org/artifact/io.fluidsonic.country/fluid-country)
[![JCenter](https://img.shields.io/bintray/v/fluidsonic/kotlin/country?label=JCenter)](https://bintray.com/fluidsonic/kotlin/country)
[![Tests](https://github.com/fluidsonic/fluid-country/workflows/Tests/badge.svg)](https://github.com/fluidsonic/fluid-country/actions?workflow=Tests)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.4.0%20(Darwin,%20JVM,%20JS)-blue.svg)](https://github.com/JetBrains/kotlin/releases/v1.4.0)
[![#fluid-libraries Slack Channel](https://img.shields.io/badge/slack-%23fluid--libraries-543951.svg?label=Slack)](https://kotlinlang.slack.com/messages/C7UDFSVT2/)

Kotlin multiplatform `Country` support.



Installation
------------

`build.gradle.kts`:
```kotlin
dependencies {
    implementation("io.fluidsonic.country:fluid-country:0.9.0")
}
```



Usage
-----

```kotlin
println(Country.fromCode("US").name) // United States of America (the)
```

### `class Country`

A class with information about a specific country defined by [ISO 3166-1](https://www.iso.org/obp/ui/).

```kotlin
val country = Country.forCode("US") // throws if code is invalid (not defined by ISO 3166-1) or has an invalid format (not two latin letters)
println(country.code) // US
println(country.code(CountryCode.Format.iso3166_alpha3)) // USA
println(country.name) // United States of America (the)
println(country.numericCode) // 840
```

```kotlin
val country = Country.forCodeOrNull("ABC123") // null if code is invalid (not defined by ISO 3166-1) or has an invalid format (not two latin letters)
println(country) // null
```

### `class CountryCode`

An inline class for ISO 3166-1 alpha-2 country codes (e.g. `US` or `DE`).

```kotlin
val code = CountryCode.parse("US") // throws if code has invalid format (not two latin letters)
println(code.toString()) // US
println(code.isValid()) // true - 'US' is defined by ISO 3166-1
```

```kotlin
val code = CountryCode.parse("aa") // throws if code has invalid format (not two latin letters)
println(code.toString()) // AA
println(code.isValid()) // false - 'AA' is not defined by ISO 3166-1
```

```kotlin
val code = CountryCode.parseOrNull("ABC123") // null if code has invalid format (not two latin letters)
println(code) // null
```



License
-------

Apache 2.0