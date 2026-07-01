# Bifrost

**Bifrost** is a high-performance, Metal-accelerated macOS video wallpaper engine designed to bring your desktop to life without compromising system resources. 

Built from the ground up utilizing Apple's modern graphics APIs and SwiftUI, Bifrost plays stunning, high-framerate video wallpapers while seamlessly pausing in the background when your system needs to focus.

<p align="center">
  <img src="[https://i.imgur.com/your-app-screenshot.png](https://i.imgur.com/Bi5INQk.png](https://i.imgur.com/Bi5INQk.png)" alt="Bifrost Screenshot" width="700">
</p>

## ✨ Features

* **Metal-Accelerated Rendering:** Uses raw Metal shaders and CoreVideo pipelines to decode and display video with near-zero CPU overhead.
* **Smart Power Management:** Automatically pauses video playback when your Mac runs on battery power, locks the screen, or goes to sleep.
* **ProMotion (120Hz) Support:** Fully supports high-refresh-rate ProMotion displays with dynamically throttled background execution. 
* **Multi-Monitor Aware:** Individually set and save different wallpapers across all your connected displays. Seamlessly manages external display hot-plugging.
* **Zero-Distraction Accessory Mode:** Run Bifrost entirely from your Menu Bar. Check the "Hide from Dock" option in settings to keep your dock pristine.
* **Mission Control Integration:** Intelligently pauses playback when windows completely occlude your wallpaper, with a built-in debounce timer to prevent jittering during macOS Desktop switching and Mission Control animations.

## 🚀 Getting Started

### Prerequisites
* macOS 13.0 (Ventura) or later
* Xcode 14+ for compiling from source
* Apple Silicon (M1/M2/M3) highly recommended, though Intel Macs are supported.

### Installation (Build from Source)
1. Clone the repository:
   ```bash
   git clone https://github.com/ReynoldsTrimax/Bifrost.git
   cd Bifrost
   ```
2. Build the Swift Package using the terminal:
   ```bash
   swift build -c release
   ```
3. Alternatively, open `Package.swift` in Xcode, select the `BifrostApp` target, and hit `Cmd + R` to build and run.

## ⚙️ How it Works under the Hood
Bifrost bypasses standard high-level UI frameworks to draw directly to a specialized `NSWindow` sitting exactly at `NSWindow.Level.desktopIcon`. By utilizing an `AVPlayerItemVideoOutput` directly piped into an `MTKView` via a dedicated background rendering thread (`CVDisplayLink`), it completely avoids stalling the Main UI Thread, delivering flawlessly smooth animations across multiple displays.

## 🤝 Contributing
Contributions are always welcome! Feel free to open issues or submit Pull Requests for new features, optimizations, or bug fixes.
