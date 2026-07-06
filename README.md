# cdn

A personal collection of vendored third-party JS builds, served via [jsDelivr's GitHub CDN](https://www.jsdelivr.com/documentation#id-github): any file in this repo is reachable at

```
https://cdn.jsdelivr.net/gh/davidchatting/cdn/<path>
```

## Structure

One folder per library, named after the library, containing its build file(s) as vendored:

```
cdn/
  opencv/
    opencv.js
```

Add new libraries the same way: `<library-name>/<file>`, using version subfolders (`<library-name>/<version>/<file>`) if more than one version needs to stay addressable at once.

## Contents

### `opencv/opencv.js`

A prebuilt browser/WASM build of [OpenCV.js](https://docs.opencv.org/4.x/d5/d10/tutorial_js_root.html).

- **Version:** 4.5.1 (built 2020-12-21, via Emscripten/em++ 10.0.0)
- **License:** Apache License 2.0 (OpenCV's license from 4.5.0 onward)
- **Modules included:** `calib3d`, `core`, `dnn`, `features2d`, `flann`, `imgproc`, `js`, `objdetect`, `photo`, `video`
- **Modules excluded:** `highgui`, `imgcodecs`, `ml`, `stitching`, `videoio`, `world` (browser build - no native GUI/file I/O)
- Confirmed at runtime via `cv.getBuildInformation()`.

A copy is also kept at the repo root (`/opencv.js`) for backward compatibility - several existing sites reference it there directly:

- [davidchatting/opencv-featurematch](https://github.com/davidchatting/opencv-featurematch) (`main` and `segmention` branches, and its `demos/`)
- [davidchatting-bot/RugbySynth](https://github.com/davidchatting-bot/RugbySynth)

New integrations should use `opencv/opencv.js` instead of the root copy.

## A note on jsDelivr caching

jsDelivr caches files fetched via a branch name (e.g. `@main`, or no version tag at all, as above) for up to 24 hours, purgeable via:

```
https://purge.jsdelivr.net/gh/davidchatting/cdn/opencv/opencv.js
```

For content that should never change once published, consider pinning to a commit hash instead: `cdn.jsdelivr.net/gh/davidchatting/cdn@<commit-sha>/opencv/opencv.js`.
