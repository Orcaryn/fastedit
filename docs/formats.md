# Supported Formats

Complete format reference for [FastEdit](https://fastedit.net). All encoding and decoding runs client-side via WebAssembly.

## Input Formats

| Format | Extension | Type | Notes |
|---|---|---|---|
| JPEG | `.jpg`, `.jpeg` | Still | Universal photo format |
| PNG | `.png` | Still | Lossless with alpha |
| WebP | `.webp` | Still or Animated | Auto-detected based on frame count |
| GIF | `.gif` | Still or Animated | Single-frame GIFs treated as still |
| AVIF | `.avif` | Still | AV1-based, excellent compression |
| APNG | `.apng` | Still | Animated PNG (treated as still input) |
| HEIC / HEIF | `.heic`, `.heif` | Still | iPhone default photo format |
| SVG | `.svg` | Still | Rasterized on import |
| JPEG XL | `.jxl` | Still | Next-gen format with progressive decode |
| BMP | `.bmp` | Still | Uncompressed bitmap |
| TIFF | `.tiff` | Still | Print/archive format |
| MP4 | `.mp4` | Animated | H.264 / H.265 video |
| MOV | `.mov` | Animated | QuickTime container |
| WebM | `.webm` | Animated | VP8 / VP9 / AV1 video |
| MKV | `.mkv` | Animated | Matroska container |

## Still Image Output Formats

| Format | Extension | Lossy | Lossless | Alpha | Key Options |
|---|---|---|---|---|---|
| WebP | `.webp` | Yes | Yes | Yes | Quality, method, near-lossless, sharp YUV |
| AVIF | `.avif` | Yes | Yes | Yes | Quality, speed, subsample |
| PNG | `.png` | No | Yes | Yes | Optimization level (oxipng) |
| JPEG | `.jpg` | Yes | No | No | Quality |
| JPEG XL | `.jxl` | Yes | Yes | Yes | Quality, effort, distance |
| BMP | `.bmp` | No | Yes | No | None |
| TIFF | `.tiff` | No | Yes | No | None |
| ICO | `.ico` | No | Yes | Yes | Multi-size (16, 32, 48, 256px) |

## Animated / Video Output Formats

| Format | Extension | Codecs | Alpha | Audio | Key Options |
|---|---|---|---|---|---|
| WebP | `.webp` | libwebp | Yes | No | Quality, method, passes, SNS, filter, keyframe interval, loop count |
| GIF | `.gif` | LZW | No (1-bit) | No | Quality, loop count |
| APNG | `.apng` | Deflate | Yes | No | Quality |
| MP4 | `.mp4` | H.264, H.265, AV1 | No | Yes | Bitrate, VBR/CBR, key frame interval, fast start |
| WebM | `.webm` | VP8, VP9, AV1 | VP8/VP9 only | Yes | Bitrate, VBR/CBR, content hint |
| MKV | `.mkv` | H.264, H.265, VP8, VP9, AV1 | No | Yes | Bitrate, VBR/CBR, key frame interval, fast start |

## Format Selection Guide

**Smallest file size for photos:** AVIF > WebP > JPEG XL > JPEG > PNG

**Smallest animated file size:** MP4 (H.265) > WebP > MP4 (H.264) > WebM (VP9) > GIF

**Best quality at low bitrate:** AVIF > JPEG XL > WebP > JPEG

**Widest browser support:** JPEG / PNG (still), MP4 H.264 / GIF (animated)

**Alpha transparency (still):** WebP, AVIF, PNG

**Alpha transparency (animated):** WebP, APNG

## Browser Compatibility

| Format | Chrome | Firefox | Safari | Edge |
|---|---|---|---|---|
| WebP (still) | 32+ | 65+ | 16+ | 18+ |
| WebP (animated) | 32+ | 65+ | 16+ | 18+ |
| AVIF | 85+ | 93+ | 16.4+ | 121+ |
| JPEG XL | No | No | 17+ | No |
| HEIC input | No | No | 11+ | No |
| APNG | 59+ | 3+ | 8+ | 79+ |
| MP4 H.264 | 4+ | 35+ | 3.1+ | 12+ |
| MP4 H.265 | Partial | No | 11+ | Partial |
| WebM VP9 | 29+ | 28+ | 14.1+ | 79+ |
| WebM AV1 | 70+ | 67+ | 17+ | 79+ |
