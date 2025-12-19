# imgui (ESP-IDF Component)

Auto-synced mirror of [ocornut/imgui](https://github.com/ocornut/imgui) core files as an ESP-IDF component.

- Upstream tag: v1.92.5
- This repo contains core sources plus `misc/` helpers (no platform backends/examples from upstream other than the demo file if enabled).
- License is MIT (see LICENSE.txt from upstream).

## Usage

In your project's :

Usage

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>
  cmake [options] -S <path-to-source> -B <path-to-build>

Specify a source directory to (re-)generate a build system for it in the
current working directory.  Specify an existing build directory to
re-generate its build system.

Run 'cmake --help' for more information.

In code:



The `misc/` directory is included for convenience (e.g. fonts, debug tools). If you don't need it in your app artifact you can exclude it via your build packaging rules.

### Demo
By default this mirror includes `imgui_demo.cpp`. When manually dispatching the sync workflow you can set  to exclude it.

## Notes
- Platform backends or software renderer should be provided as a separate component/library.
