# Still Aura

**流韵 — Moments remain.**

Still Aura is a photo editor designed for precise adjustments, thoughtful color grading, and expressive image editing.

Built around the belief that photography extends beyond the captured moment, Still Aura aims to provide a minimal, focused digital darkroom where every adjustment serves a creative purpose.

## Philosophy

**The image is still. The feeling remains.**

Photography captures a moment, but the creative process does not end with the shutter.

Still Aura embraces post-processing as an extension of photographic expression, giving photographers the freedom to shape light, tone, and color with intention.

## Setup

Still Aura is built with **Tauri 2, React, TypeScript, Vite, and Rust**, targeting Windows and Android.

### Prerequisites

Before getting started, install the following tools:

**Common requirements**：

- [Node.js](https://nodejs.org/) (LTS)
- [Rust](https://rustup.rs/) (stable toolchain)
- npm (included with Node.js)

**Windows**：

- [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) with the **Desktop development with C++** workload
- Microsoft Edge WebView2 Runtime

**Android**：

- [Android Studio](https://developer.android.com/studio)
- Android SDK, Platform Tools, Build Tools, and Command-line Tools
- Android NDK
- JDK 17 or a compatible version required by the installed Android Gradle Plugin
- A configured Android emulator or physical device with USB debugging enabled

Configure the `JAVA_HOME`, `ANDROID_HOME`, and `NDK_HOME` environment variables for Android development.

For detailed platform requirements, see the [Tauri prerequisites](https://v2.tauri.app/start/prerequisites/).

### Project Structure

```text
still-aura/
├── src/
│   ├── app/
│   ├── components/
│   ├── features/
│   │   ├── library/
│   │   ├── editor/
│   │   ├── adjustments/
│   │   └── export/
│   ├── hooks/
│   ├── services/
│   ├── stores/
│   └── styles/
├── src-tauri/
│   ├── src/
│   │   ├── lib.rs
│   │   └── commands/
│   ├── capabilities/
│   ├── gen/android/
│   ├── Cargo.toml
│   └── tauri.conf.json
├── crates/
│   └── still-aura-core/
├── public/
├── LICENSE
├── README.md
├── package.json
└── pnpm-lock.yaml
```

### Install Dependencies

```bash
npm ci
```

### Windows Development

Start the desktop application in development mode:

```bash
npm run tauri dev
```

Build the Windows application:

```bash
npm run tauri build
```

### Android Development

Install the required Rust targets:

```bash
rustup target add aarch64-linux-android
rustup target add armv7-linux-androideabi
rustup target add i686-linux-android
rustup target add x86_64-linux-android
```

Initialize the Android project (first-time setup only):

```bash
npm run tauri android init
```

Start an Android emulator or connect a physical device, then run:

```bash
npm run tauri android dev
```

Build the Android application:

```bash
npm run tauri android build
```

Release builds require Android signing configuration before distribution.

### Available Commands

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Build the frontend |
| `npm run tauri dev` | Run the Windows desktop application |
| `npm run tauri build` | Build the Windows application |
| `npm run tauri android dev` | Run the Android application |
| `npm run tauri android build` | Build the Android application |

### Troubleshooting

If the Android build fails, verify that the Android SDK, NDK, and JDK are installed and that their environment variables point to valid directories.

If the Windows build fails, verify that the MSVC C++ build tools and WebView2 runtime are installed.

For additional help, refer to the [Tauri 2 documentation](https://v2.tauri.app/).

## Roadmap

Still Aura is under active development. Our goal is to build a precise, minimal, and expressive photo editor for Windows and Android.

This roadmap tracks the development and release of major features. Priorities and release targets may change as the project evolves.

### v0.1.0 — Foundation

*Establish the cross-platform application foundation.*

- [ ] Initialize Tauri 2, React, TypeScript, and Rust
- [ ] Establish the shared application architecture
- [ ] Set up Windows development and build workflows
- [ ] Set up Android development and build workflows
- [ ] Implement responsive desktop and mobile layouts
- [ ] Introduce the initial design system and dark theme
- [ ] Configure automated builds and basic testing

### v0.2.0 — Image Library

*Import, browse, and manage photographs.*

- [ ] Import JPEG and PNG images
- [ ] Integrate native file and photo pickers
- [ ] Display image thumbnails and metadata
- [ ] Implement image browsing and selection
- [ ] Add zoom, pan, and fit-to-screen controls
- [ ] Implement basic image caching

### v0.3.0 — Basic Image Editing

*Introduce practical image editing tools and establish the essential editing experience.*

- [ ] Implement image cropping with custom aspect ratios
- [ ] Support image rotation, flipping, and straightening
- [ ] Support image resizing and resolution adjustments
- [ ] Implement text and image watermarks
- [ ] Support watermark positioning, scaling, and opacity
- [ ] Implement image borders and padding
- [ ] Support customizable border colors, widths, and proportions
- [ ] Implement image stitching and collage layouts (horizontal, vertical, and grid)
- [ ] Support customizable spacing, background colors, and image arrangements
- [ ] Implement real-time editing previews
- [ ] Support JPEG and PNG export

### v0.4.0 — Essential Adjustments

*Introduce core photographic adjustments for precise control over light, tone, and color.*

- [ ] Exposure and brightness adjustments
- [ ] Contrast adjustments
- [ ] Highlights and shadows
- [ ] Whites and blacks
- [ ] Temperature and tint
- [ ] Saturation and vibrance
- [ ] Clarity and texture
- [ ] Real-time adjustment previews
- [ ] Before-and-after comparison
- [ ] Undo and redo

### v0.5.0 — Non-Destructive Workflow

*Preserve original images and allow every adjustment to be refined or reversed.*

- [ ] Implement a non-destructive image processing pipeline
- [ ] Save and restore editing parameters
- [ ] Introduce project or sidecar files
- [ ] Add editing history
- [ ] Support reusable presets
- [ ] Improve JPEG and PNG export
- [ ] Configure export quality and resolution

### v0.6.0 — RAW Development

*Build the foundation of a professional digital darkroom.*

- [ ] Integrate a RAW decoding pipeline
- [ ] Support selected camera RAW formats
- [ ] Implement demosaicing and white balance
- [ ] Introduce camera color profiles
- [ ] Improve highlight recovery
- [ ] Add tone curves
- [ ] Support histogram visualization
- [ ] Improve high-bit-depth image processing

### v0.7.0 — Advanced Color

*Provide more deliberate control over color and tone.*

- [ ] RGB and individual channel curves
- [ ] HSL color adjustments
- [ ] Color grading controls
- [ ] Color calibration tools
- [ ] Sharpening and noise reduction
- [ ] Lens correction support
- [ ] Improve color management and export consistency

### v0.8.0 — Local Adjustments

*Enable selective editing with greater precision.*

- [ ] Linear and radial gradient masks
- [ ] Brush-based masking
- [ ] Luminance and color range masks
- [ ] Independent adjustments for masked regions
- [ ] Mask overlay and visualization
- [ ] Optimize interactive masking performance

### v0.9.0 — Performance & Workflow

*Refine performance and usability across platforms.*

- [ ] GPU-accelerated image processing where supported
- [ ] Optimize large-image rendering and caching
- [ ] Improve Android memory management
- [ ] Add batch export
- [ ] Introduce keyboard shortcuts on desktop
- [ ] Improve touch and gesture controls on Android
- [ ] Expand automated tests and compatibility coverage

### v0.10.0 — Beta

*Prepare Still Aura for its first stable public release.*

- [ ] Complete major feature integration
- [ ] Improve stability and error handling
- [ ] Conduct Windows and Android compatibility testing
- [ ] Review accessibility and localization
- [ ] Finalize application icons and branding
- [ ] Publish beta builds and release notes
- [ ] Resolve release-blocking issues

### v1.0.0 — Stable Release

*Deliver the first stable release of Still Aura.*

- [ ] Release stable Windows builds
- [ ] Release stable Android builds
- [ ] Publish complete user documentation
- [ ] Publish supported RAW format and camera compatibility information
- [ ] Finalize the noncommercial licensing documentation
- [ ] Establish a maintenance and security update process

### Release History

| Version | Status | Release Date |
| --- | --- | --- |
| v0.1.0 | Planned | TBD |
| v0.2.0 | Planned | TBD |
| v0.3.0 | Planned | TBD |
| v0.4.0 | Planned | TBD |
| v0.5.0 | Planned | TBD |
| v0.6.0 | Planned | TBD |
| v0.7.0 | Planned | TBD |
| v0.8.0 | Planned | TBD |
| v0.9.0 | Planned | TBD |
| v0.10.0 | Planned | TBD |
| v1.0.0 | Planned | TBD |

### About Roadmap

Feature requests, bug reports, and technical discussions are welcome through GitHub Issues.

Roadmap items are planning targets, not guaranteed release commitments. A feature is considered complete only after it has been implemented, tested, and included in a published release.

## License

Still Aura is licensed under the [**PolyForm Noncommercial License 1.0.0**](./PolyForm%20NonCommercial%201.0.0.txt).

This project is source-available, not OSI-approved open-source software.

Permitted noncommercial activities include personal use, studying the source code, modification, and redistribution in accordance with the license.

**Commercial use is not authorized under the public license.**

Examples of commercial uses requiring separate authorization include:

- Editing photographs for paying clients.
- Using Still Aura in a commercial photography studio.
- Using Still Aura as part of a paid photography or image-editing service.
- Integrating Still Aura into a commercial software product.
- Commercially distributing or selling Still Aura or modified versions.

Certain organizations have additional permissions under the license. The full license text governs all permitted uses.

See [LICENSE](LICENSE) for the complete terms.

---

**Still Aura · 流韵**.

*Moments remain.*
