# Spiel It

This is a Spiel demo application.

## Installation

[Install this Flatpak](http://project-spiel.org/spiel-it/spiel-it.flatpakref)

## Build instructions

```sh
meson setup build
meson compile -C build
```

To run the app without installing:
```sh
meson devenv -C build
python ../spiel_it/main.py
```