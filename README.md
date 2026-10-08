# Happy Birthday Baby!

A small top-down game written in C with [SDL3](https://www.libsdl.org/). The project is currently in early development: it initializes SDL, creates a resizable window, and sets up a renderer that will support the game world and its characters.

## Project status

The basic SDL3 application is being set up. Gameplay, artwork, audio, and controls are still to be implemented.

Planned features include:

- Top-down player movement
- A small explorable game world
- Character and environment interactions
- Simple animations, sound effects, and music
- A birthday-themed objective or story

## Requirements

To build the project, you need:

- A C compiler such as GCC
- GNU Make
- SDL3 development headers and library
- A graphical desktop session with X11 or Wayland access

On Debian- or Ubuntu-based systems, SDL3 may be available through the package manager:

```bash
sudo apt install build-essential libsdl3-dev
```

Package names can vary between distributions. If SDL3 is unavailable from your package manager, follow the [official SDL installation documentation](https://wiki.libsdl.org/SDL3/Installation).

## Building and running

Clone the repository and enter its directory, then create the output directory if it does not already exist:

```bash
mkdir -p out
```

Build the executable:

```bash
make build
```

Run it:

```bash
make run
```

You can also build and run it in one command:

```bash
make
```

The executable is written to `out/sdl_game.exe`. Despite the `.exe` suffix, the current Makefile produces a native executable for the host system running GCC.

## Project structure

```text
.
├── Makefile       # Build and run commands
├── src/
│   └── main.c     # SDL application entry points and setup
└── out/           # Compiled output
```

## Troubleshooting

### `No available video device`

SDL needs access to a graphical display. This error commonly occurs when the game is launched in a headless container, an SSH session without display forwarding, or an environment without X11 or Wayland access. Run the executable from a terminal inside a graphical desktop session.

### SDL3 headers or library not found

Confirm that the SDL3 development package is installed and that the compiler can locate both the SDL3 headers and library. The source includes SDL using:

```c
#include <SDL3/SDL.h>
```

## Development notes

The game uses SDL3's callback-based application model through `SDL_MAIN_USE_CALLBACKS`. Application setup belongs in `SDL_AppInit`, per-frame updates and rendering in `SDL_AppIterate`, event handling in `SDL_AppEvent`, and cleanup in `SDL_AppQuit`.

## License

No license has been selected yet.
