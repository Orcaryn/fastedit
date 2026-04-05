<p align="center">
  <a href="https://fastedit.net">
    <img src="icon.svg" alt="FastEdit — free browser-based image and video editor" width="80" height="80" />
  </a>
</p>

<h1 align="center">FastEdit</h1>

<p align="center">
  Free browser-based editor for WebP, GIF, MP4, AVIF, and 15+ image &amp; video formats.<br/>
  Convert, trim, crop, blur, batch-process — runs locally via WebAssembly, no uploads ever.
</p>

<p align="center">
  <a href="https://fastedit.net"><strong>Open FastEdit</strong></a>&nbsp;&nbsp;·&nbsp;&nbsp;
  <a href="https://fastedit.net/guides">Guides</a>&nbsp;&nbsp;·&nbsp;&nbsp;
  <a href="https://fastedit.net/blog">Blog</a>&nbsp;&nbsp;·&nbsp;&nbsp;
  <a href="https://fastedit.net/formats">Formats</a>
</p>

<p align="center">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-green.svg" />
  <img alt="Platform" src="https://img.shields.io/badge/runs%20in-your%20browser-blue" />
  <img alt="Uploads" src="https://img.shields.io/badge/server%20uploads-zero-brightgreen" />
  <img alt="Formats" src="https://img.shields.io/badge/formats-15%2B%20input%20·%2014%20output-orange" />
</p>

---

## What is FastEdit?

FastEdit is a free, browser-based image and video editor powered by WebAssembly. It converts, compresses, and edits WebP, GIF, MP4, AVIF, APNG, HEIC, and 15+ other formats entirely on your device. No files are uploaded, no account is required, and there are no watermarks or file size limits.

**[Open FastEdit →](https://fastedit.net)**

## Why FastEdit?

| | FastEdit | Cloud-based editors (Ezgif, CloudConvert, etc.) |
|---|---|---|
| **File uploads** | None — everything runs locally | Files uploaded to remote servers |
| **File size limit** | None (limited only by your device RAM) | Typically 50–100 MB |
| **Cost** | Free, no premium tiers | Free tiers with paid upgrades |
| **Processing speed** | Near-native via WebAssembly | Depends on server queue |
| **Privacy** | Files never leave your device | Files processed on third-party servers |
| **Watermarks** | Never | Often on free tiers |
| **Batch processing** | Unlimited parallel processing | Usually limited or paid |
| **Platform presets** | 49 built-in presets for 23 platforms | Manual configuration |
| **Advanced encoding** | Full codec control (libwebp, H.264/265, VP8/9, AV1) | Limited options |

## Getting Started

1. Open **[fastedit.net](https://fastedit.net)** in Chrome, Edge, or Firefox
2. Drop an image, GIF, or video file
3. Edit, convert, or compress
4. Download the result — nothing was uploaded

## Image Editor — Convert and Compress Still Images

- **8 output formats** — WebP, AVIF, PNG, JPEG, JPEG XL, BMP, TIFF, ICO
- **15+ input formats** — JPEG, PNG, WebP, AVIF, HEIC/HEIF, SVG, JPEG XL, APNG, BMP, TIFF, and more
- Crop with aspect ratio lock, rotate, resize with four interpolation methods (Lanczos3, Catrom, Mitchell, Triangle)
- AI-powered background removal running locally via HuggingFace Transformers — no cloud API
- Side-by-side compare slider to check quality against the original
- Format analysis grid showing every export option's file size, compression ratio, and encoding time

## Animation & Video Editor — Edit GIF, WebP, MP4, WebM

- **6 output formats** — animated WebP, GIF, MP4, WebM, APNG, MKV
- **5 video codecs** — H.264, H.265, VP8, VP9, AV1
- Timeline editing with frame-accurate control:
  - **Trim** — set start and end points
  - **Cut** — remove sections, add multiple cut regions, drag to reposition
  - **Fade** — fade in/out and mid-fades (dip opacity at any point)
  - **Speed** — variable speed regions from 0.25× to 4×
  - **Zoom** — animated pan and scale with easing curves
  - **Blur/Redact** — draw blur regions scoped to specific time ranges
- Playback modes: Normal, Reverse, Ping-pong
- FPS control, automatic frame deduplication, keep-audio toggle
- Bitrate control (VBR/CBR), hardware acceleration, key frame interval, content hints

## Batch Processing — Convert Multiple Files at Once

- Drop a folder or select multiple files to process in a single operation
- Mix stills and animations in the same batch
- Apply shared settings or override per file
- Parallel processing with real-time progress tracking for each item

## 49 Platform Presets — One-Click Optimization

One-click configurations that auto-set format, dimensions, and file size limits for specific platforms:

**Chat & Messaging** — Discord, Telegram, WhatsApp, Signal, Slack, iMessage
**Social Media** — Instagram, X/Twitter, TikTok, LinkedIn, Reddit, Pinterest, Bluesky, Mastodon, Facebook
**Streaming** — Twitch, YouTube, Spotify
**Developer & Web** — GitHub, Google Business, Open Graph, Favicon, PWA
**And more** — 49 presets across 23 platforms

Each preset applies the platform's exact requirements — format restrictions, maximum dimensions, file size caps — so the output works on the first try.

## Advanced Encoding Control

FastEdit exposes the full libwebp `WebPConfig` for animated WebP: quality, method, passes, SNS strength, filter strength/sharpness/type, alpha quality/compression/filtering, near-lossless mode, sharp YUV, keyframe interval, and loop count.

Video formats (MP4, WebM, MKV) get codec selection, bitrate control (VBR/CBR), hardware acceleration, key frame interval, and content hints (screen recording vs. animation).

Still image formats expose format-specific controls: JPEG quality, PNG optimization level, AVIF speed/quality, JPEG XL effort/distance, and more.

## How It Works

FastEdit compiles native image and video codecs to [WebAssembly](https://webassembly.org/) so they run at near-native speed directly in your browser. There is no server — your CPU does all the work. No plugins, no installs, no sign-up.

You can verify this yourself: open your browser's DevTools Network tab while editing. You'll see zero outbound file transfers.

## Tech Stack

| Layer | Technology |
|---|---|
| UI | React 19, TypeScript, Radix UI |
| Build | Vite |
| Image encoding | [wasm-webp](https://github.com/HaMMeRSI/webp-wasm) (forked libwebp), jsquash (AVIF, JPEG, JXL, PNG, WebP) |
| Video encoding | MediaRecorder API, WebCodecs |
| Background removal | HuggingFace Transformers (ONNX runtime, in-browser) |
| State management | Zustand |

## Browser Support

| Browser | Still images | Animated / Video |
|---|---|---|
| Chrome / Edge | Full support | Full support |
| Firefox | Full support | Partial — no animated WebP/GIF input decoding |
| Safari | Full support | Partial — limited codec support |

Requires WebAssembly and SharedArrayBuffer. Desktop browsers recommended for large files and complex animations.

## Common Use Cases

- **Convert GIF to MP4 or WebP** — produce smaller, sharper animations with full codec control. [Guide →](https://fastedit.net/convert/gif-to-mp4)
- **Make Discord emojis and stickers** — auto-resize to 128px, compress under 256 KB. [Guide →](https://fastedit.net/guides/make-discord-emoji)
- **Create Telegram sticker packs** — export as 512×512 WebP under 64 KB. [Guide →](https://fastedit.net/guides/make-telegram-sticker)
- **Optimize images for the web** — convert to AVIF, WebP, or JPEG XL with precise quality control for faster page loads. [Guide →](https://fastedit.net/guides/compress-image-for-web)
- **Batch resize and convert** — process an entire folder of screenshots or product photos in one pass. [Guide →](https://fastedit.net/guides/batch-convert-images)
- **Blur and redact sensitive info** — draw blur regions on screen recordings, scoped to exact time ranges. [Guide →](https://fastedit.net/guides/blur-sensitive-info)
- **Trim and crop video clips** — cut intros, remove borders, adjust speed — all in the browser without installing software. [Guide →](https://fastedit.net/guides/trim-video-online)
- **Convert HEIC to JPEG or PNG** — open iPhone photos on any device by converting HEIC/HEIF locally. [Guide →](https://fastedit.net/convert/heic-to-jpg)

## FAQ

**Is FastEdit really free?**
Yes. No premium tiers, no watermarks, no usage limits, no account required. All processing runs on your device, so there are no server costs to pass on.

**Are my files uploaded anywhere?**
No. All processing happens locally in your browser via WebAssembly. Your files never leave your device — not temporarily, not anonymously, not ever. You can verify by checking the Network tab in DevTools.

**What formats does FastEdit support?**
15+ input formats: JPEG, PNG, WebP, GIF, AVIF, APNG, HEIC/HEIF, SVG, JPEG XL, MP4, MOV, WebM, MKV, BMP, TIFF. Still images export to 8 formats (WebP, AVIF, PNG, JPEG, JXL, BMP, TIFF, ICO). Animations export to 6 formats (WebP, GIF, MP4, WebM, APNG, MKV).

**Is there a file size limit?**
No. The only constraint is your device's available RAM. FastEdit routinely handles files that cloud-based tools reject.

**Does it work offline?**
Once the page loads and downloads the WebAssembly modules, all processing runs locally. You can disconnect from the internet and keep editing.

**What is WebAssembly?**
WebAssembly (Wasm) lets browsers run compiled code at near-native speed. FastEdit uses it to run image and video codecs directly on your CPU — the same technology behind Figma and Google Earth.

**How does FastEdit compare to Ezgif?**
FastEdit never uploads your files, has no file size limits, no processing queues, and no watermarks. It also includes batch processing, 49 platform presets, timeline editing with blur/redact, and full codec control — all running locally.

**Can I edit videos?**
Yes. Trim, crop, blur regions, adjust speed (0.25×–4×), reverse playback, and convert between MP4, WebM, and MKV with codec control (H.264, H.265, VP8, VP9, AV1).

## Documentation

- [**Social media image sizes**](docs/social-media-image-sizes.md) — dimensions, file limits, and format requirements for 23 platforms
- [**Image format comparison**](docs/image-format-comparison.md) — WebP vs AVIF vs JPEG XL vs PNG vs JPEG — when to use which
- [**Format reference**](docs/formats.md) — all input/output formats, codec support, browser compatibility
- [**Encoding parameters**](docs/encoding.md) — full reference for WebP, video, GIF, and APNG encoding options
- [**Platform presets (JSON)**](presets/) — 49 presets as machine-readable data

## Contributing

Found a bug or have a feature idea? [Open an issue](https://github.com/Orcaryn/fastedit/issues). See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Privacy

FastEdit processes everything locally. Files are never uploaded, cached, or logged by any server. No cookies for tracking, no third-party analytics on your media. Read the full [privacy policy](https://fastedit.net/privacy).

## License

[MIT](LICENSE)

## Links

- [fastedit.net](https://fastedit.net) — open the editor
- [Image converter](https://fastedit.net/tools/image-converter) — convert between 15+ image formats
- [GIF to MP4 converter](https://fastedit.net/convert/gif-to-mp4) — convert GIF animations to MP4 video
- [WebP editor](https://fastedit.net/formats/webp) — edit and optimize WebP images and animations
- [Video trimmer](https://fastedit.net/guides/trim-video-online) — trim and crop video clips in the browser
- [Batch image converter](https://fastedit.net/guides/batch-convert-images) — convert multiple files at once
- [All guides](https://fastedit.net/guides) — tutorials and how-to articles
- [Blog](https://fastedit.net/blog) — updates and technical deep-dives
- [Format reference](https://fastedit.net/formats) — detailed specs for every supported format
