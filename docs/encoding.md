# Encoding Parameters

Reference for all encoding options exposed by [FastEdit](https://fastedit.net). These map directly to the underlying codec configurations.

## Animated WebP (libwebp)

FastEdit exposes the complete `WebPConfig` struct from [libwebp](https://chromium.googlesource.com/webm/libwebp/) via a [custom WebAssembly build](https://github.com/HaMMeRSI/webp-wasm).

| Parameter | Range | Default | Description |
|---|---|---|---|
| `quality` | 0–100 | 80 | Lossy compression quality. Higher = better quality, larger file. |
| `lossless` | bool | false | Lossless encoding. Ignores quality when enabled. |
| `method` | 0–6 | 4 | Compression method. 0 = fastest, 6 = best compression. |
| `pass` | 1–10 | 1 | Number of entropy analysis passes. More passes = better compression, slower. |
| `sharpYuv` | bool | true | Use sharp RGB→YUV conversion. Better color accuracy at edges. |
| `preprocessing` | 0–2 | 0 | 0 = none, 1 = segment-smooth, 2 = pseudo-random dithering. |
| `snsStrength` | 0–100 | 50 | Spatial noise shaping. Higher = more adaptive quantization. |
| `filterStrength` | 0–100 | 60 | Deblocking filter strength. |
| `filterSharpness` | 0–7 | 0 | Filter sharpness. 0 = sharpest, 7 = least sharp. |
| `filterType` | bool | true | true = strong filter, false = simple filter. |
| `autofilter` | bool | false | Auto-adjust filter strength per segment. |
| `alphaQuality` | 0–100 | 100 | Alpha channel compression quality. |
| `alphaCompression` | bool | true | Compress alpha channel (vs. raw). |
| `alphaFiltering` | 0–2 | 1 | Alpha pre-filtering. 0 = none, 1 = fast, 2 = best. |
| `nearLossless` | 60–100 | 100 | Near-lossless preprocessing. 100 = no preprocessing (true lossless). |
| `exact` | bool | false | Preserve RGB values in transparent areas. |
| `segments` | 1–4 | 4 | Number of macroblock segments for lossy encoding. |
| `partitions` | 0–3 | 0 | Log2 of the number of token partitions. |
| `partitionLimit` | 0–2 | 0 | Quality degradation limit for partitions. |
| `emulateJpegSize` | bool | false | Try to match JPEG output size at equivalent quality. |
| `keyframeInterval` | 0+ | 17 | Maximum frames between keyframes. 0 = encoder decides. |
| `loopCount` | 0+ | 0 | Number of loops. 0 = infinite. |
| `targetSize` | bytes | 0 | Target file size. 0 = disabled. Overrides quality when set. |

## Video (MP4 / WebM / MKV)

| Parameter | Options | Default | Description |
|---|---|---|---|
| `codec` | `avc` (H.264), `hevc` (H.265), `vp8`, `vp9`, `av1` | `avc` | Video codec. Available codecs depend on output format. |
| `bitrate` | bps | 2000000 | Target bitrate in bits per second. |
| `bitrateMode` | `variable`, `constant` | `variable` | VBR adapts quality per frame. CBR maintains fixed rate. |
| `hardwareAcceleration` | `no-preference`, `prefer`, `deny` | `no-preference` | GPU encoding when available. |
| `keyFrameInterval` | seconds | 5 | Seconds between keyframes. Lower = better seeking, larger file. |
| `contentHint` | `""`, `"detail"`, `"motion"`, `"text"` | `""` | Hints to the encoder. `"text"` for screen recordings, `"motion"` for action. |
| `fastStart` | bool | true | Move MP4 metadata to file start for progressive playback. |

### Codec Availability by Format

| Format | H.264 | H.265 | VP8 | VP9 | AV1 |
|---|---|---|---|---|---|
| MP4 | Yes | Yes | No | No | Yes |
| WebM | No | No | Yes | Yes | Yes |
| MKV | Yes | Yes | Yes | Yes | Yes |

## GIF

| Parameter | Range | Default | Description |
|---|---|---|---|
| `quality` | 0–100 | 80 | Color quantization quality. Lower = fewer colors, smaller file. |
| `loopCount` | 0+ | 0 | Number of loops. 0 = infinite. |

## APNG

| Parameter | Range | Default | Description |
|---|---|---|---|
| `quality` | 0–100 | 80 | Quantization quality for color reduction. |

## Timeline Effects

These apply to all animated output formats.

| Effect | Parameters | Description |
|---|---|---|
| **Trim** | `start`, `end` (seconds) | Set playback range |
| **Cut** | Multiple `{start, end}` regions | Remove sections from timeline |
| **Fade in** | Duration (seconds) | Opacity ramp from 0→1 at start |
| **Fade out** | Duration (seconds) | Opacity ramp from 1→0 at end |
| **Mid-fade** | `center`, `width` (seconds) | Dip opacity at a point in the timeline |
| **Speed** | `{start, end, speed}` regions | Variable speed 0.25×–4× over time ranges |
| **Zoom** | `{start, end, from, to, easeIn, easeOut}` | Animated pan + scale between keyframes |
| **Blur** | `{start, end, rect, strength}` | Blur a rectangular region during a time range |

## Resize Methods

| Method | Algorithm | Best For |
|---|---|---|
| `lanczos3` | Lanczos windowed sinc (3 lobes) | General purpose, sharp results |
| `catrom` | Catmull-Rom bicubic | Moderate sharpness, fewer artifacts |
| `mitchell` | Mitchell-Netravali bicubic | Balanced sharpness and smoothness |
| `triangle` | Bilinear interpolation | Fast, smooth, slightly soft |
