# Notus

Hide people's identity and image metadata, right on your phone. Nothing is sent: detection and rendering run on the device.

**Use:** open the page on your phone, choose a photo, adjust, save. "Add to Home Screen" to keep it as an app.

## Gestures

- Drag vertically (photo or bottom panel): pick an option.
- Drag horizontally or turn the dial: adjust. Flick to spin the dial.
- Tap the photo: full screen (pinch to zoom). Long press: show the original.
- Settings › Manual › Select faces: tap a face to remove or add its mask.

## Settings and styles

- **Threshold**: how many faces are masked, from the most obvious to the least certain.
- **Margin**: mask size around the face outline (0 to 1).
- **Overlay**: detector boxes, outlines, points and scores (never exported).
- **Styles**: Colour, Square, Noise, Emoji, Light (−100 dark · +100 light), Neon.

Exports JPEG or PNG with no EXIF metadata.

## Technical

A single static page, no build step.

- Detection: SCRFD-2.5G (InsightFace), two passes for crowds.
- Outline: 106 landmarks (InsightFace 2d106det).
- Inference: [onnxruntime-web](https://github.com/microsoft/onnxruntime) 1.22, WebAssembly.

```
index.html   the app
vendor/      onnxruntime-web (MIT)
models/      ONNX models (see licences)
```

Serve the folder as is (GitHub Pages, or `python3 -m http.server`).

## Licences

- **Code**: MIT, see [LICENSE](LICENSE).
- **onnxruntime-web**: MIT, © Microsoft.
- **Models `models/*.onnx`**: released by [InsightFace](https://github.com/deepinsight/insightface) **for non-commercial research use only**. They will be replaced with openly licensed models before any stable release.
