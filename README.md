# ai-on_the_go!

A handheld cyberdeck that runs an AI model **offline**: a custom keyboard, a screen and a Raspberry Pi 5, all in a 3D-printed case.

Hack Club Stardance hardware project by @suvyakthacharya.

## How it works

```
[Custom keyboard PCB] --USB--> [Raspberry Pi 5, 8GB] --DSI/HDMI--> [Screen]
   (RP2040, KMK firmware)        (Ollama + local LLM)
                                        ^
                                 [Battery / UPS HAT]
```

- **Keyboard:** custom PCB (about a 40% layout) with an RP2040 running KMK firmware. It shows up as a normal USB keyboard.
- **Brain:** a Raspberry Pi 5 (8GB) running [Ollama](https://ollama.com) with a small model (Llama 3.2 3B / Qwen 2.5 3B) for usable speed.
- **Screen:** a 5–7" Pi display.
- **Software:** a fullscreen chat app that boots straight into the AI.
- **Case:** a 3D-printed clamshell or slab enclosure.

## Repo layout

| Folder | Contents |
|---|---|
| `pcb/` | KiCad project, Gerbers |
| `cad/` | Case models (STEP + STL) |
| `firmware/` | KMK keyboard firmware |
| `software/` | Chat app running on the Pi |
| `docs/` | Plan, BOM, photos, wiring |

See [docs/PLAN.md](docs/PLAN.md) and [docs/BOM.md](docs/BOM.md).
