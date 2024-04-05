# Spiel It

This is a Spiel demo application.

## Installation

TODO: Offer Flatpaks

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