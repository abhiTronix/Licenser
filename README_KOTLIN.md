# Licenser  [![API](https://img.shields.io/badge/API-14%2B-blue.svg?style=flat)](https://android-arsenal.com/api?level=14) 
An android library to display the licenses of your application libraries in a easy way.

_Click [here](https://github.com/marcoscgdev/Licenser/blob/master/README.md) for the Java version of this readme._

---

## Releases:

#### Current release: 1.0.7.

You can see all the library releases [here](https://github.com/marcoscgdev/Licenser/releases).

---

## Wiki

You can access Licenser wiki [here](https://github.com/marcoscgdev/Licenser/wiki).

## Demo:

You can download the **sample apk** [here](https://github.com/marcoscgdev/Licenser/releases/download/1.0.6/app-debug.apk).

<img src="https://raw.githubusercontent.com/marcoscgdev/Licenser/master/device-2018-02-11-161003.png" width="350">

---

## Usage:

#### Step: 1 - adding the library via Gradle

First of all add this to your root *build.gradle* file:

```groovy
allprojects {
    repositories {
        maven { url "https://jitpack.io" }
    }
}
```

Now add the dependency to your app *build.gradle* file:

```groovy
implementation 'com.github.marcoscgdev:Licenser:1.0.7'
```

#### Step: 2 - creating a dialog

*You have to use an AppCompatActivity*

```java
LicenserDialog(this)
        .setTitle("Licenses")
        .setCustomNoticeTitle("Notices for files:")
        .setBackgroundColor(Color.RED) // Optional
        .setLibrary(Library("Android Support Libraries",
                "https://developer.android.com/topic/libraries/support-library/index.html",
                License.APACHE2)) // APACHE deprecated, see wiki
        .setLibrary(Library("Example Library",
                "https://github.com/marcoscgdev",
                License.APACHE2)) // APACHE deprecated, see wiki
        .setLibrary(Library("Licenser",
                "https://github.com/marcoscgdev/Licenser",
                License.MIT))
        .setPositiveButton(android.R.string.ok, object:DialogInterface.OnClickListener() {
            fun onClick(dialogInterface:DialogInterface, i:Int) {
                // TODO: 11/02/2018
            }
        })
        .show()
```

**NEW:** You can set a custom AlertDialog theme.

```
LicenserDialog(this, R.style.DialogStyle)
        ...
```

Library structure:

```java
var lib1 = Library(String title, String url, int licenseType)
```

LICENSE TYPES (At this moment):

```java
 - License.APACHE1 // Apache v1
 - License.APACHE1_1 // Apache v1.1
 - License.APACHE2 // Apache v2
 - License.BSD3 // BSD v3
 - License.BSD4 // BSD v4
 - License.BSL // BSL
 - License.CREATIVE_COMMONS // Creative commons
 - License.FREEBSD // FreeBSD
 - License.GNU2 // GNU v2
 - License.GNU3 // GNU v3
 - License.ISC // ISC
 - License.LGPL2_1 // GNU Lesser v2.1
 - License.LGPL3 // GNU Lesser v3
 - License.MIT // MIT
 - License.NTP // NTP
 ```
 
 ```java
var lib1 = Library("Library name", "https://github.com/marcoscgdev", License.APACHE)
 ```

**If you don't want a dialog, you can use the Licenser class:**

```java
var licenser = Licenser()
        .setCustomNoticeTitle("Notices for files:")
        .setLibrary(Library("Android Support Libraries",
                "https://developer.android.com/topic/libraries/support-library/index.html",
                License.APACHE))
        .setLibrary(Library("Example Library",
                "https://github.com/marcoscgdev",
                License.APACHE))
        .setLibrary(Library("Licenser",
                "https://github.com/marcoscgdev/Licenser",
                License.MIT))
```

And show it in a webview:

```java
val webView = findViewById(R.id.webView) as WebView
webView.loadData(licenser.getHTMLContent(), "text/html; charset=UTF-8", null)
```

#### Extra functions

You can access this functions with both classes

```java
var licenses = licenser.getHTMLContent() // HTML content
var apacheLibraries = licenser.getApacheLibraries()
var mitLibraries = licenser.getMitLibraries()
var gnuLibraries = licenser.getGnuLibraries()
```

---
>See the *sample project* to clarify any queries you may have.

---

## License

```
The MIT License (MIT)

Copyright (c) 2018 Marcos Calvo García

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
