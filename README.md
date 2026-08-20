# LED Curve Studio

**Live: [jeromedemers.github.io/led-curve-studio](https://jeromedemers.github.io/led-curve-studio/)** — the hosted version runs over HTTPS, so direct Arduino programming works there without the local launcher.

A dependency-free LED animation designer that runs entirely in one `index.html`.

## Use it

For design and export only, open `index.html` directly. No install, build step, web server, or network connection is required. Direct Nano R4 programming uses the included localhost launcher described below.

1. Choose **Change image** or drop a photo onto the preview.
2. Choose **Edit LED**, then drag the LED body to move it.
3. Use the corner and rotation handles to size and orient the light.
4. Pick a shape, color, glow spread, preset, and cycle speed.
5. Drag curve points to control brightness over time. Double-click the curve to add a point or a non-endpoint handle to remove it.

The playhead can be dragged to preview a moment in the cycle. Keyboard users can nudge the LED with the arrow keys and edit selected curve points with the arrow and Delete keys.

## Program an Arduino from Chrome

WebUSB and Web Serial are blocked on `file://`, so launch the secure localhost version:

1. Double-click **Start LED Curve Studio.cmd** and keep its terminal window open. Launching it again reuses the running server, so the address stays stable (normally `http://localhost:8765`).
2. In the opened Chrome/Edge tab, finish the curve and open **Arduino code**.
3. Select the board profile and LED output.
4. Close Arduino IDE's Serial Monitor, then click **Program…** and select the USB device/port.

Supported direct-programming profiles:

- **Arduino Nano R4** — WebUSB DFU; double-tap Reset if the Upgrade device is not listed.
- **Arduino Uno R3 / ATmega328P** — Web Serial STK500v1 at 115200 baud.
- **Classic Nano / ATmega328P** — new bootloader at 115200 baud or old bootloader at 57600 baud.

The browser patches the current duration, output mode, pin, and 64 gamma-corrected samples into a precompiled player firmware. AVR uploads are read back and compared byte-for-byte before success is reported. Programming overwrites the board's current sketch. No browser C++ compiler or cloud service is involved.

Mega 2560, Leonardo/Micro, Nano Every, Uno R4 WiFi, SAMD/MKR, and ESP32 boards use other bootloader protocols; code export still works, but direct browser programming needs a board-specific profile.

## Saving and sharing

- Settings save automatically in browser storage.
- Uploaded images are resized to a maximum 1600 px edge and kept locally in IndexedDB.
- **Arduino code** generates a Nano R4 copy-paste sketch from the current curve and speed. Its built-in LED is `LED_BUILTIN` on internal pin 22 (not D13), driven with non-blocking software PWM, or an external LED can use D9 hardware PWM.
- **Export GIF** lets you choose 0.25–30 seconds of playback and shows the frame/cycle count plus whether the result loops seamlessly. The built-in dependency-free encoder renders at up to 480 px and only re-encodes the changing glow region to keep files small.
- **Copy JSON** shares the small animation and placement setup without the image.
- **Download project** includes the current image.
- **Import** accepts either format and validates values before applying them.

The bundled sample photo (`clicks-phone.jpg`, also embedded in the HTML) is the Clicks keyboard phone with its side LED unlit, so every preset renders truthfully.

All processing stays in the browser. The app has no runtime dependencies and makes no network requests.
