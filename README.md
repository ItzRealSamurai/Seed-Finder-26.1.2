# Seed Finder

**Automatically detects structures as you explore and cracks the world seed.**

Seed Finder is a client-side Fabric mod for Minecraft Java Edition. You play normally; it spots villages, shipwrecks, temples and other structures in the chunks around you, and once it has seen enough of them it works out the full world seed, usually in a few seconds.

It works in single-player and on servers, with no cheats, no `/seed` access and nothing installed on the server.

---

## Features

- **Automatic structure detection.** Recognises structures from their blocks and works out each one's exact start chunk.
- **Fast seed cracking.** Recovers the full 64-bit world seed from about 10 structures, using all CPU cores.
- **Client-side only.** Nothing to install on the server.
- **Verification tools.** Check a known seed against your recorded structures, or add structures by hand.
- **Saves your progress.** Recorded structures and results are kept between game sessions.

### Detected structures

| Structure | Auto-detected |
|---|---|
| Villages (all biomes) | ✅ |
| Shipwrecks (all variants) | ✅ |
| Desert pyramids | ✅ |
| Jungle temples | ✅ |
| Swamp huts | ✅ |
| Igloos | ✅ |
| Pillager outposts, ocean ruins | Manual only (`/seedfinder add`) |

---

## Requirements

- Minecraft Java Edition **26.1 / 26.1.2**
- [Fabric Loader](https://fabricmc.net/use/)
- [Fabric API](https://modrinth.com/mod/fabric-api)

## Installation

1. Install Fabric Loader for your Minecraft version.
2. Download **Fabric API** and **Seed Finder**.
3. Put both `.jar` files into your `.minecraft/mods` folder.
4. Launch the game with the Fabric profile.

---

## Quick start

```
/seedfinder clear
/seedfinder auto on
```

Explore. Each structure the mod finds is announced in chat. When about **10 structures** are recorded (check with `/seedfinder list`), run:

```
/seedfinder crack
```

The mod prints the structure seed and then:

```
WORLD SEED: 1234567890123456789
```

**Tips**

- A **mix** of structure types works best. Villages and shipwrecks give the most information, so a few of each makes the crack much faster. (try to find atleast 3 shipwrecks and 3 villages along with other structures for best results)
- If `crack` reports several candidates, keep exploring and run it again.
- Run `/seedfinder clear` whenever you switch worlds or servers.

---

## Commands

| Command | Description |
|---|---|
| `/seedfinder auto on` / `off` | Scan loaded chunks for structures every 5 seconds |
| `/seedfinder detect` | Scan loaded chunks once |
| `/seedfinder list` | Show recorded structures and how much information they give |
| `/seedfinder crack` | Find the world seed from the recorded structures |
| `/seedfinder add <type> [x z]` | Add a structure by hand (at your position, or at given block coordinates) |
| `/seedfinder undo` | Remove the last recorded structure |
| `/seedfinder clear` | Remove all recorded structures |
| `/seedfinder check <seed>` | Test a known seed against the recorded structures |
| `/seedfinder full [structureSeed]` | Run only the final step (structure seed → world seed) |
| `/seedfinder templates` | Show the structure templates the detector loaded |
| `/seedfinder hashed` | Show the hashed seed the server sent |

Structure types for `add`: `village`, `desert_pyramid`, `igloo`, `jungle_temple`, `swamp_hut`, `shipwreck`, `ocean_ruin`, `pillager_outpost`.

---

## Limitations

- Some server software sends a fake hashed seed. On those servers the mod still finds the structure seed (the lower 48 bits), but not the full world seed.
- Pillager outposts and ocean ruins are not detected automatically yet.
- The structure list is shared between worlds, so remember `/seedfinder clear`.

---

*Not an official Minecraft product. Not approved by or associated with Mojang or Microsoft.*
