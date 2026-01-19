# Overview

Minimal hello-world with Meson. Native build works out of the box; Emscripten build uses a Meson cross file for emcc/em++.

## Build Setup
```
$ meson setup [--buildtype=release] build[/native|/wasm][/debug|/release] [--cross-file config/emscripten.ini]
```

## Compile
```
$ meson compile -C build[/native|/wasm][/debug|/release]
```

## Run
* Native
  ```
  $ build[/native][/debug|/release]/hello
  ```
* Browser
  ```
  $ python3 -m http.server <8080> --directory build[/wasm][/debug|/release]
  ```
