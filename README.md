# Spotifyd-win

A hacked-together version of spotifyd that can work on Windows.

Setup:

-   `git clone` this repository somewhere
-   Create `spotifyd.conf` in the cloned repository with these contents:
    ```toml
    [global]
    backend = "rodio"
    mixer = "PCM"
    volume-controller = "softvol" # or alsa_linear, or softvol
    #onevent = command_run_on_playback_event
    device_name = "spotifyd"
    bitrate = 320
    cache_path = "SOMEWHERE/cache_directory"
    volume-normalisation = false
    normalisation-pregain = -10
    device_type = "s_t_b"
    initial_volume = "100"
    ```
    Adjust `username`, `password`, and `cache_path`. `cache_path` should probably be in the spotifyd directory.
-   Run `cargo build --release`
-   Run `target/release/spotifyd.exe` and listen to music!

To run at startup:

1. Go to `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup` and create a shortcut (New -> Shortcut)
2. Set the path to wherever spotifyd was built (`somewhere/target/release/spotifyd.exe`)
3. It should run at startup

TODO: When run at startup there are no logs

# Spotifyd <!-- omit in toc -->

<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->

[![All Contributors](https://img.shields.io/badge/all_contributors-83-orange.svg?style=flat-square)](#contributors-)

<!-- ALL-CONTRIBUTORS-BADGE:END -->

[![Cargo Downloads](https://img.shields.io/crates/d/spotifyd)](https://crates.io/crates/spotifyd)
[![Github Actions - CD][cd-badge]][github-actions]
[![Github Actions - CI][ci-badge]][github-actions]

> An open source Spotify client running as a UNIX daemon.

Spotifyd streams music just like the official client, but is more lightweight and supports more platforms. Spotifyd also supports the Spotify Connect protocol, which makes it show up as a device that can be controlled from the official clients.

> **Note:** Spotifyd requires a Spotify Premium account.

**To read about how to install and configure Spotifyd, take a look at our [wiki][wiki]!**

-   [Common issues](#common-issues)
-   [Contributing](#contributing)
-   [Credits](#credits)

## Common issues

-   Spotifyd will not work without Spotify Premium
-   The device name cannot contain spaces

## Contributing

We always appreciate help during the development of `spotifyd`! If you are new to programming, open source or Rust in general, take a look at issues tagged with [`good first issue`][good-first-issues]. These normally are easy to resolve and don't take much time to implement.

## Credits

This project would not have been possible without the amazing reverse engineering work done in [librespot](https://github.com/librespot-org/librespot), mostly by [plietar](https://github.com/plietar).

<!-- This section contains all links used within the document. This prevents cluttering and makes reading the raw markdown a lot easier -->

[github-actions]: https://github.com/Spotifyd/spotifyd/actions
[good-first-issues]: https://github.com/Spotifyd/spotifyd/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22
[cd-badge]: https://github.com/Spotifyd/spotifyd/workflows/Continuous%20Deployment/badge.svg
[ci-badge]: https://github.com/Spotifyd/spotifyd/workflows/Continuous%20Integration/badge.svg
[wiki]: https://spotifyd.github.io/spotifyd/
