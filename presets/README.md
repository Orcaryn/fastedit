# Platform Image & Video Presets

Machine-readable specifications for image and video uploads across 23 platforms. Used by [FastEdit](https://fastedit.net) to auto-configure exports with one click.

## Data

[`presets.json`](presets.json) contains 49 presets with these fields:

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique preset identifier |
| `platform` | string | Platform name |
| `label` | string | Preset variant (e.g. "Emoji", "Avatar", "Banner") |
| `type` | `"still"` or `"animated"` | Whether the preset targets a static image or animation/video |
| `format` | string | Required output format (`webp`, `png`, `jpeg`, `gif`, `apng`, `webm`, `ico`) |
| `width` | number | Required width in pixels |
| `height` | number | Required height in pixels |
| `maxFileSize` | number? | Maximum file size in bytes (omitted if no limit) |
| `maxDuration` | number? | Maximum duration in seconds (animated only) |
| `aspectRatio` | string | Required aspect ratio |
| `codec` | string? | Required codec (animated only, e.g. `"vp9"`) |
| `fps` | number? | Required frame rate (animated only) |
| `sizes` | number[]? | Multi-size icon array (ICO only) |

## Platforms Covered

Discord, Telegram, WhatsApp, Slack, Signal, iMessage, Twitch, X (Twitter), YouTube, Instagram, Bluesky, Facebook, LinkedIn, GitHub, Google Business, Favicon, Mastodon, Open Graph, Pinterest, PWA, Reddit, Spotify, TikTok

## Usage

```javascript
import presets from './presets.json';

// Find all Discord presets
const discord = presets.filter(p => p.platform === 'Discord');

// Find presets that accept animated input
const animated = presets.filter(p => p.type === 'animated');

// Find presets with tight file size limits (under 256KB)
const tight = presets.filter(p => p.maxFileSize && p.maxFileSize <= 256 * 1024);

// Validate a file against a preset
function validate(file, preset) {
  if (preset.maxFileSize && file.size > preset.maxFileSize) {
    return { valid: false, reason: `File exceeds ${preset.maxFileSize} bytes` };
  }
  return { valid: true };
}
```

## Keeping Up to Date

Platform requirements change. If you notice outdated specs, [open an issue](https://github.com/Orcaryn/fastedit/issues).

## License

[MIT](../LICENSE)
