# ai-on_the_go!

A **pocket-sized** handheld that runs an AI model **offline**, with a thumb keyboard and voice control (talk to it, it talks back). Think PocketTerm / BlackBerry, with a local LLM inside.

Hack Club Stardance hardware project by @suvyakthacharya.

## How it works

```
[Thumb-keyboard PCB] --USB--> [Raspberry Pi 5, 8GB] --DSI--> [~4" screen]
  RP2040 + ~45 tact switches     Ollama (LLM)
  I2S mic + I2S speaker amp --GPIO--> whisper.cpp (speech->text)
                                     Piper (text->speech)
                                        ^
                                 [LiPo + 5V boost]
```

- **Keyboard:** custom thumb-keyboard PCB with ~45 small SMD tactile switches (cheap, thin, typeable). An RP2040 runs KMK firmware and shows up as a normal USB keyboard.
- **Voice:** an I2S MEMS mic (INMP441) and an I2S amp (MAX98357A) + small speaker, broken out on the same PCB and wired to the Pi's GPIO. A push-to-talk key starts listening.
- **Brain:** a Raspberry Pi 5 (8GB) running [Ollama](https://ollama.com) with a small model (Llama 3.2 3B / Qwen 2.5 3B) for usable speed.
- **Screen:** a ~4" DSI display (for example 720×720), sized to the keyboard width.
- **Software:** a fullscreen chat app that boots straight into the AI.
- **Case:** a 3D-printed slab (screen on top, keyboard below), target about 95 × 160 × 30 mm so it fits a pocket.

## Repo layout

| Folder | Contents |
|---|---|
| `pcb/` | KiCad project, Gerbers |
| `cad/` | Case models (STEP + STL) |
| `firmware/` | KMK keyboard firmware |
| `software/` | Chat app running on the Pi |
| `docs/` | Plan, BOM, photos, wiring |

See [docs/PLAN.md](docs/PLAN.md) and [docs/BOM.md](docs/BOM.md).
