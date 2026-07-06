# cdn

A personal collection of vendored third-party JS builds and personal utility scripts, served via [jsDelivr's GitHub CDN](https://www.jsdelivr.com/documentation#id-github): any file in this repo is reachable at

```
https://cdn.jsdelivr.net/gh/davidchatting/cdn/<path>
```

## Contents

### `opencv/4.5.1/opencv.js`

A prebuilt browser/WASM build of [OpenCV.js](https://docs.opencv.org/4.x/d5/d10/tutorial_js_root.html).

- **Version:** 4.5.1 (built 2020-12-21, via Emscripten/em++ 10.0.0)
- **License:** Apache License 2.0 (OpenCV's license from 4.5.0 onward)
- **Modules included:** `calib3d`, `core`, `dnn`, `features2d`, `flann`, `imgproc`, `js`, `objdetect`, `photo`, `video`
- **Modules excluded:** `highgui`, `imgcodecs`, `ml`, `stitching`, `videoio`, `world` (browser build - no native GUI/file I/O)
- Confirmed at runtime via `cv.getBuildInformation()`.

### `shimage/1.0.0/shimage.js`

Image shims for p5.js (converting between `ImageBitmap`/`HTMLCanvasElement`/OpenCV `Mat` and `p5.Image`). Originally developed in [davidchatting/p5js-experiments](https://github.com/davidchatting/p5js-experiments) (`js/shimage.js`), which has no version numbers of its own - `1.0.0` starts fresh here, following semver from this point on.
