# Instructions for coding agents

Read `README.md` first. It holds the hardware, how the touch sensor behaves, the wiring and what is
proven. This file is the rules for working on it.

## The hardware can be damaged

- **Never tell anyone to plug USB into the XIAO while it is wired to the lamp.** The USB 5 V back-feeds
  the lamp's battery. In the lamp, the firmware is updated over Wi-Fi only.
- The XIAO runs from the lamp's own cell. **Never leave `Stay awake` on** or weaken the low-battery sleep
  (`sleep_below`, `resume_above`): without it the board drains the cell flat, which ruins it.

## Tapping the lamp

- A tap from Home Assistant is a physical action on someone's lamp. Test it with a person watching.
- After anything is touched at the rod, the touch chip may ignore taps for about a minute. Wait before
  concluding a change failed.

## Secrets

- `secrets.yaml` is gitignored. Only `secrets.example.yaml` goes in git. Never commit a `.bin`.
- Example files and the README name no real network, address or person.

## Building

- Use `uvx esphome@2026.9.1`, the version this config is proven on. Bump deliberately and say so.
- `esphome upload` re-flashes the previous binary without compiling. Use `esphome run`, or `compile`
  then `upload`.
- `images/wiring.svg` is exported from a drawing; edit the SVG directly, and keep the README's wiring
  table in step with it.

## Keeping the docs honest

- Anything marked **not yet proven** in the README stays marked until a person has seen it work on a
  lamp. Then update the README in the same change.
- The README is read by people who have not seen this lamp's insides. Explain a term the first time it
  appears.
- A finding goes in the README once, in the section it belongs to. Do not repeat it.
