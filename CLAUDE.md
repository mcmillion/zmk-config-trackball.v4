# Thumbsup! Trackball v4 ZMK Config

Forked from [ak66666/zmk-config-trackball.v4](https://github.com/ak66666/zmk-config-trackball.v4). ZMK firmware running on nice!nano v2 with PMW3610 sensor.

## Build & Flash

- Push to `main` triggers GitHub Actions build (workflow pinned to ZMK v0.2.1)
- Download `.uf2` artifact from Actions
- Double-tap reset on nice!nano, copy `.uf2` to `NICENANO` USB drive
- If ZMK Studio was used previously, "Restore Stock Settings" first or Studio overrides the flashed keymap

## Physical Layout

Orientation: thumb-right, ball at south. Binding order in keymap is: BotR, BotL, MidL, MidR, TopR, InnerL, InnerR, TopL.

```
┌──────────┬──────────┐┌──────────┬──────────┐
│ Top Left │Inner Left││InnerRight│Top Right │
├──────────┴──────────┘└──────────┴──────────┤
│ Mid Left │                      │Mid Right │
├──────────┘                      └──────────┤
│ Bot Left │                      │Bot Right │
└──────────┘                      └──────────┘
                 (ball)
```

## Current Keymap (Layer 0)

```
┌──────────┬──────────┐┌──────────┬──────────┐
│ Top Left │Inner Left││InnerRight│Top Right │
│tap: Esc  │ L Click  ││tap: MClk │ R Click  │
│hold:UTIL │          ││hold:Scroll│         │
└──────────┴──────────┘└──────────┴──────────┘
┌──────────┐                      ┌──────────┐
│ Mid Left │                      │Mid Right │
│Mouse Back│                      │Mouse Fwd │
└──────────┘                      └──────────┘
┌──────────┐                      ┌──────────┐
│ Bot Left │                      │Bot Right │
│tap: Enter│                      │Alt+Space │
│hold:ARROWS│                     │(whisper) │
└──────────┘                      └──────────┘
                (ball)
```

## Layers

| # | Name | Activation |
|---|------|-----------|
| 0 | FRONT_RIGHT | Default (sliders: front+right) |
| 1 | FRONT_LEFT | Handedness slider |
| 2 | BACK_RIGHT | Orientation slider |
| 3 | BACK_LEFT | Both sliders (conditional) |
| 4 | FRONT_SCROLL | Hold Inner Right (layer 0) |
| 5 | BACKWARD_SCROLL | Hold scroll key (layers 2/3) |
| 6 | UTIL | Hold Top Left |
| 7 | ARROWS | Hold Bot Left |

### UTIL layer (hold Top Left)

- +Inner Left = Mission Control (Ctrl+Up)
- +Inner Right = Show Desktop (F11)
- +Top Right = App Switcher (Cmd+Tab)

### ARROWS layer (hold Bot Left)

- +Top Left = Left
- +Inner Left = Down
- +Inner Right = Up
- +Top Right = Right
- +Bot Right = (unassigned)

## Scroll Speed

Controlled by `&zip_xy_scaler 1 N` in `a_ball.overlay` (higher N = slower). Currently set to 40.

## Custom Behaviors

`lt_mkp` — hold-tap that combines `&mo` (hold) with `&mkp` (tap), used for Inner Right (tap middle click, hold scroll layer).
