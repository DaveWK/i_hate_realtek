# i_hate_realtek

Open, clean-room replacements for Realtek's closed firmware and out-of-tree drivers, so Realtek hardware runs on
open code alone and their proprietary drivers can be retired and forgotten.

## Why

Many Realtek network, Wi-Fi and Bluetooth chips depend on one or both of:
- **closed firmware or microcode blobs** (`rtl_nic/`, `rtw88/`, `rtw89/`, `rtl_bt/` in linux-firmware);
- **out-of-tree vendor drivers** that lag years behind the kernel.

Nobody outside Realtek can audit or fix the blobs. This repository is where the open replacements, measurements and
documentation get built.

## Scope

- **Analysis** of what each blob is for, taken from the open drivers' own code and public commit history.
  Example: the RTL8125B microcode that `r8169` loads.
- **Open replacements** where they're feasible: clean-room firmware, driver code that works without the blob, and
  upstream patches.
- **Parity and benchmark results:** throughput, latency, link stability and error counters, with and without the
  closed pieces.
- **Image tooling:** auditing which closed firmware files a system actually ships.

First target: the RTL8125B 2.5GbE controller (`r8169`, `rtl_nic/rtl8125b-2.fw`).

## What this repository does NOT contain

- No Realtek firmware, microcode, source or headers that aren't already published under an open licence.
- Nothing obtained by disassembling, decompiling or dumping their binaries.

See [CONTRIBUTING.md](CONTRIBUTING.md). Clean room is the whole point: it keeps the result unencumbered.

## Status

Starting. Contributions are welcome, including LLM-assisted ones, under the rules in CONTRIBUTING.md.

## Licence

MIT unless a file says otherwise. Code derived from GPL-licensed kernel sources keeps their licence, noted per file.
