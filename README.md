# korvo-voice

A voice assistant for the ESP32-S31-Korvo-1 with the 4.3" LCD sub-board, written in Rust with
[esp-hal](https://github.com/esp-rs/esp-hal) and Embassy.

Tap the button on the screen and speak, then tap it again. [Deepgram](https://deepgram.com)
transcribes the recording, [Claude](https://www.anthropic.com/api) answers, and the question and
the answer are shown on the screen.

Migrated from the example in [esp-rs/esp-hal#6610](https://github.com/esp-rs/esp-hal/pull/6610).
Until that PR is merged, the esp-hal crates are pinned to its branch, because it also fixes stale
pixels at the start of DPI frames.

## Hardware

- ESP32-S31-Korvo-1 with the 4.3" 800x480 RGB LCD sub-board connected
- USB-UART port connected to the computer, board switched on

## Running

Requires a nightly Rust toolchain (installed from `rust-toolchain.toml`) and
[espflash](https://github.com/esp-rs/espflash).

```sh
SSID=... PASSWORD=... DEEPGRAM_API_KEY=... ANTHROPIC_API_KEY=... cargo run --release
```

The API keys are stored in the firmware in plain text, and anyone with access to the board can
read them. Use keys with a spending limit.

## License

Licensed under either of [Apache License, Version 2.0](LICENSE-APACHE) or [MIT license](LICENSE-MIT)
at your option.
